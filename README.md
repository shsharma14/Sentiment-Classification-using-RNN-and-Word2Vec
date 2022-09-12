# Sentiment-Classification-using-RNN-and-Word2Vec

In any language, tokens may be deeply interrelated even when they are far apart in a sentence. 
For example, in a sentence like "The young woman went to the movies with her friends", the subject “woman” immediately precedes its main verb “went.” For sentence like these, traditional RNNs and CNNs will have no problem in learning the relationship.

But for a sentence like "The young woman, having found a free ticket on the ground, went to the movies", the noun and verb are no longer one
time step apart in the sequence. Traditional RNNs have one major drawback: a token’s effect is almost completely lost by the time two tokens
have passed. So, it will have difficulty picking up the relationship between "woman" and "went" and it will overemphasize on the relationship
between the words "woman" and "having" which are one time step apart.

### Traditional RNNs suffer from 2 problems:
1. Vanishing Gradients
2. Exploding Gradients

The weights in a recurrent network decay too quickly in time as you roll through each sentence.
An LSTM (Long short-term memory) can overcome this drawback as it can remember important time events in the past across the entire input
sequence. LSTMs work so well they have replaced recurrent neural networks in almost all applications involving time series, discrete
sequences, and NLP.


## Details of the Project: 
Using this project, I have tried to analyze the disadvantages of using traditional RNN for text data. 
They suffer from vanishing/explodient gradient problem and tend to forget the words after a certain state of time. But in many languages like English, a word that appears first might be related to the second last word in a long sentence. These kind of dependencies in English language exists often and a traditional RNN model
fails to detect such cases. Common NLP applications such as Text Summarization, Sentence Completion, Machine Translation can't work well if we do not save the information while modeling.

**LSTMs and GRUs** are type of Recurrent Neural Networks that allows us to store information with memory units and the fascinating part is that
they can be trained on what information to store and what information to discard. This is achieved by using 4 feed-forward neural networks
inside an LSTM cell.

### Dataset and approach: 
**I used IMDB review dataset consisting of 25000 sentences (12500 negative and 12500 positive reviews) to make a sentiment classification
word based model.** Each word was converted into a numerical representation known as word embeddings by using pre-trained embeddings
trained on the Google News dataset. It contains embeddings for 3 million words. NLPIA package has a function to load word2vec
representations but I used gensim.

Our initial model consisted of a single LSTM layer with dropout (to avoid overfitting). It achieved an accuracy of ~81% but it was trained on only
5000 randomly sampled sentences due to high memory requirement. If the system allowed more data, accuracy would have been more. I used
different epochs, batch_size, number of neurons in LSTM layer and the maximum token length in each sentence to make a more accurate
model but accuracy remained around 82%.

Relation between words is difficult to model than predicting the next character given some character sequence. Even though character modeling is not used these days, I have used character modeling for sentiment classification. That model was overfit with ~99% train accuracy
and only ~52% validation accuracy which is almost similar to random guessing.

But, even though character modeling can't be used to figure out sentiment of a sentence, it can be used to generate text similar to Shakespeare
writing style. For this model, I have used Shakespeare sonnet from the Gutenberg project. When we are trying to generate text based on some
defined pattern (tone and syntax similar to Shakespeare), overfitting is ideal. I get a validation accuracy of ~50% but this not same as randomly
guessing the next character because next character could be from a set of 50 different characters.

Overall, I have used IMDB dataset for sentiment classification, with word-level modeling and character level modeling approach. I got into
character modeling to study how NLP applications like text generation work.
