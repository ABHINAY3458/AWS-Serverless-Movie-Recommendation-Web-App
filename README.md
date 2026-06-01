Serverless Movie Recommendation Web App Deployment on AWS

---

# Project Objective

Design and deploy a serverless web application using AWS cloud services. It will help me gain practical knowledge of cloud computing, serverless architecture, IAM security, monitoring, storage, networking, and Infrastructure as Code (IaC).

---

# Technology Stack

* AWS Free Tier
* Amazon S3
* Amazon CloudFront
* AWS Lambda
* API Gateway
* DynamoDB
* IAM
* CloudWatch
* Terraform
* HTML/CSS/JavaScript

---

# 3-Tier Architecture

## Frontend Layer

* Static website hosted on Amazon S3
* Delivered globally using CloudFront CDN

## API Layer

* REST API created using API Gateway
* Backend processing handled by AWS Lambda

## Database Layer

* DynamoDB used for storing movie information and users

---

# Architecture Flow

User → CloudFront CDN → S3 Static Website → API Gateway → Lambda Function → DynamoDB

---

# AWS Services Used

| Service         | Purpose                        |
| --------------- | ------------------------------ |
| S3              | Static website hosting         |
| CloudFront      | CDN and fast content delivery  |
| Lambda          | Serverless backend compute     |
| API Gateway     | REST API                       |
| DynamoDB        | NoSQL database                 |
| IAM             | Security and access management |
| CloudWatch      | Monitoring and logs            |
| Secrets Manager | Store secrets securely         |
| Terraform       | Infrastructure as Code         |

---

# Step 1 – Create Frontend

## Create index.html

```html
<!DOCTYPE html>
<html>
<head>
    <title>Movie Recommendation App</title>
</head>
<body>
    <h1>Welcome to Movie Recommendation App</h1>
    <button onclick="getMovies()">Load Movies</button>

    <ul id="movies"></ul>

    <script>
        async function getMovies() {
            const response = await fetch('YOUR_API_GATEWAY_URL');
            const data = await response.json();

            let output = '';

            data.forEach(movie => {
                output += `<li>${movie.name}</li>`;
            });

            document.getElementById('movies').innerHTML = output;
        }
    </script>
</body>
</html>
```

---

# Step 2 – Upload Website to S3

## Steps

1. Open AWS S3
2. Create bucket
3. Enable static website hosting
4. Upload index.html
5. Make bucket objects public

---

# Step 3 – Create DynamoDB Tables

## Table 1: Movies

| Attribute | Type   |
| --------- | ------ |
| movieId   | String |
| name      | String |
| category  | String |

## Table 2: Users

| Attribute | Type   |
| --------- | ------ |
| userId    | String |
| username  | String |

---

# Step 4 – Create Lambda Function

## Runtime

Python 3.x

## Lambda Code

```python
import json


def lambda_handler(event, context):
    movies = [
        {"name": "KGF"},
        {"name": "Pushpa"},
        {"name": "Bahubali"}
    ]

    return {
        'statusCode': 200,
        'headers': {
            'Access-Control-Allow-Origin': '*'
        },
        'body': json.dumps(movies)
    }
```

---

# Step 5 – Create API Gateway

## Steps

1. Open API Gateway
2. Create REST API
3. Create GET method
4. Connect Lambda function
5. Enable CORS
6. Deploy API

---

# Step 6 – Connect Frontend with API

Replace:

```javascript
YOUR_API_GATEWAY_URL
```

with your deployed API endpoint.

---

# Step 7 – Configure IAM

## IAM Best Practices

* Use least privilege access
* Avoid root account usage
* Enable MFA
* Use IAM roles for Lambda

## IAM Roles

### Lambda Role

Permissions:

* CloudWatch Logs
* DynamoDB Access

### S3 Role

Permissions:

* Read static website files

---

# Step 8 – Configure CloudWatch Monitoring

## Enable:

* Lambda logs
* API Gateway metrics
* Error tracking

## Dashboard Metrics

* Request count
* Error rate
* Latency

---

# Step 9 – Configure Cost Alert

## Budget Setup

1. Open AWS Billing Dashboard
2. Create Budget
3. Set threshold to $5
4. Add email notification

---

# Step 10 – Terraform Infrastructure as Code

## main.tf

```terraform
provider "aws" {
  region = "ap-south-1"
}

resource "aws_s3_bucket" "movie_bucket" {
  bucket = "movie-app-bucket-demo"
}
```

---


---

