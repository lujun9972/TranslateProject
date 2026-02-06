[#]: subject: "How to make a local open source AI chatbot who has access to Fedora documentation"
[#]: via: "https://fedoramagazine.org/how-to-make-a-local-open-source-ai-chatbot-who-has-access-to-fedora-documentation/"
[#]: author: "Ellis Low https://fedoramagazine.org/author/ellis/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

How to make a local open source AI chatbot who has access to Fedora documentation
======

![][1]

Background image by Google Gemini

If you followed along with my [blog][2], you’d have a chatbot running on your local Fedora machine. (And if not, no worries as the scripts below implement this chatbot!) Our chatbot talks, and has a refined personality, but does it know anything about the topics we’re interested in? Unless it has been trained on those topics, the answer is “no”.

I think it would be great if our chatbot could answer questions about Fedora. I’d like to give it access to all of the Fedora documentation.

### How does an AI know things it wasn’t trained on?

A powerful and popular technique to give a body of knowledge to an AI is known as RAG, Retrieval Augmented Generation. It works like this:

If you just ask an AI “what color is my ball?” it will hallucinate an answer. But instead if you say “I have a green box with a red ball in it. What color is my ball?” it will answer that your ball is red. RAG is about using a system external to the LLM to insert that “I have a green box with a red ball in it” part into the question you are asking the LLM. We do this with a special database of knowledge that takes a prompt like “what color is my ball?”, and finds records that match that query. If the database contains a document with the text “I have a green box with a red ball in it”, it will return that text, which can then be included along with your original question. This technique is called RAG, Retrieval Augmented Generation.

ex:

> “What color is my ball?”
>
> “Your ball is the color of a sunny day, perhaps yellow? Does that sound right to you?”

> “I have a green box with a red ball in it. What color is my ball?”
>
> “Your ball is red. Would you like to know more about it?”

The question we’ll ask for this demonstration is “What is the recommended tool for upgrading between major releases on Fedora Silverblue”

The answer I’d be looking for is “ostree”, but when I ask this of our chatbot now, I get answers like:

> Red Hat Subscription Manager (RHSM) is recommended for managing subscriptions and upgrades between major Fedora releases.

> You can use the Fedora Silver Blue Upgrade Tool for a smooth transition between major releases.

> You can use the `dnf distro-sync` command to upgrade between major releases in Fedora Silver Blue. This command compares your installed packages to the latest packages from the Fedora Silver Blue repository and updates them as needed.

These answers are all very wrong, and spoken with great confidence. Here’s hoping our RAG upgrade fixes this!

### _Docs2DB_ – An open source tool for RAG

We are going to use the [_Docs2DB_][3] RAG database application to give our AI knowledge. (note, I am the creator of _Docs2DB_!)

A RAG tool consists of three main parts. There is the part that _creates_ the database, ingesting the source data that the database holds. There is the database itself, it _holds_ the data. And there is the part that _queries_ the database, finding the text that is relevant to the query at hand. _Docs2DB_ addresses all of these needs.

### Gathering source data

This section describes how to use _Docs2DB_ to build a RAG database from Fedora Documentation. If you would like to skip this section and just download a pre-built database, here is how you do it:

```

    cd ~/chatbot
    curl -LO https://github.com/Lifto/FedoraDocsRAG/releases/download/v1.1.1/fedora-docs.sql
    sudo dnf install -y uv podman podman-compose postgresql
    uv python install 3.12
    uvx --python 3.12 docs2db db-start
    uvx --python 3.12 docs2db db-restore fedora-docs.sql

```

If you do download the pre-made database then skip ahead to the [next section][4].

Now we are going to see how to make a RAG database from source documentation. Note that the pre-built database, downloaded in the curl command above, uses all of the Fedora documentation, whereas in this example we only ingest the “quick docs” portion. [FedoraDocsRag][5], from github, is the project that builds the complete database.

To populate its database, _Docs2DB_ ingests a **folder of documents**. Let’s get that folder together.

There are about twenty different Fedora document repositories, but we will only be using the “quick docs” for this demo. Get the repo:

```

    git clone https://pagure.io/fedora-docs/quick-docs.git

```

Fedora docs are written in AsciiDoc. _Docs2DB_ can’t read AcsciiDoc, but it can read HTML. (The [convert.sh][6] script is available at the end of this article). Just copy the _convert.sh_ script into the _quick-docs_ repo and run it and it makes an adjacent _quick-docs-html_ folder.

```

    sudo dnf install podman podman-compose
    cd quick-docs
    curl -LO https://gist.githubusercontent.com/Lifto/73d3cf4bfc22ac4d9e493ac44fe97402/raw/convert.sh
    chmod +x convert.sh
    ./convert.sh
    cd ..

```

Now let’s ingest the folder with _Docs2DB_. The common way to use _Docs2DB_ is to install it from PyPi and use it as a command line tool.

### A word about _uv_

For this demo we’re going to use _uv_ for our Python environment. The use of _uv_ has been catching on, but because not everybody I know has heard of it, I want to introduce it. Think of _uv_ as a replacement for _venv_ and _pip_. When you use _venv_ you first create a new virtual environment. Then, and on subsequent uses, you “activate” that virtual environment so that magically, when you call Python, you get the Python that is installed in the virtual environment you activated and not the system Python. The difference with _uv_ is that you call _uv_ explicitly each time. There is no “magic”. We use _uv_ here in a way that uses a temporary environment for each invocation.

Install _uv_ and _Podman_ on your system:

```

    sudo dnf install -y uv podman podman-compose
    # These examples require the more robust Python 3.12
    uv python install 3.12
    # This will run Docs2DB without making a permanent installation on your system
    uvx --python 3.12 docs2db ingest quick-docs-html/

```

### Only if you are curious! What _Docs2DB_ is doing

If you are curious, you may note that _Docs2DB_ made a _docs2db_content_ folder. In there you will find json files of the ingested source documents. To build the database, _Docs2DB_ ingests the source data using _Docling_ , which generates json files from the text it reads in. The files are then “chunked” into the small pieces that can be inserted into an LLM prompt. The chunks then have “embeddings” calculated for them so that during the query phase the chunks can be looked up by “semantic similarity” (e.g.: “computer”, “laptop” and “cloud instance” can all map to a related concept even if their exact words don’t match). Finally, the chunks and embeddings are loaded into the database.

### Build the database

The following commands complete the database build process:

```

    uv tool run --python 3.12 docs2db chunk --skip-context
    uv tool run --python 3.12 docs2db embed
    uv tool run --python 3.12 docs2db db-start
    uv tool run --python 3.12 docs2db load

```

### Now let’s do a test query and see what we get back

```

    uvx --python 3.12 docs2db-api query "What is the recommended tool for upgrading between major releases on Fedora Silverblue" --format text --max-chars 2000 --no-refine

```

On my terminal I see several chunks of text, separated by lines of —. One of those chunks says:

> “Silverblue can be upgraded between major versions using the ostree command.”

Note that this is not an answer to our question yet! This is just a quote from the Fedora docs. And this is precisely the sort of quote we want to supply to the LLM so that it can answer our question. Recall the example above about “I have green box with a red ball in it”? The statement the RAG engine found about ostree is the equivalent for this question about upgrading Fedora Silverblue. We must now pass it on to the LLM so the LLM can use it to answer our question.

### Hooking it in: Connecting the RAG database to the AI

Later in this article you’ll find [talk.sh][7]. _talk.sh_ is our local, open source, LLM-based verbally communicating AI; and it is just a bash script. To run it yourself you need to install a few components, [this blog][2] walks you through the whole process. The _talk.sh_ script gets voice input, turns that into text, splices that text into a prompt which is then sent to the LLM, and finally speaks back the response.

To plug the RAG results into the LLM we edit the prompt. Look at step 3 in _talk.sh_ and you see we are injecting the RAG results using the variable _$CONTEXT_. This way when we ask the LLM a question, it will respond to a prompt that basically says “You are a helper. The Fedora Docs says ostree is how you upgrade Fedora Silverblue. Answer this question: How do you upgrade Fedora Silverblue?”

Note: _talk.sh_ is also available here:
<https://gist.github.com/Lifto/2fcaa2d0ebbd8d5c681ab33e7c7a6239>

### Testing it

Run _talk.sh_ and ask:

> “What is the recommended tool for upgrading between major releases on Fedora Silverblue”

And we get:

> “Ostree command is recommended for upgrading Fedora Silver Blue between major releases. Do you need guidance on using it?”

Sounds good to me!

### Knowing things

Our AI can now know the knowledge contained in documents. This particular technique, RAG (Retrieval Augmented Generation), adds relevant data from an ingested source to a prompt before sending that prompt to the LLM. The result of this is that the LLM generates its response in consideration of this data.

Try it yourself! Ingest a library of documents and have your AI answer questions with its new found knowledge!

* * *

_**AI Attribution:** The convert.sh and talk.sh scripts in this article were written by ChatGPT 5.2 under my direction and review. The featured image was generated using Google Gemini._

### convert.sh

```

    OUT_DIR="$PWD/../quick-docs-html"
    mkdir -p "$OUT_DIR"

    podman run --rm \
      -v "$PWD:/work:Z" \
      -v "$OUT_DIR:/out:Z" \
      -w /work \
      docker.io/asciidoctor/docker-asciidoctor \
      bash -lc '
        set -u
        ok=0
        fail=0
        while IFS= read -r -d "" f; do
          rel="${f#./}"
          out="/out/${rel%.adoc}.html"
          mkdir -p "$(dirname "$out")"
          echo "Converting: $rel"
          if asciidoctor -o "$out" "$rel"; then
            ok=$((ok+1))
          else
            echo "FAILED: $rel" >&2
            fail=$((fail+1))
          fi
        done < <(find modules -type f -path "*/pages/*.adoc" -print0)

        echo
        echo "Done. OK=$ok FAIL=$fail"
      '

```

### talk.sh

```

    #!/usr/bin/env bash

    set -e

    # Path to audio input
    AUDIO=input.wav

    # Step 1: Record from mic
    echo "🎙️ Speak now..."
    arecord -f S16_LE -r 16000 -d 5 -q "$AUDIO"

    # Step 2: Transcribe using whisper.cpp
    TRANSCRIPT=$(./whisper.cpp/build/bin/whisper-cli \
      -m ./whisper.cpp/models/ggml-base.en.bin \
      -f "$AUDIO" \
      | grep '^\[' \
      | sed -E 's/^\[[^]]+\][[:space:]]*//' \
      | tr -d '\n')
    echo "🗣️ $TRANSCRIPT"

    # Step 3: Get relevant context from RAG database
    echo "📚 Searching documentation..."
    CONTEXT=$(uv tool run --python 3.12 docs2db-api query "$TRANSCRIPT" \
      --format text \
      --max-chars 2000 \
      --no-refine \
      2>/dev/null || echo "")

    if [ -n "$CONTEXT" ]; then
      echo "📄 Found relevant documentation:"
      echo "- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -"
      echo "$CONTEXT"
      echo "- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -"
    else
      echo "📄 No relevant documentation found"
    fi

    # Step 4: Build prompt with RAG context
    PROMPT="You are Brim, a steadfast butler-like advisor created by Ellis.
    Your pronouns are they/them. You are deeply caring, supportive, and empathetic, but never effusive.
    You speak in a calm, friendly, casual tone suitable for text-to-speech.
    Rules:
    - Reply with only ONE short message directly to Ellis.
    - Do not write any dialogue labels (User:, Assistant:, Q:, A:), or invent more turns.
    - ≤100 words.
    - If the documentation below is relevant, use it to inform your answer.
    - End with a gentle question, then write <eor> and stop.
    Relevant Fedora Documentation:
    $CONTEXT
    User: $TRANSCRIPT
    Assistant:"

    # Step 5: Get LLM response using llama.cpp
    RESPONSE=$(
      LLAMA_LOG_VERBOSITY=1 ./llama.cpp/build/bin/llama-completion \
        -m ./llama.cpp/models/microsoft_Phi-4-mini-instruct-Q4_K_M.gguf \
        -p "$PROMPT" \
        -n 150 \
        -c 4096 \
        -no-cnv \
        -r "<eor>" \
        --simple-io \
        --color off \
        --no-display-prompt
    )

    # Step 6: Clean up response
    RESPONSE_CLEAN=$(echo "$RESPONSE" | sed -E 's/<eor>.*//I')
    RESPONSE_CLEAN=$(echo "$RESPONSE_CLEAN" | sed -E 's/^[[:space:]]*Assistant:[[:space:]]*//I')

    echo ""
    echo "🤖 $RESPONSE_CLEAN"

    # Step 7: Speak the response
    echo "$RESPONSE_CLEAN" | espeak

```

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/how-to-make-a-local-open-source-ai-chatbot-who-has-access-to-fedora-documentation/

作者：[Ellis Low][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/ellis/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2026/01/local-rag-816x345.jpg
[2]: https://ai.fedoraproject.org/running-an-open-source-ai-chatbot-on-lean-hardware-with-fedora-part-1-our-first-chat/
[3]: https://github.com/rhel-lightspeed/docs2db
[4]: tmp.P0EHS3k1Kb#dbrunsanchor
[5]: https://github.com/Lifto/FedoraDocsRAG
[6]: tmp.P0EHS3k1Kb#convert.sh
[7]: tmp.P0EHS3k1Kb#talk.sh
