# Disaster Response Pipeline

## Project Structure:

app     
| - template     
| |- master.html  # main page of web app     
| |- go.html  # classification result page of web app     
|- run.py  # Flask file that runs app     

data    
|- disaster_categories.csv  # data to process     
|- disaster_messages.csv  # data to process    
|- process_data.py      
|- DisasterResponse.db   # database to save clean data      

models
|- train_classifier.py             
|- classifier.pkl  # saved model           

README.md                

visul           
|- visualization1         
|- visualization2          

notebooks        
|- ETL Pipeline Preparation.ipynb #Jupyter notebook to test and prepare the ETL process          
|- Machine Learning Pipeline Preparation.ipynb #Jupyter notebook to test and prepare the ML pipeline         

## Project Descriptioin

This project analyzes disaster data from [Figure Eight](https://www.figure-eight.com/) to build a model for an API that classifies disaster messages. It includes an ETL pipeline, Machine Learning pipeline and Deployment as a Flask web app. 

## Data Description

- [messages](https://github.com/lisu1222/Disaster-Response-Pipeline/blob/master/data/disaster_messages.csv) has 26,248 rows and four columns: 'id', 'messages', 'original' and 'genre'
- [categories](https://github.com/lisu1222/Disaster-Response-Pipeline/blob/master/data/disaster_categories.csv) dataset has 26,248 rows and two columns: 'id' and 'categories'

## ETL Pipeline

The [process_data.py](https://github.com/lisu1222/Disaster-Response-Pipeline/blob/master/data/process_data.py) is a data cleaning pipleline that:
 - Loads and merges the [messages](https://github.com/lisu1222/Disaster-Response-Pipeline/blob/master/data/disaster_messages.csv) and [categories](https://github.com/lisu1222/Disaster-Response-Pipeline/blob/master/data/disaster_categories.csv) datasets
 - Cleans the data
 - Stores it in a SQLite database 

## Machine Learning

The [train_classifier.py](https://github.com/lisu1222/Disaster-Response-Pipeline/blob/master/models/train_classifier.py) is a machine learning pipeline that:
 - Loads the data from the SQLite database
 - Splits the dataset into training and test sets
 - Builds a text processing and machine learning pipeline to vectorize and apply TF-IDF to the text
 - Trains and tunes a model using GridSearchCV to find the best paprameters
 - Outputs multi-classification results on the test set and evaluate the model with f1 score, precision and recall
 - Exports the final model as a pickle file

## Flask Web Application

Some Flask templates are used to complete this part. This is a web where an emergency worker can input a new message and get classification results in several categories. The web app will also display visualizations of the data.

The front page of the Disaster Response Project: 

![alt text](https://github.com/lisu1222/Disaster-Response-Pipeline/blob/master/visul/visualization1.png)

Enter a message in the box and output the classification results:

![alt text](https://github.com/lisu1222/Disaster-Response-Pipeline/blob/master/visul/visualization2.png)


## About
This project was prepared as part of the Udacity Data Scientist nanodegree program.
