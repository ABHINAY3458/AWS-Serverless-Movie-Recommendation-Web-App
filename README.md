# Serverless Movie Recommendation App

## Project Overview

This project demonstrates a serverless web application built on AWS using S3, API Gateway, Lambda, and DynamoDB.

## Technologies Used

* AWS S3
* AWS API Gateway
* AWS Lambda
* AWS DynamoDB
* CloudWatch
* HTML, CSS, JavaScript

## Architecture

User → S3 Website → API Gateway → Lambda → DynamoDB

## Features

* Static website hosting using S3
* Serverless API using Lambda
* Data storage using DynamoDB
* Movie and User management
* Cloud monitoring with CloudWatch

## Setup Instructions

Step 1 – Create S3 Bucket

Open AWS Console → Search S3 → Click Amazon S3

Click Create Bucket

Enter:

Bucket Name
Region

Uncheck:

Block all public access 

Enable:

Versioning 
Click Create Bucket








Step 2 – Upload Website to S3




Steps

    1. Open AWS S3
    2. Create bucket
    3. Enable static website hosting
    4. Upload index.html
    5. Make bucket objects public
Step 3 – Create DynamoDB Tables



Table 1: Movies

Attribute	Type
movieId	String
name	String
category	String

Table 2: Users

Attribute	Type
userId	String
username	String









Step 4 – Create Lambda Function









Step 5 – Create API Gateway




Steps:

Open API Gateway
Create REST API
Create GET method
Connect Lambda function
Enable CORS
Deploy API





Step 6 – Connect Frontend with API

    1) Replace
    2) YOUR_API_GATEWAY_URL
    3) with your deployed API endpoint in HTML file


Step 7 – Configure IAM

IAM Best Practices

    • Use least privilege access
    • Avoid root account usage
    • Enable MFA
    • Use IAM roles for Lambda

IAM Roles









Lambda Role

Permissions:

    • CloudWatch Logs
    • DynamoDB Access
    
S3 Role

Permissions:

    • Read static website files

Step 8 – Configure CloudWatch Monitoring

Enable:

    • Lambda logs
    • API Gateway metrics
    • Error tracking
    
Dashboard Metrics

    • Request count
    • Error rate
    • Latency

Step 9 – Configure Cost Alert


Budget Setup

    1. Open AWS Billing Dashboard
    2. Create Budget
    3. Set threshold to $5
    4. Add email notification



---


---

