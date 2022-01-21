# Reviews Analysis
I perform a Sentiment Analysis, also known as Opinion Mining, on Amazon’s reviews for the purpose to extract subjective information by analyzing text data written by users. The main goal is to identify the user’s subjectivity and classify the statements into two different groups of sentiments. I also perform a clustering analysis on the
reviews in order to discover similarities. Indeed, understanding purchase patterns has significant impact on similar item suggestions, which is a crucial component to the Amazon experience.
I download the data from this web site https://drive.google.com/drive/folders/0Bz8a_Dbh9Qhbfll6bVpmNUtUcFdjYmF2SEpmZUZUcVNiMUw1TWN6RDV3a0JHT3kxLVhVR2M?resourcekey=0-TLwzfR2O-D2aPitmn5o9VQ. The code comes with a data loader which automatically unzip the data.

# Preprocessing
For NLP projects, text preprocessing is traditionally a vital step as it has a potential impact on the final performance of our models. The first step we made
was to convert the numerical rating information in two classes (positive and negative). In particular, ratings > 3 were classified as *positive* and consequently ratings ≤ 3 were classified as *negative*.
Some fundamental preprocessing steps i made include:
- Lowecasing;
- Punctuations, urls, additional space and digit removal;
- Stop words remotion (e.g. 'the', 'a'..)
- Conversion of emoticons and emoji in word format (good/bad);
- Chat words conversion (e.g. 'imo' become 'in my opinion');
- Expansion of contractions (e.g. ’won’t’ corresponds to ’will not’). 

As last I perform lemmatization and stemming to reduce the inflactions.
It follows an example of my preprocessing:

- Before: *’Pitch Black plays perfectly, but for some reason Chronicles is still terrible in this set :(.’*
- After with stemming: *’pitch black play perfectli reason chronicl terribl set bad’*.

I will focus on Bag of Words and TF-IDF for words representation.
# Classification and Clustering
The first task I faced was classify the preprocessed reviews as positive or negative. I tried performing some machine learning classifiers for predicting the sentiments of each review. In particular, we tested these classifiers:
- AdaBoost Classifier;
- Multilayer Perceptron;
- Neural Network.

I decided to test both MLP and NN, because in MLP it is not possible to specify the type of layer and execute any kind of regularitazion.
Furthermore, I wanted to understand if it was better a customized neural networks or a classical MLP. For evaluating our candidate model for the prediction
of sentiment binary-classification, I computed several metrics, but in particular I used the accuracy on the test data set.

Since Clustering is inherently an unsupervised algorithm, I have to specify the number of clusters before. In this case, I perform a Low-Rank Approximation
using a Dimensionality reduction technique using a Truncated Singular Value Decomposition (SVD). Thus, the clustering algorithms I used, worked better in the new dimensional
space and they were faster.
I used the K-means algorithm and the agglomerative ones. I found out the optimal number of cluster with the Elbow Visualizer for the K-means and a Dendogram for the agglomerative approach.
