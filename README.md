# WeChat Dialogue Analyzer

This project is a front-end server that responds to AWS API Gateway, which analyzes WeChat dialogue history using a Python backend deployed in AWS Lambda and returns the analysis result.

## Getting Started

### Prerequisites

To run the front-end server locally, you need to have the following installed:

- Node.js (v12 or later)
- npm (v6 or later)

You also need to have access to the AWS Console to set up the backend.

### Installation

To install the dependencies for the front-end server, run:
```
npm install
```

### Configuration

Before running the server, you need to configure the following environment variables:

- `API_ENDPOINT`: The URL of the AWS API Gateway endpoint that you want to send requests to.
- `AWS_REGION`: The AWS region where your Lambda function is deployed.
- `AWS_ACCESS_KEY_ID`: The access key ID for an IAM user with permission to invoke your Lambda function.
- `AWS_SECRET_ACCESS_KEY`: The secret access key for the same IAM user.

You can set these environment variables using a `.env` file in the root directory of the project. An example `.env` file is included in this repository:
```
API_ENDPOINT=https://your-api-gateway-endpoint.amazonaws.com
AWS_REGION=us-west-2
AWS_ACCESS_KEY_ID=YOUR_ACCESS_KEY_ID
AWS_SECRET_ACCESS_KEY=YOUR_SECRET_ACCESS_KEY
```

### Running the Server

To run the front-end server, run:

'''
npm start
'''

This will start the server at `http://localhost:3000`.

### Deployment

To deploy the front-end server, you can use a platform like Heroku or AWS Elastic Beanstalk.

To deploy the backend, you can use the AWS Serverless Application Model (SAM) to package and deploy your Lambda function, along with any necessary resources like S3 buckets and DynamoDB tables. You can find more information on using SAM in the AWS documentation.

## Usage

To use the front-end server, you can send a POST request to the `/analyze` endpoint with a JSON payload containing the WeChat dialogue history that you want to analyze. Here's an example payload:

```
json
{
  "dialogue": [
    {
      "speaker": "A",
      "text": "Hello, how are you?"
    },
    {
      "speaker": "B",
      "text": "I'm doing well, thanks for asking. How about you?"
    },
    {
      "speaker": "A",
      "text": "I'm good too, thanks. Have you seen any good movies lately?"
    },
    {
      "speaker": "B",
      "text": "Actually, I just saw a really good one last night. It was called..."
    },
    {
      "speaker": "A",
      "text": "That sounds interesting. I'll have to check it out."
    }
  ]
}
```

The server will send the dialogue history to the AWS API Gateway endpoint that you configured, and return the analysis result as a JSON object.

### Contributing
Contributions to this project are welcome. To contribute, please submit a pull request with your changes.

### License
This project is licensed under the MIT License. See the LICENSE file for details.

