# Two Point Oh

## Overview
**Two Point Oh** is a fully serverless web application built entirely on **AWS managed services**.

The primary strength of the application is its **cloud-native architecture**: a static frontend, a serverless HTTP API, event-driven compute, and a managed NoSQL database, all integrated using AWS best practices.

The distance calculation functionality serves as a clear, deterministic workload that demonstrates how these services interact in a real application context.

---

## Application Architecture

**Frontend**
- Static single-page application hosted on **AWS Amplify**
- Implemented in HTML and JavaScript with Tailwind CSS
- Sends HTTP POST requests with JSON payloads to the backend

**Backend**
- **Amazon API Gateway** exposes a REST endpoint
- **AWS Lambda (Python)** handles request processing and distance calculation
- **Amazon DynamoDB** persists calculation results with timestamps

**Security**
- **AWS IAM** is used to enforce least-privilege access between services

**Request Flow**
```
Browser
  → API Gateway
    → Lambda (Haversine distance calculation)
      → DynamoDB (store result)
    ← API Gateway
  ← Browser (distance in km)
```

---

## AWS Services Used
- AWS Amplify – static frontend hosting
- Amazon API Gateway – REST interface
- AWS Lambda – serverless backend logic (Python)
- Amazon DynamoDB – NoSQL persistence layer
- AWS Identity and Access Management (IAM) – permissions and access control

---

## Repository Structure
```
.
├── index.html           # Frontend application (Amplify)
├── lambda_function.py   # AWS Lambda function (Python)
├── test_data.json       # Example API request payload
├── dynamopolicy.json    # IAM policy for DynamoDB access
├── architecture.md      # Service-to-component mapping
└── README.md            # Project documentation
```

---

## Frontend
**File:** `index.html`

- Collects latitude and longitude for two points
- Performs client-side validation
- Sends a POST request to the API Gateway endpoint
- Displays the calculated distance directly in the UI

The API endpoint URL is configured in the JavaScript section of the file.

---

## Backend

### AWS Lambda
**File:** `lambda_function.py`

Responsibilities:
- Parse request input (latitude and longitude)
- Convert coordinates to radians
- Calculate distance using the Haversine formula
- Persist the result and timestamp in DynamoDB
- Return the computed distance to the caller

### API Gateway
- Accepts HTTP POST requests
- Uses Lambda proxy integration
- Returns Lambda responses directly to the client

### DynamoDB
- Stores calculation results
- Each record includes the computed distance and execution timestamp

---

## IAM
**File:** `dynamopolicy.json`

Defines permissions allowing the Lambda function to:
- Write items to DynamoDB
- Read, update, and delete items as required

The policy is scoped to a single table and follows least-privilege principles.

---

## API Testing
**File:** `test_data.json`

Example request body:
```json
{
  "lat1": "47.5975024",
  "lon1": "-122.3492781",
  "lat2": "40.7579787",
  "lon2": "-73.9900326"
}
```

This payload can be used directly in the API Gateway test console or via tools such as `curl` or Postman.

---

## Notes
- The application uses fully managed AWS services
- No servers or infrastructure management is required
- The architecture is intentionally minimal and focused on clarity and correctness

---

## License
Provided as-is.

