# Sample web application (Python Flask) invoking a Lambda function

This sample web application invokes a AWS Lambda function for calculating the maximum heart rate and based on this maximum heart rate calculates the target heart rate. All the backend logic is implemented in a Lambda function.

This application was designed by [Qxf2 Services](https://www.qxf2.com/?utm_source=qa-interview&utm_medium=click&utm_campaign=From%20QA%20Interview). Qxf2 provides QA for startups.

For convenience, this app will be shortly hosted at pythonanywhere.com

## Features of the Sample Lambda heart rate application

1. This app takes Name and Age as inputs

2. It invokes a Lambda function to calculate the maximum heart rate and target heart rate.

3. Displays the returned response(target heart rate range) on the browser.


## Setup

This app will be shortly hosted at pythonanywhere.com

Prerequisites:

1) Need to have a AWS account
2) Update the conf/aws_credentials.py file with the credentials
3) Create a AWS Lambda function with name 'patient_health_record' and paste the below code.

`
import json

def lambda_handler(event, context):
    #lambda handler function
    print "handler started"
    age = event['age']
    calculate_max_heart_rate(age)
    calculate_low_heart_rate_range(event,context)
    calculate_high_heart_rate_range(event,context)
    return {
        "low": round(low_heart_rate_range),
        "high":round(high_heart_rate_range)}
    
        
def calculate_max_heart_rate(age):
    # caculates maximum heart rate
    global max_heart_rate
    max_heart_rate = 220 - age
    return max_heart_rate
    
def calculate_low_heart_rate_range(event,context):
    # calculates the low heart rate range
    global low_heart_rate_range
    low_heart_rate_range = max_heart_rate * .7
    return low_heart_rate_range
    
def calculate_high_heart_rate_range(event,context):
    # calculates the high heart rate range
    global high_heart_rate_range
    high_heart_rate_range = max_heart_rate * .85
    return high_heart_rate_range    
`

Follow this setup if you want to use a local copy of this application. 

1. `pip install requirements.txt`

## How to run the Sample Lambda heart rate application

To start the application, 

1. Run `python sample_lambda_heart_rate.py` from the console.
2. Visit `localhost:6464` in your browser. 
3. Give the inputs and click on the 'Calculate THR Range!' button

## What the application does

The application calculates target heart rate for the given user. We have exactly one page with:

* two text boxes 
* one submit button
* a page title 
* three hyperlinks 
* a copyright message

