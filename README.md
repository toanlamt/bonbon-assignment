# BonBon Assignment

## Overview
This project demonstrates how to build a customer support chatbot using LangChain and Azure OpenAI services. The chatbot is capable of answering frequently asked questions (FAQs) from a knowledge base and performing internet searches for general queries.

## Features
- **Document Indexing**: Indexes the content of `BonBon FAQ.pdf` into a local Chroma vector database using Azure OpenAI embeddings.
- **Chatbot**: A conversational chatbot built with LangChain's Conversational ReAct agent, capable of:
  - Answering FAQs from the indexed knowledge base.
  - Performing internet searches using DuckDuckGo for queries outside the scope of the knowledge base.
  - Providing answers with citations, including the source file and page number.

## Pre-requisites
- **WSL** (Windows Subsystem for Linux)
- **Miniconda3**

## Setup Environment
1. Create a Conda environment:
   ```bash
   conda create -n langchain python=3.11
   ```
2. Set the `langchain` environment as the running environment in Visual Studio Code.

## Installation
Install the required Python packages:
```bash
pip install python-dotenv langchain chromadb openai tiktoken pypdf langchain_openai langchain-chroma duckduckgo-search
```

## Usage
### Document Indexing
The content of `BonBon FAQ.pdf` is indexed into a local Chroma vector database using the following code:

### Chatbot
The chatbot is built using LangChain's Conversational ReAct agent. It supports:
- **Knowledge Base Search**: Answers FAQs from `BonBon FAQ.pdf`.
- **Internet Search**: Uses DuckDuckGo for general queries.

Run the chatbot using:
```python
def chat():
    print("💬 Welcome to BonBon Support Chatbot! (type 'exit' to quit)\n")
    while True:
        question = input("User: ")
        if question.lower() == "exit":
            break
        response = agent.run(question)
        print(f"\n🤖 Bot: {response}\n")

chat()
```

### Example Interaction
- **User**: "How to connect to Any Corp’s Corporate Wi-Fi network?"
- **Bot**: "To connect to Any Corp’s Corporate Wi-Fi network, you need to look for the network in your device's available Wi-Fi networks, select it, enter the password or security key when prompted, and verify the connection. If you're having trouble, you can refer to the email you received when you first joined Any Corp, ask a colleague, or contact the IT Helpdesk for assistance.  
(Source: BonBon FAQ.pdf (page 5))"

## Optional Assignment
Explore additional features:
- Index `BonBon FAQ.pdf` to Azure Cognitive Search.
- Implement a new assistant with similar behavior.
- Explore RBACs and admin portal features.

## Environment Variables
Set the following variables in your `.env` file:
```env
OPENAI_API_TYPE=azure
OPENAI_API_KEY=<your-api-key>
AZURE_OPENAI_API_VERSION=<api-version>
AZURE_OPENAI_EMBEDDING_DEPLOYMENT=<embedding-deployment-name>
AZURE_OPENAI_CHAT_DEPLOYMENT=<chat-deployment-name>
```

## License
This project is licensed under the MIT License.