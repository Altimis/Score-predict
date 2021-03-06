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
- 
TF-IDF + SVM model for classification achieved the best performance with an Area Under the Curve of P/R of 0.962.




