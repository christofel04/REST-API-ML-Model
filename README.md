# REST-API-ML-Model
Deploy simple machine learning model as Rest API in Python.
The case the we used is [Sentiment Analysis on Movie Reviews](https://www.kaggle.com/c/sentiment-analysis-on-movie-reviews/overview) in Kaggle competition  to predict whether sentimen of a comment in Rotten Tomatoes review is good or not.
Dataset can be found [here](https://www.kaggle.com/c/sentiment-analysis-on-movie-reviews/data).

# Use
We can test the API using request function in `Jupyter Notebook`.
  
```
url = 'http://127.0.0.1:5000/'
params ={'query': 'that movie was boring'}
response = requests.get(url, params)
response.json()
Output: {'confidence': 0.128, 'prediction': 'Negative'}
```
Or using HTTPie in terminal.

```
$ http http://127.0.0.1:5000/ query=='that movie was boring'
HTTP/1.0 200 OK
Content-Length: 58
Content-Type: application/json
Date: Fri, 31 Aug 2018 18:49:25 GMT
Server: Werkzeug/0.14.1 Python/3.6.3
{
    "confidence": 0.128,
    "prediction": "Negative"
}
```
# File Structure
User use this file structure for API.

    .
    ├── README.md
		├── app.py  # Flask REST API script
		├── build_model.py  # script to build and pickle the classifier
		├── model.py  # script for the classifier class object
		├── util.py  # helper functions
		├── requirements.txt
		└── lib/
    		├── data/  # data from Kaggle
    		│   ├── sampleSubmission.csv
    		│   ├── test.tsv
    		│   └── train.tsv
    		└── models/  # pickled models for import into API script
        		├── SentimentClassifier.pkl
        		└── TFIDFVectorizer.pkl
 
