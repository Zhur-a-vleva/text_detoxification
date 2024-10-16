# Solution Building. Report 1

## Hypothesis 1: data exploration
I'll honestly admit that I think my data research is pretty bad. I should have cleaned the dataset better of cases that did not change toxicity at all or that were not really relevant to the task at hand (for example, in some places there were just typos instead of toxic words). However, this task was not done in the best physical condition, so I decided not to change the dataset much. 

The `toxic` column of the new dataset contains texts that have a higher level of toxicity than the other text in the pair. The `normal` column contains texts that have a lower toxicity level than the other text in the pair. The `toxic_reduction` column contains values that indicate how much the toxicity level decreased from the original text to the paraphrased text. This dataset I then used to train the model

## Hypothesis 2: data preprocessing
At first I thought I had to do some special preprocessing, but since it's an nlp and not a cv, I ended up with the classic preprocessing steps: `clean` the text from unnecessary characters, bring it to the `same case`, `tokenize` it, `remove stopwords` and `lemmatize` it

## Hypothesis 3: NLP task, language model
In order to solve the problem of text detoxification, several approaches can be used:
1. Replace specific toxic words with non-toxic counterparts
2. Apply a language translation model

The 1st approach seemed to me too algorithmic, besides it does not take into account the context at all, which significantly affects the quality. Consequently, I decided to dive into language models. If we consider the task differently, we get: translate from toxic English to non-toxic English. From here, we can take popular pre-trained models for translation and finalize them on our dataset. My choice was `T5-small`, as its performance in the article I found was the best for this task

## Hypothesis 4: bad tokenizing or small part of dataset
Before running model training on the entire dataset, I selected only a portion of it and ran `10 epochs` of training. However, after that my model, instead of reducing the toxicity of the text, simply translated it into German, with the sentence remaining just as toxic :)

I enlisted the help of my smarter friends, who suggested to me that the issue could be either bad tokenization or that I had trained on too small a dataset so far.

Both are true. The `T5-small` is designed to translate text in different languages where English, German and others are available. It trained on not enough examples and therefore translated the text into German. This problem went away after training on the full dataset, but the model did not do as well on detoxification, hence the tokenization (or maybe even earlier, the dataset preprocessing stage) was poor. However, I lack the experience to redo it in a better way

## Result
The model fulfills its purpose, though not as well as I would have liked. It is possible to improve dataset preprocessing and tokenization. The main thing is that I gained a little more knowledge than I had before

P.s. and at the same time I got a laugh out of German.
