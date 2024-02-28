
# Titanic Survival Prediction Web App

This project implements a web application using Flask for predicting survival on the Titanic dataset. It includes a logistic regression model trained on the dataset to make predictions.

## Overview

The Titanic dataset contains information about passengers aboard the Titanic, including features like age, gender, passenger class, fare, etc. The goal of this project is to predict whether a passenger survived or not based on these features.

The project includes the following components:

1. **Model Training**: A logistic regression model is trained on the Titanic dataset to predict survival outcomes.

2. **Flask Web Application**: A Flask web application is created to deploy the trained model. It provides an API endpoint `/predict` where users can send POST requests with passenger information to get survival predictions.

3. **Ngrok Integration**: Ngrok is used to expose the Flask web application to the internet, allowing users to access the prediction API remotely.

## Setup

To run the project locally, follow these steps:

1. Clone the repository:

   ```
   git clone https://github.com/yourusername/titanic-survival-prediction.git
   ```

2. Install dependencies:

   ```
   pip install -r requirements.txt
   ```

3. Run the Flask app:

   ```
   python app.py
   ```

4. Expose the Flask app using Ngrok:

   ```
   ngrok http 5000
   ```

   Note: Make sure to replace `5000` with the port number on which your Flask app is running.

## Usage

Once the Flask app is running and exposed through Ngrok, you can send POST requests to the `/predict` endpoint with JSON data containing passenger information. Here's an example using Python requests:

```python
import requests
import json

# Define passenger information
data = {
    "Pclass": 3,
    "Sex": 0,  # 0 for male, 1 for female
    "Age": 25,
    "SibSp": 0,
    "Parch": 0,
    "Fare": 7.25,
    "Embarked": 0  # 0 for S, 1 for C, 2 for Q
}

# Send POST request to prediction API
response = requests.post('https://your-ngrok-url.ngrok.io/predict', json=data)

# Get prediction from response
prediction = response.json()['prediction']
print("Survived" if prediction == 1 else "Did not survive")
```


## Credits

This project was developed by mobisa frankline. It is based on the Titanic dataset from Kaggle.
