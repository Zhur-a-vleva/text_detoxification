# Final Solution. Report 2

## Data analysis
Ananalysis of the data revealed that some toxic words are simply misspelled words and some translations are just as toxic as the original

The new dataset was created. The `toxic` column of the new dataset contains texts that have a higher level of toxicity than the other text in the pair. The `normal` column contains texts that have a lower toxicity level than the other text in the pair. The `toxic_reduction` column contains values that indicate how much the toxicity level decreased from the original text to the paraphrased text. This dataset I then used to train the model

## Model Specification
I decided to dive into language models. If we consider the task differently, we get: translate from toxic English to non-toxic English. From here, we can take popular pre-trained models for translation and finalize them on our dataset. My choice was `T5-small`, as its performance in the article I found was the best for this task. I decided not to freeze the weights as I felt it would help the model train more for our task. I used a `learning_rate=2e-5` and a small `batch_size` so as not to overload the GPU during training. Every `100 steps` I saved a checkpoint for reliability and saved the model to a separate folder at the very end. `10 epochs` was enough, at least for homework, because 5 hours were spent on it :) Preliminary dataset was already divided into 2 parts: `train` and `test`

## Evaluation
The model was evaluated on several random sentences in traslate.txt. This is not a very objective evaluation, but I did not have the energy to perform a detailed evaluation on the entire dataset

## Result
The model fulfills its purpose, though not as well as I would have liked. It is possible to improve dataset preprocessing and tokenization. The main thing is that I gained a little more knowledge than I had before

P.s. and at the same time I got a laugh out of German.
