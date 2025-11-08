# Build a Complete Medical Chatbot with LLMs, LangChain, Pinecone, Flask, and AWS

This project is an AI-powered medical chatbot that uses Large Language Models (LLMs) to understand and respond to medical-related queries. It integrates LangChain for prompt management, Pinecone for vector storage, and Flask for the web interface. The chatbot is deployed on AWS using Docker and GitHub Actions for CI/CD.

## Features

* Conversational chatbot for medical queries
* LLMs integrated via OpenAI API
* Pinecone for storing and retrieving embeddings
* Flask-based web interface
* Dockerized for easy deployment
* Automated AWS deployment (ECR + EC2)

## Tech Stack

* Python
* LangChain
* OpenAI GPT
* Pinecone
* Flask
* AWS (EC2, ECR)
* GitHub Actions

## Setup Instructions

### Step 1: Clone the repository

```bash
git clone https://github.com/entbappy/Build-a-Complete-Medical-Chatbot-with-LLMs-LangChain-Pinecone-Flask-AWS.git
cd Build-a-Complete-Medical-Chatbot-with-LLMs-LangChain-Pinecone-Flask-AWS
```

### Step 2: Create and activate a conda environment

```bash
conda create -n medibot python=3.10 -y
conda activate medibot
```

### Step 3: Install dependencies

```bash
pip install -r requirements.txt
```

### Step 4: Add environment variables

Create a `.env` file in the root directory and add the following:

```
PINECONE_API_KEY = "your_pinecone_api_key"
OPENAI_API_KEY = "your_openai_api_key"
```

### Step 5: Store embeddings in Pinecone

```bash
python store_index.py
```

### Step 6: Run the Flask application

```bash
python app.py
```

Open your browser and go to `http://localhost:5000` to interact with the chatbot.

## Deployment Guide (AWS)

1. Log in to AWS console.

2. Create an IAM user with the following permissions:

   * AmazonEC2FullAccess
   * AmazonEC2ContainerRegistryFullAccess

3. Create an ECR repository to store your Docker image. Example:

   ```
   315865595366.dkr.ecr.us-east-1.amazonaws.com/medicalbot
   ```

4. Create and launch an EC2 Ubuntu instance.

5. Install Docker on EC2:

```bash
sudo apt-get update -y
sudo apt-get upgrade -y
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
sudo usermod -aG docker ubuntu
newgrp docker
```

6. Configure EC2 as a self-hosted GitHub Actions runner:
   Go to
   GitHub repository → Settings → Actions → Runners → New self-hosted runner
   Follow the provided commands for your OS.

7. Add GitHub Secrets:

```
AWS_ACCESS_KEY_ID  
AWS_SECRET_ACCESS_KEY  
AWS_DEFAULT_REGION  
ECR_REPO  
PINECONE_API_KEY  
OPENAI_API_KEY  
```

8. Push your Docker image to ECR, pull it on EC2, and run the container.

## Output

A fully functional AI-powered chatbot capable of answering medical queries in real time, deployed securely on AWS.

