[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Practice parsing text in NLP with Python)
[#]: via: (https://opensource.com/article/20/8/intro-python-nltk)
[#]: author: (Girish Managoli https://opensource.com/users/gammay)

Practice parsing text in NLP with Python
======
Get to know the foundational concepts behind natural language
processing.
![Hands on a keyboard with a Python book ][1]

Natural language processing (NLP) is a specialized field for analysis and generation of human languages. Human languages, rightly called natural language, are highly context-sensitive and often ambiguous in order to produce a distinct meaning. (Remember the joke where the wife asks the husband to "get a carton of milk and if they have eggs, get six," so he gets six cartons of milk because they had eggs.) NLP provides the ability to comprehend natural language input and produce natural language output appropriately.

Computational linguistics (CL) is the larger field of linguistic comprehension and modeling. NLP is a subset of CL that deals with the engineering aspects of language understanding and generation. NLP is an interdisciplinary domain that touches on multiple fields including artificial intelligence (AI), machine learning (ML), deep learning (DL), mathematics, and statistics.

Some of the applications you can build with NLP include:

  * **Machine translation:** With over 6,000 languages in the world, NLP coupled with neural machine translation can ease text translation from one language into other.
  * **Chatbots:** Personal assistants like Alexa, Siri, and the open source [Mycroft][2] are blended into our lives today. NLP is at the core of these chatbots, helping machines analyze, learn, and understand speech as well as provide vocal response.
  * **Voice enablement:** NLP makes it possible to serve customers in healthcare, travel, retail, and other industries in a friendly way.
  * **Sentiment analysis:** Businesses always want to have a finger on customers' pulse and take proactive actions when they sense discontent. NLP makes this possible.
  * **HR productivity:** Human resources professionals must handle a mountain of documents, and NLP can use document process automation to alleviate some of that burden.



### NLP building blocks

Like a skyscraper is built brick by brick, you can build large applications like the ones above by using NLP's fundamental and essential building blocks.

There are several open source NLP libraries available, such as Stanford CoreNLP, spaCy, and Genism in Python, Apache OpenNLP, and GateNLP in Java and other languages.

To demonstrate the functions of NLP's building blocks, I'll use Python and its primary NLP library, Natural Language Toolkit ([NLTK][3]). NLTK was created at the University of Pennsylvania. It is a widely used and convenient starting point for getting into NLP. After learning its concepts, you can explore other libraries to build your "skyscraper" NLP applications.

The fundamental building blocks covered in this article are:

  * Tokenize into sentences and words
  * Stopwords
  * Collocations
  * Parts of speech identification
  * Stemming and lemmatization
  * Corpus



### Setup

This article assumes you are [familiar with Python][4]. Once you have Python installed, download and install NLTK:


```
`pip install nltk`
```

Then install NLTK Data:


```
`python -m nltk.downloader popular`
```

If you have lots of storage space and good bandwidth, you can also use `python -m nltk.downloader all`. See NLTK's [installation page][5] for help.

There's also a user interface to select data to download, which you can start with the Python shell:


```
Python 3.8.2 ...
Type "help", ...

&gt;&gt;&gt; import nltk
&gt;&gt;&gt; nltk.download()
```

![NLTK UI Screenshot][6]

(Opensource.com, [CC BY-SA 4.0][7])

### Tokenize sentences and words

The first step in text analysis and processing is to split the text into sentences and words, a process called tokenization. Tokenizing a text makes further analysis easier. Almost all text analysis applications start with this step.

Here are some examples with this line of text:


```
`text = "Computers don't speak English. So, we've to learn C, C++, ,C#, Java, Python and the like! Yay!"`
```

Sentence tokenization:


```
from nltk.tokenize import sent_tokenize
sentences = sent_tokenize(text)
print(len(sentences), 'sentences:', sentences)
```

Word tokenization:


```
from nltk.tokenize import word_tokenize
words = word_tokenize(text)
print(len(words), 'words:', words)

[/code] [code]`29 word(s): ['Computers', 'do', "n't", 'speak', 'English', '.', 'So', ',', 'we', "'ve", 'to', 'learn', 'C', ',', 'C++', ',', ',', 'C', '#', ',', 'Java', ',', 'Python', 'and', 'the', 'like', '!', 'Yay', '!']`
```

NLTK uses regular expressions internally for tokenization. A keen reader may ask whether you can tokenize without using NLTK. Yes, you can. However, NLTK is well-designed considering all the variations out there; for example, something like nltk.org should remain one word `['nltk.org']` not `['nltk', 'org']`:


```
`text = "I love nltk.org"`
```

If you tokenize using the code above, nltk.org is retained as one word:


```
1 sentence(s): ['I love nltk.org']
3 word(s): ['I', 'love', 'nltk.org']
```

NLTK does not offer the ability to replace contractions like "don't" with "do not" and "we've" with "we have," but the [pycontractions][8] library can help.

#### Try it yourself

Using Python libraries, download Wikipedia's page on [open source][9] and tokenize the text.

### Stopwords

A language like English has many "fluff" words (technically called "stopwords") that are necessary in speech and writing but do not carry value in analysis. NLTK can identify and remove these stopwords to help text processing focus on requisite words.

See the words considered stopwords:


```
from nltk.corpus import stopwords
stop_words = stopwords.words('english')
print(len(stop_words), "stopwords:", stop_words)

[/code] [code]`179 stopwords: ['i', 'me', 'my', 'myself', 'we', ..., "wouldn't"]`
```

Tokenize the text first, then filter out the stopwords:


```
text = "Computers don't speak English. So, we've to learn C, C++, Java, Python and the like! Yay!"

from nltk.tokenize import word_tokenize
words = word_tokenize(text)

print(len(words), "in original text:", words)

[/code] [code]`25 words in original text: ['Computers', 'do', 'not', 'speak', 'English', '.', 'So', ',', 'we', 'have', 'to', 'learn', 'C', ',', 'C++', ',', 'Java', ',', 'Python', 'and', 'the', 'like', '!', 'Yay', '!']`[/code] [code]

words = [word for word in words if word not in stop_words]
print(len(words), "without stopwords:", words)

[/code] [code]`18 words without stopwords: ['Computers', 'speak', 'English', '.', 'So', ',', 'learn', 'C', ',', 'C++', ',', 'Java', ',', 'Python', 'like', '!', 'Yay', '!']`
```

The text still has punctuation marks, which add to the noise. To remove them, use Python's string class. Some punctuation is important, e.g., the question mark. This method can be used to remove punctuation (not using NLTK).

See the characters considered to be punctuation:


```
import string
punctuations = list(string.punctuation)
print(punctuations)

[/code] [code]`['!', '"', '#', '$', '%', '&', "'", '(', ')', '*', '+', ',', '-', '.', '/', ':', ';', '<', '=', '>', '?', '@', '[', '\\', ']', '^', '_', '`', '{', '|', '}', '~']`
```

Remove punctuation:


```
words = [word for word in words if word not in punctuations]
print(len(words), "words without stopwords and punctuations:", words)

[/code] [code]`11 words without stopwords and punctuations: ['Computers', 'speak', 'English', 'So', 'learn', 'C', 'C++', 'Java', 'Python', 'like', 'Yay']`
```

#### Try it yourself

Using the Python libraries, download Wikipedia's page on [open source][9] and remove the stopwords. What percentage of the page is stopwords?

### Collocations

Collocation refers to two (or more) words that tend to appear frequently together. Collocations help in understanding text formation and aid in text search and similarity comparison.

Use a longer text file from [Project Gutenburg][10] for this example. (Project Gutenberg is an initiative to digitize books.)

Download the text:


```
# coding: utf-8

import urllib.request

# Download text and decode
# Note: Set proxy if behind a proxy (<https://docs.python.org/2/library/urllib.html>)
url = "<http://www.gutenberg.org/files/1342/1342-0.txt>"
text = urllib.request.urlopen(url).read().decode()
print(text)

[/code] [code]

The Project Gutenberg EBook of Pride and Prejudice, by Jane Austen
This eBook is for the use of anyone anywhere at no cost and with
...
      Chapter 1
      It is a truth universally acknowledged, that a single man in
      possession of a good fortune
...
      bringing her into Derbyshire, had been the means of
      uniting them.
```

Preprocessing (tokenization, de-stopwording, and de-punctuating):


```
# Tokenize
from nltk.tokenize import word_tokenize
text = word_tokenize(text)

# Remove stopwords
from nltk.corpus import stopwords
stops = stopwords.words('english')
# print(stops)
words = [word for word in text if word not in stops]

# Remove punctuations
import string
punctuations = list(string.punctuation)
# print(punctuations)

words = [word for word in words if word not in punctuations]
print("Without punctuations:", words)

[/code] [code]`Preprocessed: ['The', 'Project', 'Gutenberg', 'EBook', 'Pride', 'Prejudice', 'Jane', 'Austen', ...`
```

Bigrams (two words that appear together):


```
# Bigrams
from nltk.metrics import BigramAssocMeasures
from nltk.collocations import BigramCollocationFinder
bigram_collocation = BigramCollocationFinder.from_words(words)
# Top 10 most occurring collocations
print("Bigrams:", bigram_collocation.nbest(BigramAssocMeasures.likelihood_ratio, 10))

[/code] [code]`Bigrams: [('”', '“'), ('Mr.', 'Darcy'), ('Lady', 'Catherine'), ('”', 'said'), ('Mrs.', 'Bennet'), ('Mr.', 'Collins'), ('Project', 'Gutenberg-tm'), ('“', 'I'), ('Sir', 'William'), ('Miss', 'Bingley')]`
```

A keen reader may observe that the double-quote characters—” (codepoint 8220) and “ (codepoint 8221)—still occur in the text after de-punctuation. `string.punctuation` does not detect these as these being different than the standard double quote “ (codepoint 34). To process these, add the characters to the punctuation list.

Trigrams (three words that appear together):


```
# Trigrams
from nltk.collocations import TrigramCollocationFinder
from nltk.metrics import TrigramAssocMeasures
trigram_collocation = TrigramCollocationFinder.from_words(text)
# Top 10 most occurring collocations
print("Trigrams:", trigram_collocation.nbest(TrigramAssocMeasures.likelihood_ratio, 10))

[/code] [code]`Trigrams: [('late', 'Mr.', 'Darcy'), ('Mr.', 'Darcy', 'returned'), ('saw', 'Mr.', 'Darcy'), ('friend', 'Mr.', 'Darcy'), ('Mr.', 'Darcy', 'walked'), ('civility', 'Mr.', 'Darcy'), ('Mr.', 'Darcy', 'looked'), ('said', 'Mr.', 'Darcy'), ('surprised', 'Mr.', 'Darcy'), ('Mr.', 'Darcy', 'smiled')]`
```

"Mr. Darcy" is almost everywhere! You can imply he is the protagonist of the novel. This is an example of information extraction using NLP.

#### Try it yourself

Using the Python libraries, download Wikipedia's page on [open source][9]. You can hypothesize that "open source" is the most occurring bigram and "open source code" is the most occurring trigram. See if you can confirm this.

### Parts of speech identification

NLTK has the ability to identify words' parts of speech (POS). Identifying POS is necessary, as a word has different meanings in different contexts. The word "code" as noun could mean "a system of words for the purposes of secrecy" or "program instructions," and as verb, it could mean "convert a message into secret form" or "write instructions for a computer." This context cognizance is necessary for correct text comprehension.

Here is an example using this text:


```
`text = "Computers don't speak English. So, we've to learn C, C++, Java, Python and the like! Yay!"`
```

Preprocess the text as you did earlier:


```
import nltk
from nltk.tokenize import word_tokenize

words = word_tokenize(text)
```

Identify the POS tags:


```
pos_tagged_text = nltk.pos_tag(words)
print(pos_tagged_text)

[/code] [code]`[('Computers', 'NNS'), ('do', 'VBP'), ("n't", 'RB'), ('speak', 'VB'), ('English', 'NNP'), ('.', '.'), ('So', 'RB'), (',', ','), ('we', 'PRP'), ("'ve", 'VBP'), ('to', 'TO'), ('learn', 'VB'), ('C', 'NNP'), (',', ','), ('C++', 'NNP'), (',', ','), ('Java', 'NNP'), (',', ','), ('Python', 'NNP'), ('and', 'CC'), ('the', 'DT'), ('like', 'JJ'), ('!', '.'), ('Yay', 'NN'), ('!', '.')]`
```

NNS, VBP, etc. are POS codes [defined][11] by the University of Pennsylvania, and you can also see them programmatically:


```
`nltk.help.upenn_tagset()`[/code] [code]

NNS: noun, common, plural
    undergraduates scotches bric-a-brac products bodyguards facets coasts
    divestitures storehouses designs clubs fragrances averages
    subjectivists apprehensions muses factory-jobs ...
VBP: verb, present tense, not 3rd person singular
    predominate wrap resort sue twist spill cure lengthen brush terminate
    appear tend stray glisten obtain comprise detest tease attract
    emphasize mold postpone sever return wag ...
...
```

You can see the POS definition of each word in the sentence:


```
for pos_tag_word in pos_tagged_text:
    print(pos_tag_word[0], ":")
    nltk.help.upenn_tagset(pos_tag_word[1])

[/code] [code]

Computers :
NNS: noun, common, plural
        ...
do :
VBP: verb, present tense, not 3rd person singular
        ...
n't :
RB: adverb
        ...
speak :
VB: verb, base form
        ...
English :
NNP: noun, proper, singular
        ...
. :
.: sentence terminator
```

#### Try it yourself

Using the Python libraries, download Wikipedia's page on [open source][9] and identify the POS of all words in the text.

### Stemming and lemmatization

Words are typically [inflected][12] (e.g., letters suffixed, affixed, etc.) to express their forms (e.g., plural, tense, etc.). `Dog -> Dogs` is an example of inflection. Usually, words must be compared in their native forms for effective text matching.

Stemming and lemmatization are two methods to convert a word to a non-inflected form. The essence of both stemming and lemmatization is the same: to reduce a word to its most native form. But they differ in how they do it.

  * **Stemming** uses a simple mechanism that removes or modifies inflections to form the root word, but the root word may not be a valid word in the language.
  * **Lemmatization** also removes or modifies the inflections to form the root word, but the root word is a valid word in the language.



Lemmatization uses a word dataset (called a corpus, discussed in the next section) to arrive at root words; hence, it is slower than stemming. There are cases when stemming suffices, and in other cases, lemmatization is required.

NLTK has several stemmers and lemmatizers (e.g., RegexpStemmer, LancasterStemmer, PorterStemmer, WordNetLemmatizer, RSLPStemmer, and more). There are also many built-in stemmers and lemmatizers you can choose from (see the [nltk.stem][13] package).

To compare them, try out PorterStemmer and WordNetLemmatizer.

Create an instance of PorterStemmer:


```
import nltk
stemmer = nltk.stem.PorterStemmer()
```

Stem the word "building":


```
word = "building"
print("Stem of", word, stemmer.stem(word))

[/code] [code]`Stem of building : build`
```

Stemming has no POS cognizance, so the word "building," in noun or verb form, is stemmed to "build."

This is not the case with lemmatization using WordNetLemmatizer:


```
lemmatizer = nltk.stem.WordNetLemmatizer()
word = "building"
pos = 'n';
print("Lemmatization of", word, "(" , pos, "):", lemmatizer.lemmatize(word, pos))
pos = 'v';
print("Lemmatization of", word, "(" , pos, "):", lemmatizer.lemmatize(word, pos))

[/code] [code]

Lemmatization of building ( n ): building
Lemmatization of building ( v ): build
```

Lemmatization takes more time (slightly in this example, but noticeable) than stemming.

#### Try it yourself

Using the Python libraries, download Wikipedia's page on [open source][9] and preprocess and convert the text to its native forms. Try it with various stemming and lemmatizing modules. Use Python's timer module to measure their performance.

### Corpus

A corpus in NLTK is a dataset of text. NLTK makes several corpora available. Corpora aid in text processing with out-of-the-box data. For example, a corpus of US presidents' inaugural addresses can help with the analysis and preparation of speeches.

Several corpus readers are available in NLTK. Depending on the text you are processing, you can choose the most appropriate one. The required corpus must be installed with Data (see the [Setup][14] section above).

There are several types of corpus that indicate the structure and type of data that the corpus provides. The available corpora list can be found in the `nltk_data` UI (see Setup).

![NLTK UI Installed][15]

(Opensource.com, [CC BY-SA 4.0][7])

A corpus is accessed through a reader. The reader to be used for a corpus depends on the type on corpus. For example, the Gutenberg corpus holds text in plain text format and is accessed with [PlaintextCorpusReader][16]. The Brown corpus has categorized, tagged text and is accessed with [CategorizedTaggedCorpusReader][17]. The readers follow a tree structure. Here are some corpora and their readers.

![Various corpora and their associated readers][18]

(Opensource.com, [CC BY-SA 4.0][7])

Here's how to access corpora.

First, create a utility function to show corpus info based on the corpus reader type:


```
def corpus_info(corpus):
    print(corpus)
    print()
    print("README:", corpus.readme())
    print()
    files = corpus.fileids()
    print(len(files), "files:")
    print(files)
    print()
    file = files[0]
    text = corpus.raw(file)
    print("File", file, len(corpus.paras(file)), "paras", len(corpus.sents(file)), "sentences", len(corpus.words(file)), "words", ":")
    print(text.encode("utf-8"))
    print()
    if isinstance(corpus, nltk.corpus.TaggedCorpusReader):
        tagged_words = corpus.tagged_words()
        print(len(tagged_words), "tags:")
        print(tagged_words)
        print()
    if isinstance(corpus, nltk.corpus.CategorizedTaggedCorpusReader):
        categories = corpus.categories()
        print(len(categories), "categories:")
        print(categories)
        print()
        category = categories[-1]
        files = corpus.fileids(category)
        print(len(files), "files in category", category, ":")
        print(files)
        print()
        file = files[0]
        print("File:", file, len(corpus.paras(file)), "paras", len(corpus.sents(file)), "sentences", len(corpus.words(file)), "words")
        print()
        print("Raw text:")
        text = corpus.raw(file)
        print(text)
        print()
        print("Tagged text:")
        tagged_words = corpus.tagged_words(file)
        print(tagged_words)
        print()
```

Here are two corpora examples:

  * ABC is a collection of news from the Australian Broadcasting Commission. This is a basic plain text corpus: [code]`corpus_info(nltk.corpus.abc)`[/code] [code] &lt;PlaintextCorpusReader in '.../corpora/abc' (not loaded yet)&gt;
   
README: b'Australian Broadcasting Commission 2006\nhttp://www.abc.net.au/\n\nContents:\n* Rural News    <http://www.abc.net.au/rural/news/\\n\>* Science News  <http://www.abc.net.au/science/news/\\n\\n>'
   
2 files:
['rural.txt', 'science.txt']
   
File: rural.txt 2425 paras 13015 sentences 345580 words :
'PM denies knowledge of AWB kickbacks\nThe Prime Minister has denied ... 
```
  * Brown corpus has about a million words of contemporary American English words put together by Brown University: [code]`corpus_info(nltk.corpus.brown)`[/code] [code] &lt;CategorizedTaggedCorpusReader in '.../corpora/brown' (not loaded yet)&gt;
   
README: BROWN CORPUS
A Standard Corpus of Present-Day Edited American
...
   
500 files:
['ca01', 'ca02', 'ca03', ...]
   
File ca01 67 paras 98 sentences 2242 words :
b"\n\n\tThe/at Fulton/np-tl County/nn-tl Grand/jj-tl Jury/nn-tl ...
   
1161192 tags:
[('The', 'AT'), ('Fulton', 'NP-TL'), ...]
   
15 categories:
['adventure', 'belles_lettres', 'editorial', 'fiction', 'government', 'hobbies', 'humor', 'learned', 'lore', 'mystery', 'news', 'religion', 'reviews', 'romance', 'science_fiction']
   
6 files in category science_fiction :
['cm01', 'cm02', 'cm03', 'cm04', 'cm05', 'cm06']
   
File: cm01 57 paras 174 sentences 2486 words
   
Raw text:
Now/rb that/cs he/pps ...
   
Tagged text:
[('Now', 'RB'), ('that', 'CS'), ('he', 'PPS'), ...]
```



Imagine what you could do with such corpora at your disposal! With the Brown corpus, you can train a model to categorize and tag texts for a chatbot to understand human intent better, for example. You can also create your own corpus.

### Next steps

In my next article, I'll expand your knowledge of NLP's building blocks by showing you how to compare parsed data, implement entity recognition, and more with NLP and NLTK.

For now, try training a machine-learning model using the Brown corpus to categorize text and tag words. Apply this to a part of a [PG Woodhouse book][19] and see what category it identifies.

--------------------------------------------------------------------------------

via: https://opensource.com/article/20/8/intro-python-nltk

作者：[Girish Managoli][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://opensource.com/users/gammay
[b]: https://github.com/lujun9972
[1]: https://opensource.com/sites/default/files/styles/image-full-size/public/lead-images/python-programming-code-keyboard.png?itok=fxiSpmnd (Hands on a keyboard with a Python book )
[2]: https://opensource.com/article/20/6/open-source-voice-assistant
[3]: http://www.nltk.org/
[4]: https://opensource.com/article/17/10/python-101
[5]: https://www.nltk.org/install.html
[6]: https://opensource.com/sites/default/files/uploads/nltk-ui.png (NLTK UI Screenshot)
[7]: https://creativecommons.org/licenses/by-sa/4.0/
[8]: https://pypi.org/project/pycontractions/
[9]: https://en.wikipedia.org/wiki/Open_source
[10]: https://www.gutenberg.org/
[11]: https://www.ling.upenn.edu/courses/Fall_2003/ling001/penn_treebank_pos.html
[12]: https://en.wikipedia.org/wiki/Inflection#Examples_in_English
[13]: https://www.nltk.org/api/nltk.stem.html
[14]: tmp.XEvF53uYEn#Setup
[15]: https://opensource.com/sites/default/files/uploads/nltk-ui-installed.png (NLTK UI Installed)
[16]: https://www.nltk.org/_modules/nltk/corpus/reader/plaintext.html
[17]: https://www.nltk.org/_modules/nltk/corpus/reader/tagged.html
[18]: https://opensource.com/sites/default/files/uploads/corpora.jpg (Various corpora and their associated readers)
[19]: http://www.gutenberg.org/ebooks/author/783
