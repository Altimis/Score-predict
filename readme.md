#  Predict the score of feedbacks

## Description
In this project, we will examine a dataset of 10,000 feedback from music professional societies (influencer_id) to artists/bands (band_id) accompanied with a score between 0 and 1 (score).  

As expected in this challenge, the objective is to extract relevant information from the data and then use the feedbacks to train a machine learning algorithm in order to be able to predict the score.  

The first step is the exploratory data analysis where I used some measures and visualizations to :  

- Remove duplicate feedbacks  
- Ddetect outliers  
- Detect the language of the feedbacks and visualize their ength  
- Clean and pre-process the feedbacks  
- Use sentiment analysis to analyze the sentiment of the feedbacks for each score  

In the second step, I used two approach for predictive modeling :  

- TF-IDF + regression in the case of continuous score, and classication if we consider a binary score of 0 or 1 (0 if score < 0.5 and 1 if score > 0.5).  
- Word embeddings + LSTM model  

TF-IDF + SVM model for classification achieved the best performance with an Area Under the Curve of P/R of 0.962.

## Data
Feedback dataset was provided by Groover as a part of a challenge.  

## Requirements 
The requirements.txt file contains all the libaries needed to run the code.  
For the predictive modeling part, an embeddings weigths file was used to initialize the embeddings layer. The glove file is [here](https://nlp.stanford.edu/projects/glove/)

## Conclusion 
In conclusion, the TF-IDF scored better in the classification of the feedback score (1 or 0, meaning good or bad feedback). The hypothesis I made earlier on the effectiveness of the TF-IDF approach in our problem has been validated (unless we can use another version of RNN or better pre-trained embeddings weights). The unbalanced scores forced me to consider this problem as binary (0 or 1) because there are few examples (feedbacks) that have scores strictly between 0.0 and 1.0 (0.25 for example). Although the regression models gave encouraging results on our data (0.08 MSE), the model will not be robust enough to accurately predict the score of feedback outside of our data set that could be related to scores between 0 and 1. There are several possible solutions to this problem. The first option is to collect feedbacks of different scores, the second option is to use text augmentation techniques, and the third option is to oversample or undersample the dataset. As for the other languages, I have removed them from the dataset, assuming that they will only represent noise during the training phase with new words from each language. I suggest either collecting more data on these languages or focusing only on feedback in English/French.  

## Note
Execute the offline mode for plotly to be able to show the figures, here are some examples of the figures:

### Score distribution
![image info](newplot (8).png)  

### Average rating - Numbre of ratings
![image info](newplot (9).png)  

### Polarity - Subjectivity
![image info](newplot (10).png)  
