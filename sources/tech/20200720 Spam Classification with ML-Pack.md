[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Spam Classification with ML-Pack)
[#]: via: (https://fedoramagazine.org/spam-classification-with-ml-pack/)
[#]: author: (fed500 https://fedoramagazine.org/author/fed500/)

Spam Classification with ML-Pack
======

![][1]

### Introduction

[ML-Pack][2] is a small footprint C++ machine learning library that can be easily integrated into other programs. It is an actively developed open source project and released under a [BSD-3 license][3]. Machine learning has gained popularity due to the large amount of electronic data that can be collected. Some other popular machine learning frameworks include [TensorFlow][4], [MxNet][5], [PyTorch][6], [Chainer][7] and [Paddle Paddle][8], however these are designed for more complex workflows than ML-Pack. On Fedora, ML-Pack is packaged by its lead developer [Ryan Curtin][9]. In addition to a command line interface, ML-Pack has bindings for [Python][10] and [Julia][11]. Here, we will focus on the command line interface since this may be useful for system administrators to integrate into their workflows.

### Installation

You can install ML-Pack on the Fedora command line using

```
$ sudo dnf -y install mlpack mlpack-bin
```

You can also install the documentation, development headers and Python bindings by using …

```
$ sudo dnf -y install  mlpack-doc \
mlpack-devel mlpack-python3
```

though they will not be used in this introduction.

### Example

As an example, we will train a machine learning model to classify spam SMS messages. To keep this article brief, linux commands will not be fully explained, but you can find out more about them by using the man command, for example for the command first command used below, _wget_

```
$ man wget
```

will give you information that _wget_ will download files from the web and options you can use for it.

#### Get a dataset

We will use an example spam dataset in Indonesian provided by Yudi Wibisono
```

```

$ wget <https://drive.google.com/file/d/1-stKadfTgJLtYsHWqXhGO3nTjKVFxm\_Q/view>
$ unzip dataset_sms_spam_bhs_indonesia_v1.zip
```

```

#### Pre-process dataset

We will try to classify a message as spam or ham by the number of occurrences of a word in a message. We first change the file line endings, remove line 243 which is missing a label and then remove the header from the dataset. Then, we split our data into two files, labels and messages. Since the labels are at the end of the message, the message is reversed and then the label removed and placed in one file. The message is then removed and placed in another file.

```
$ tr 'r' 'n' < dataset_sms_spam_v1.csv > dataset.txt
$ sed '243d' dataset.txt > dataset1.csv
$ sed '1d' dataset1.csv > dataset.csv
$ rev dataset.csv | cut -c1  | rev > labels.txt
$ rev dataset.csv | cut -c2- | rev > messages.txt
$ rm dataset.csv
$ rm dataset1.csv
$ rm dataset.txt
```

Machine learning works on numeric data, so we will use labels of 1 for ham and 0 for spam. The dataset contains three labels, 0, normal sms (ham), 1, fraud (spam), and 2 promotion (spam). We will label all spam as 1, so promotions and fraud will be labelled as 1.

```
$ tr '2' '1' < labels.txt > labels.csv
$ rm labels.txt
```

The next step is to convert all text in the messages to lower case and for simplicity remove punctuation and any symbols that are not spaces, line endings or in the range a-z (one would need expand this range of symbols for production use)

```
$ tr '[:upper:]' '[:lower:]' < \
messages.txt > messagesLower.txt
$ tr -Cd 'abcdefghijklmnopqrstuvwxyz n' < \
 messagesLower.txt > messagesLetters.txt
$ rm messagesLower.txt
```

We now obtain a sorted list of unique words used (this step may take a few minutes, so use nice to give it a low priority while you continue with other tasks on your computer).

```
$ nice -20 xargs -n1 < messagesLetters.txt > temp.txt
$ sort temp.txt > temp2.txt
$ uniq temp2.txt > words.txt
$ rm temp.txt
$ rm temp2.txt
```

We then create a matrix, where for each message, the frequency of word occurrences is counted (more on this on Wikipedia, [here][12] and [here][13]). This requires a few lines of code, so the full script, which should be saved as ‘makematrix.sh’ is below

```
#!/bin/bash
declare -a words=()
declare -a letterstartind=()
declare -a letterstart=()
letter=" "
i=0
lettercount=0
while IFS= read -r line; do
        labels[$((i))]=$line
        let "i++"
done < labels.csv
i=0
while IFS= read -r line; do
        words[$((i))]=$line
        firstletter="$( echo $line | head -c 1 )"
        if [ "$firstletter" != "$letter" ]
        then
                letterstartind[$((lettercount))]=$((i))
                letterstart[$((lettercount))]=$firstletter
                letter=$firstletter
                let "lettercount++"
        fi
        let "i++"
done < words.txt
letterstartind[$((lettercount))]=$((i))
echo "Created list of letters"

touch wordfrequency.txt
rm wordfrequency.txt
touch wordfrequency.txt
messagecount=0
messagenum=0
messages="$( wc -l messages.txt )"
i=0
while IFS= read -r line; do
        let "messagenum++"
        declare -a wordcount=()
        declare -a wordarray=()
        read -r -a wordarray <<> wordfrequency.txt
        echo "Processed message ""$messagenum"
        let "i++"
done < messagesLetters.txt
# Create csv file
tr ' '  ','  data.csv
```

Since [Bash][14] is an interpreted language, this simple implementation can take upto 30 minutes to complete. If using the above Bash script on your primary workstation, run it as a task with low priority so that you can continue with other work while you wait:

```
$ nice -20 bash makematrix.sh
```

Once the script has finished running, split the data into testing (30%) and training (70%) sets:

```
$ mlpack_preprocess_split     \
    --input_file data.csv                     \
    --input_labels_file labels.csv            \
    --training_file train.data.csv            \
    --training_labels_file train.labels.csv   \
    --test_file test.data.csv                 \
    --test_labels_file test.labels.csv        \
    --test_ratio 0.3                          \
    --verbose
```

#### Train a model

Now train a [Logistic regression model][15]:

```
$ mlpack_logistic_regression \
--training_file train.data.csv \
--labels_file train.labels.csv --lambda 0.1 \
--output_model_file lr_model.bin
```

#### Test the model

Finally we test our model by producing predictions,

```
$ mlpack_logistic_regression \
--input_model_file lr_model.bin \
 --test_file test.data.csv \
--output_file lr_predictions.csv
```

and comparing the predictions with the exact results,

```
$ export incorrect=$(diff -U 0 lr_predictions.csv \
test.labels.csv | grep '^@@' | wc -l)
$ export tests=$(wc -l < lr_predictions.csv)
$ echo "scale=2;  100 * ( 1 - $((incorrect)) \
/ $((tests)))"  | bc
```

This gives approximately 90% validation rate, similar to that obtained [here][16].

The dataset is composed of approximately 50% spam messages, so the validation rates are quite good without doing much parameter tuning. In typical cases, datasets are unbalanced with many more entries in some categories than in others. In these cases a good validation rate can be obtained by mispredicting the class with a few entries. Thus to better evaluate these models, one can compare the number of misclassifications of spam, and the number of misclassifications of ham. Of particular importance in applications is the number of false positive spam results as these are typically not transmitted. The script below produces a confusion matrix which gives a better indication of misclassification. Save it as ‘confusion.sh’

```
#!/bin/bash
declare -a labels
declare -a lr
i=0
while IFS= read -r line; do
        labels[i]=$line
        let "i++"
done < test.labels.csv
i=0
while IFS= read -r line; do
        lr[i]=$line
        let "i++"
done < lr_predictions.csv
TruePositiveLR=0
FalsePositiveLR=0
TrueZerpLR=0
FalseZeroLR=0
Positive=0
Zero=0
for i in "${!labels[@]}"; do
        if [ "${labels[$i]}" == "1" ]
        then
                let "Positive++"
                if [ "${lr[$i]}" == "1" ]
                then
                        let "TruePositiveLR++"
                else
                        let "FalseZeroLR++"
                fi
        fi
        if [ "${labels[$i]}" == "0" ]
        then
                let "Zero++"
                if [ "${lr[$i]}" == "0" ]
                then
                        let "TrueZeroLR++"
                else
                        let "FalsePositiveLR++"
                fi
        fi

done
echo "Logistic Regression"
echo "Total spam"  $Positive
echo "Total ham"  $Zero
echo "Confusion matrix"
echo "             Predicted class"
echo "                 Ham | Spam "
echo "              ---------------"
echo " Actual| Ham  | " $TrueZeroLR "|" $FalseZeroLR
echo " class | Spam | " $FalsePositiveLR " |" $TruePositiveLR
echo ""
```

then run the script

```
$ bash confusion.sh
```

You should get output similar to

Logistic Regression
Total spam 183
Total ham 159
Confusion matrix

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/spam-classification-with-ml-pack/

作者：[fed500][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/fed500/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2020/07/mlpack-1-816x346.png
[2]: https://mlpack.org
[3]: https://github.com/mlpack/mlpack/blob/master/LICENSE.txt
[4]: https://www.tensorflow.org/
[5]: https://mxnet.apache.org/
[6]: https://pytorch.org/
[7]: https://chainer.org/
[8]: http://paddlepaddle.org/
[9]: https://koji.fedoraproject.org/koji/packageinfo?packageID=15021
[10]: https://www.python.org/
[11]: https://julialang.org/
[12]: https://en.wikipedia.org/wiki/Tf%E2%80%93idf
[13]: https://en.wikipedia.org/wiki/Document-term_matrix
[14]: https://www.gnu.org/software/bash/
[15]: https://mlpack.org/doc/mlpack-3.3.1/cli_documentation.html#logistic_regression
[16]: https://towardsdatascience.com/spam-detection-with-logistic-regression-23e3709e522
