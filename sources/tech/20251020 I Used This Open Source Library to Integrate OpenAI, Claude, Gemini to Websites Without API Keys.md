[#]: subject: "I Used This Open Source Library to Integrate OpenAI, Claude, Gemini to Websites Without API Keys"
[#]: via: "https://itsfoss.com/puter-js-ai-without-api/"
[#]: author: "Bhuwan Mishra https://itsfoss.com/author/bhuwan/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

I Used This Open Source Library to Integrate OpenAI, Claude, Gemini to Websites Without API Keys
======

[![Warp Terminal][1]][2]

When I started experimenting with AI integrations, I wanted to create a chat assistant on my website, something that could talk like GPT-4, reason like Claude, and even joke like Grok.

But OpenAI, Anthropic, Google, and xAI all require API keys. That means I needed to set up an account for each of the platforms and upgrade to one of their paid plans before I could start coding. Why? Because most of these LLM providers require a paid plan for API access. Not to mention, I would need to cover API usage billing for each LLM platform.

What if I could tell you there's an easier approach to start integrating AI within your websites and mobile applications, even without requiring API keys at all? Sounds exciting? Let me share how I did exactly that.

### Integrate AI with Puter.js

Thanks to [Puter.js][3], an open source JavaScript library that lets you use cloud features like AI models, storage, databases, user auth, all from the client side. No servers, no API keys, no backend setup needed here. What else can you ask for as a developer?

Puter.js is built around Puter’s decentralized cloud platform, which handles all the stuff like key management, routing, usage limits, and billing. Everything’s abstracted away so cleanly that, from your side, it feels like authentication, AI, and LLM just live in your browser.

Enough talking, let’s see how you can add GPT-5 integration within your web application in less than 10 lines.

```

    <html>
    <body>
        <script src="https://js.puter.com/v2/"></script>
        <script>
            puter.ai.chat(`What is puter js?`, {
                model: 'gpt-5-nano',
            }).then(puter.print);
        </script>
    </body>
    </html>

```

Yes, that’s it. Unbelievable, right? Let's save the HTML code into an `index.html` file place this a new, empty directory. Open a terminal and switch to the directory where `index.html` file is located and serve it on localhost with the Python command:

```

    python -m http.server

```

Then open [http://localhost:8000][4] in your web browser. Click on Puter.js “Continue” button when presented.

![Integrate ChatGPT with Puter JS][5]

🚧 It would take some time before you see a response from ChatGPT. Till then, you'll see a blank page.

![ChatGPT Nano doesn't know Puter.js yet but it will, soon][6]

You can explore a lot of examples and get an idea of what Puter.js does for you on its [playground][7].

Let’s modify the code to make it more interesting this time. It would take a user query and return streaming responses from three different LLMs so that users can decide which among the three provides the best result.

```

    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>AI Model Comparison</title>
        <script src="https://cdn.twind.style"></script>
        <script src="https://js.puter.com/v2/"></script>
    </head>
    <body class="bg-gray-900 min-h-screen p-6">
        <div class="max-w-7xl mx-auto">
            <h1 class="text-3xl font-bold text-white mb-6 text-center">AI Model Comparison</h1>

            <div class="mb-6">
                <label for="queryInput" class="block text-white mb-2 font-medium">Enter your query:</label>
                <div class="flex gap-2">
                    <input
                        type="text"
                        id="queryInput"
                        class="flex-1 px-4 py-3 rounded-lg bg-gray-800 text-white border border-gray-700 focus:outline-none focus:border-blue-500"
                        placeholder="Write a detailed essay on the impact of artificial intelligence on society"
                        value="Write a detailed essay on the impact of artificial intelligence on society"
                    />
                    <button
                        id="submitBtn"
                        class="px-6 py-3 bg-blue-600 hover:bg-blue-700 text-white rounded-lg font-medium transition-colors"
                    >
                        Generate
                    </button>
                </div>
            </div>

            <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
                <div class="bg-gray-800 rounded-lg p-4">
                    <h2 class="text-xl font-semibold text-blue-400 mb-3">Claude Opus 4</h2>
                    <div id="output1" class="text-gray-300 text-sm leading-relaxed h-96 overflow-y-auto whitespace-pre-wrap"></div>
                </div>

                <div class="bg-gray-800 rounded-lg p-4">
                    <h2 class="text-xl font-semibold text-green-400 mb-3">Claude Sonnet 4</h2>
                    <div id="output2" class="text-gray-300 text-sm leading-relaxed h-96 overflow-y-auto whitespace-pre-wrap"></div>
                </div>

                <div class="bg-gray-800 rounded-lg p-4">
                    <h2 class="text-xl font-semibold text-purple-400 mb-3">Gemini 2.0 Pro</h2>
                    <div id="output3" class="text-gray-300 text-sm leading-relaxed h-96 overflow-y-auto whitespace-pre-wrap"></div>
                </div>
            </div>
        </div>

        <script>
            const queryInput = document.getElementById('queryInput');
            const submitBtn = document.getElementById('submitBtn');
            const output1 = document.getElementById('output1');
            const output2 = document.getElementById('output2');
            const output3 = document.getElementById('output3');

            async function generateResponse(query, model, outputElement) {
                outputElement.textContent = 'Loading...';

                try {
                    const response = await puter.ai.chat(query, {
                        model: model,
                        stream: true
                    });

                    outputElement.textContent = '';

                    for await (const part of response) {
                        if (part?.text) {
                            outputElement.textContent += part.text;
                            outputElement.scrollTop = outputElement.scrollHeight;
                        }
                    }
                } catch (error) {
                    outputElement.textContent = `Error: ${error.message}`;
                }
            }

            async function handleSubmit() {
                const query = queryInput.value.trim();

                if (!query) {
                    alert('Please enter a query');
                    return;
                }

                submitBtn.disabled = true;
                submitBtn.textContent = 'Generating...';
                submitBtn.classList.add('opacity-50', 'cursor-not-allowed');

                await Promise.all([
                    generateResponse(query, 'claude-opus-4', output1),
                    generateResponse(query, 'claude-sonnet-4', output2),
                    generateResponse(query, 'google/gemini-2.0-flash-lite-001', output3)
                ]);

                submitBtn.disabled = false;
                submitBtn.textContent = 'Generate';
                submitBtn.classList.remove('opacity-50', 'cursor-not-allowed');
            }

            submitBtn.addEventListener('click', handleSubmit);

            queryInput.addEventListener('keypress', (e) => {
                if (e.key === 'Enter') {
                    handleSubmit();
                }
            });
        </script>
    </body>
    </html>

```

Save the above file in the `index.html` file as we did in the previos example and then run the server with Python. This is what it looks like now on localhost.

![Comparing output from different LLM provider with Puter.js][8]

And here is a sample response from all three models on the query "What is It's FOSS".

![][9]

Looks like It's FOSS is well trusted by humans as well as AI 😉

### My Final Take on Puter.js and LLMs Integration

That’s not bad! Without requiring any API keys, you can do this crazy stuff.

Puter.js utilizes the “User pays model” which means it’s completely free for developers, and your application user will spend credits from their Puter’s account for the cloud features like the storage and LLMs they will be using. I reached out to them to understand their pricing structure, but at this moment, the team behind it is still working out to come up with a pricing plan.

This new Puter.js library is superbly underrated. I’m still amazed by how easy it has made LLM integration. Besides it, you can use Puter.js SDK for authentication, storage like Firebase.

Do check out [this wonderful open source JavaScript library][3] and explore what else you can build with it.

![][10]

--------------------------------------------------------------------------------

via: https://itsfoss.com/puter-js-ai-without-api/

作者：[Bhuwan Mishra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/bhuwan/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://developer.puter.com/
[4]: http://localhost:8000
[5]: https://itsfoss.com/content/images/2025/10/data-src-image-03f7b24c-4e4e-44d4-9da1-2de9a07ff625.jpeg
[6]: https://itsfoss.com/content/images/2025/10/puter-js-ai-without-api-example.png
[7]: https://docs.puter.com/playground/
[8]: https://itsfoss.com/content/images/2025/10/data-src-image-675e3ede-e510-4810-8e1c-c7e54cbfa743.jpeg
[9]: https://itsfoss.com/content/images/2025/10/itsfoss-in-ai-views.png
[10]: https://itsfoss.com/content/images/icon/apple-icon-180x180.png
