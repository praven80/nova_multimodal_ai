# Amazon Nova Multimodal Chatbot

A sophisticated chatbot application leveraging Amazon Bedrock's Nova models to handle multiple types of media interactions including text, image, and video processing.

You can view a short demo video in the "Demo" folder.

## Features

- **Multiple Input Types**:
  - Text Input
  - Image Upload (PNG)
  - Video Upload (MP4)

- **Multiple Output Types**:
  - Text Generation
  - Image Generation
  - Video Generation

- **Supported Conversions**:
  - Text → Text
  - Text → Image
  - Text → Video
  - Image → Text
  - Image → Image
  - Image → Video
  - Video → Text

## Architecture

- Built with Streamlit
- Powered by Amazon Bedrock Nova models
- Deployed on AWS ECS Fargate
- Uses S3 for storage
- Load balanced with Application Load Balancer

## Prerequisites

- AWS Account
- AWS CDK installed
- Docker
- Python 3.9+
- Required AWS permissions for:
  - Amazon Bedrock
  - Amazon ECS
  - Amazon S3
  - AWS IAM
  - Amazon EC2

## Installation

1. Clone the repository:
```bash
git clone <repository-url>
cd nova-multimodal-chatbot
```

2. Install dependencies:
```bash
pip install -r requirements.txt
```

3. Set up AWS credentials:
```bash
aws configure
```

## Deployment

### Local Development

1. Run the Streamlit application locally:
```bash
streamlit run app.py
```

### AWS Deployment

1. Install AWS CDK (if not already installed):
```bash
npm install -g aws-cdk
```

2. Bootstrap CDK (first time only):
```bash
cdk bootstrap
```

3. Deploy the stack:
```bash
cdk deploy
```

## Environment Variables

- `S3_BUCKET_NAME`: Name of the S3 bucket for storing media files

## Docker

Build the container:
```bash
docker build -t nova-multimodal-chatbot .
```

Run the container:
```bash
docker run -p 8501:8501 nova-multimodal-chatbot
```

## Usage

1. Access the application through your web browser
2. Select input type (Text/Image/Video)
3. Select output type (Text/Image/Video)
4. Enter prompt or upload file
5. View generated response

## Infrastructure

The application is deployed using AWS CDK with the following components:

- VPC with public and private subnets
- ECS Fargate cluster
- Application Load Balancer
- S3 bucket for media storage
- IAM roles and security groups
- CloudWatch logs

## Security

- Private subnets for container deployment
- Security groups for network access control
- IAM roles with least privilege
- S3 bucket with appropriate permissions

## Limitations

- Video to Image/Video conversions not supported
- Maximum file size limitations
- Processing time varies by media type