# House Price Prediction API

A simple REST API built with **FastAPI** that predicts house prices using a pre-trained machine learning model. The API accepts house features (size and number of bedrooms) and returns predicted prices for either a single house or multiple houses in a batch.

---

## Features

* Predict the price of a single house
* Predict prices for multiple houses in one request
* Fast and lightweight REST API built with FastAPI
* Uses a pre-trained machine learning model stored as a Pickle (`.pkl`) file

---

## Technologies Used

* Python 3
* FastAPI
* NumPy
* Pydantic
* Pickle
* Uvicorn

---

## Project Structure

```
House-Price-Prediction-API/
│
├── main.py                  # FastAPI application
├── house_price_model.pkl    # Trained machine learning model
├── requirements.txt
└── README.md
```

---

## Installation

### 1. Clone the repository

```bash
git clone https://github.com/yourusername/house-price-prediction-api.git
cd house-price-prediction-api
```

### 2. Create a virtual environment (optional but recommended)

Windows

```bash
python -m venv venv
venv\Scripts\activate
```

Linux / macOS

```bash
python3 -m venv venv
source venv/bin/activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

---

## Running the API

Start the FastAPI server with Uvicorn:

```bash
uvicorn main:app --reload
```

The API will be available at:

```
http://127.0.0.1:8000
```

---

## Interactive API Documentation

FastAPI automatically generates interactive documentation.

Swagger UI:

```
http://127.0.0.1:8000/docs
```

ReDoc:

```
http://127.0.0.1:8000/redoc
```

---

## API Endpoints

### Home

**GET /**

Returns a welcome message.

Response

```json
{
    "message": "Welcome to the House Prediction API"
}
```

---

### Predict a Single House

**POST /predict**

Predicts the price of a single house.

Request Body

```json
{
    "size_sqft": 1800,
    "bedrooms": 3
}
```

Example Response

```json
{
    "predicted_price": 342500.18
}
```

---

### Predict Multiple Houses

**POST /predict_batch**

Predicts prices for multiple houses in a single request.

Request Body

```json
{
    "houses": [
        {
            "size_sqft": 1800,
            "bedrooms": 3
        },
        {
            "size_sqft": 2400,
            "bedrooms": 4
        }
    ]
}
```

Example Response

```json
{
    "predicted_prices": [
        342500.18,
        468730.52
    ]
}
```

---

## Input Parameters

| Parameter | Type    | Description                      |
| --------- | ------- | -------------------------------- |
| size_sqft | float   | Size of the house in square feet |
| bedrooms  | integer | Number of bedrooms               |

---

## Requirements

Example `requirements.txt`

```text
fastapi
uvicorn
numpy
pydantic
scikit-learn
```

---

## Machine Learning Model

The API loads a pre-trained machine learning model from:

```text
house_price_model.pkl
```

The model is loaded when the application starts and is used to generate predictions for incoming requests.
