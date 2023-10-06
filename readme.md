# PDF Layout Analysis API

## Overview

The PDF Layout Analysis API is a service that analyzes PDF documents and provides layout bounding box coordinates in a specific format. This document provides instructions on how to use the API, the input parameters, and the format of the output.

## How to Use

To use this API, you need to make a POST request to the API endpoint with the path of the PDF file you want to analyze. You can use the Python `requests` library for this purpose.

### Example Python Code

```python
import requests

# Define the URL of the FastAPI server
fastapi_url = "http://127.0.0.1:8008/predict/"

# Define the input data as a dictionary
input_data = {"text": "path_to_your_pdf_file.pdf"}  # Replace 'path_to_your_pdf_file.pdf' with the actual path to your PDF file

# Send a POST request to the FastAPI server with JSON data
response = requests.post(fastapi_url, json=input_data)

# Handle the response data (explained in the next section)

{
    "0": {
        "pred_boxes": {
            "tensor": {
                // Bounding box coordinates for page 0
            }
        },
        "scores": {
            // Probability scores for page 0
        },
        "pred_classes": {
            // Prediction class indexes for page 0
        }
    },
    "1": {
        "pred_boxes": {
            "tensor": {
                // Bounding box coordinates for page 1
            }
        },
        "scores": {
            // Probability scores for page 1
        },
        "pred_classes": {
            // Prediction class indexes for page 1
        }
    },
    // More pages if applicable
}

# Extract bounding box coordinates for page 0
page_0_boxes = response.json().get("0", {}).get("pred_boxes", {}).get("tensor", {})

# You can similarly extract scores and prediction class indexes

