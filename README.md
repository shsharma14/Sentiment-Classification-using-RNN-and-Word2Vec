# Sentiment-Classification-using-RNN-and-Word2Vec

In any language, tokens may be deeply interrelated even when they are far apart in a sentence. 
For example, in a sentence like "The young woman went to the movies with her friends", the subject “woman” immediately precedes its main verb “went.” For sentence like these, traditional RNNs and CNNs will have no problem in learning the relationship.

But for a sentence like "The young woman, having found a free ticket on the ground, went to the movies", the noun and verb are no longer one
time step apart in the sequence. Traditional RNNs have one major drawback: a token’s effect is almost completely lost by the time two tokens
have passed. So, it will have difficulty picking up the relationship between "woman" and "went" and it will overemphasize on the relationship
between the words "woman" and "having" which are one time step apart.

## Traditional RNNs suffer from 2 problems:
1. Vanishing Gradients
2. Exploding Gradients

The weights in a recurrent network decay too quickly in time as you roll through each sentence.
An LSTM (Long short-term memory) can overcome this drawback as it can remember important time events in the past across the entire input
sequence. LSTMs work so well they have replaced recurrent neural networks in almost all applications involving time series, discrete
sequences, and NLP.
