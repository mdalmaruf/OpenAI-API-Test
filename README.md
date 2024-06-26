# OpenAI API with Python ChatCompletion using Jupyter Notebook

## Introduction

This guide will walk you through setting up your Python environment to interact with the OpenAI API, specifically using the ChatCompletion feature. We will be using Jupyter Notebook for running and testing our code. Before we begin, ensure you have Python 3.9 and Anaconda installed.

## Prerequisites

### Software Requirements

1. **Python 3.9**: Ensure you have Python 3.9 installed. You can download it from the [official Python website](https://www.python.org/downloads/).
2. **Anaconda**: Anaconda helps manage Python packages and environments. Download it from the [Anaconda website](https://www.anaconda.com/products/individual).

### Integrated Development Environment (IDE)

You can use any of the following IDEs:

- VS Code
- Visual Studio
- Jupyter Notebook

## Setup Instructions

### Step 1: Create a Conda Environment

Open your terminal (or VS Code terminal) and run the following commands to set up a conda environment:

```sh
# Create a conda environment named 'venv' with Python 3.9
conda create -p venv python=3.9

# Check the list of conda environments
conda env list

# Activate the newly created environment
conda activate venv

# OpenAI API with Python ChatCompletion using Jupyter Notebook

## Introduction

This guide will walk you through setting up your Python environment to interact with the OpenAI API, specifically using the ChatCompletion feature. We will be using Jupyter Notebook for running and testing our code. Before we begin, ensure you have Python 3.9 and Anaconda installed.

## Prerequisites

### Software Requirements

1. **Python 3.9**: Ensure you have Python 3.9 installed. You can download it from the [official Python website](https://www.python.org/downloads/).
2. **Anaconda**: Anaconda helps manage Python packages and environments. Download it from the [Anaconda website](https://www.anaconda.com/products/individual).

### Integrated Development Environment (IDE)

You can use any of the following IDEs:

- VS Code
- Visual Studio
- Jupyter Notebook

## Setup Instructions

### Step 1: Create a Conda Environment

Open your terminal (or VS Code terminal) and run the following commands to set up a conda environment:


# Create a conda environment named 'venv' with Python 3.9

conda create -p venv python=3.9

# Check the list of conda environments
conda env list

# Activate the newly created environment
conda activate venv
```

### Step 2: Create a requirements.txt File

Create a `requirements.txt` file in your project directory and add the following lines to specify the dependencies:

openai
pandas
numpy
python-dotenv


### Step 3: Install Dependencies

Run the following command in your terminal to install the dependencies listed in `requirements.txt`:

```sh
pip install -r requirements.txt

Additionally, install the ipykernel package to enable Jupyter Notebook to use the new conda environment:

```sh
pip install ipykernel

### Step 4: Set Up OpenAI API Key

#### Create a `.env` File

Create a `.env` file in your project directory and add your OpenAI API key:

```sh
OPENAI_API_KEY=sk-your-api-key-here

####Load Environment Variables
Ensure your Python script loads the environment variables from the .env file using the dotenv package.

## Testing the OpenAI API

Below is the complete code to test the ChatCompletion API using the OpenAI Python client.

```python
import os
from openai import OpenAI
from dotenv import load_dotenv

# Load environment variables from the .env file
load_dotenv()

# Set your OpenAI API key
api_key = os.getenv("OPENAI_API_KEY")

# Initialize the OpenAI client with the API key
client = OpenAI(api_key=api_key)

# Function to test the ChatCompletion API
def test_chat_completion():
    response = client.chat.completions.create(
        model="gpt-3.5-turbo",
        messages=[
            {"role": "system", "content": "You are a helpful assistant."},
            {"role": "user", "content": "What is the capital of France?"}
        ],
        temperature=1,
        max_tokens=256,
        top_p=1,
        frequency_penalty=0,
        presence_penalty=0
    )
    return response.choices[0].message.content

# Get the response from the ChatCompletion API
response = test_chat_completion()

# Print the response
print("Response:", response)
