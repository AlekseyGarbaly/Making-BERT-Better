# Making-BERT-Better

This project was a team effort comprised of Aleksey Garbaly, Rachel Rystedt, and Amit Bista. A paper that was written for this project can be provided upon request.

The BERT model on Google Colab already has instructions, this ReadME is just outlining what was done in the project and the conclusions.

The project's motivation was to improve an existing sentiment analysis models using a state-of-the-art (SOTA) model such as BERT. BERT and other NLP models are often large
and costly to train, limiting the amount of people that could use them and improve upon them. In this project various ways to make BERT better to make it more available to others are explored. When optimal parameters are found, they could be combined to get the best possible BERT model. 

The dataset the team choose came from a text processing challenge on Kaggle, the URL for the dataset was found on: https://www.kaggle.com/c/twitter-sentiment-analysis2
The team went through data preparation steps to ensure the data was ready to be input into BERT. irst regular expressions were used to clean any strings that the team felt were not deterministic for sentiment analysis. Removing hashtag may influence sentiment but we wanted to extract sentiment from sentences, not being influenced y the subject the sentence was directed toward We also removed numbers as they were additional data in the tweets that did not help predict a tweets sentiment. We also removed blank tweets as
they could not be tokenized by the model and caused problems when training.

Setting up local environments became a time-consuming process for the team, as we ran into installation issues with Transformers, a needed package for BERT. To solve for this the team used Google Colab as the cloud server to execute our code on. The model used in the paper was based on a prewritten Google Colab notebook found in the citation.

BERT, Bidirectional Encoder Representations from Transformers, was introduced by researchers at Google AI Language. It provides state-of-the-art results in various NLP tasks that includes Question Answering (SQuADv1.1), Natural Language Inference (MNLI) etc. This was the model used as it had a lot of documentation. While there are many metrics that can measure how well models perform for any given tasks, the f1 score is a balanced one because it provides a combination precision and recall. Precision is a measure of how exact your predictions are while the recall compares how many predicted true positives there are compared to the actual number of positives, it can be thought as the sensitivity.

Implemented Model Improvements:

MobileBERT: MobileBERT was used as a way for our team to quickly test out if we could get hyperparameter tuning to improve the model's accuracy. MobileBERT is a lite version of BERT Base that has bottleneck layers to help remove noise and increase processing power. The model was trained varying epochs from 1 to 5, using epoch 1 as a base, learning rates and batch sizes were also changed. Unfortunately, The F1 score did not change any significant amount for any changes made to the model.

1 Epoch is Enough: This method for BERT improvement came from a paper that looked at trying to reduce training time and improve the overall model. They found that by training on a larger dataset and training on less epochs, they sped up the training and reduced overfitting without needing to perform regularization as it slowed down the training. Generally, they state the following “Training for E epochs is roughly equivalent to training on a shuffled dataset consisting of E copies of the original dataset for one epoch”. When the epoch was reduced from three epochs to one epoch, the training data was also increased from threefold. There was a slight increase in training size and a small increase in the F1 score. These results differ from the results in the paper that was referenced in the methods, this might have been due to not changing the iteration parameter and small dataset used.
