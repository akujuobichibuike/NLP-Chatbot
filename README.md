# NLP-Chatbot

# Innovative Chatbot Project

## Overview

Our innovative chatbot project is designed to provide efficient and confidential assistance to users. This project leverages advanced natural language processing (NLP) techniques and AI-powered models to answer questions and engage in conversations with users.

## Components and Libraries

### 1. Tokenization and Text Chunking

We utilized the GPT-2 Tokenizer to break down text into smaller, manageable chunks. The `count_tokens` function counts the tokens in a given text, and the `split_text_into_chunks` function segments long texts into smaller sections for processing.

### 2. Language Models and Embeddings

Our project integrates OpenAI's language models and embeddings to understand and generate human-like responses. The OpenAI API key (`api_key`) allows us to access these powerful language capabilities securely.

### 3. Vector Storage

To efficiently manage and retrieve text chunks, we employed the FAISS vector store, ensuring rapid access to relevant information.

### 4. Question-Answering Chain

Our system includes a question-answering (QA) chain, which utilizes OpenAI's language models to provide accurate answers to user queries.

### 5. Conversational Interface

The project features a user-friendly conversational interface that enables users to interact with the chatbot.

## Code Snippet

```python
# Import necessary libraries and modules
import os
import pandas as pd
import matplotlib.pyplot as plt
from transformers import GPT2TokenizerFast
from langchain.document_loaders import PyPDFLoader
# ... (other imports)

# Initialize components and libraries
# ... (initialization of tokenizer, embeddings, text splitter, etc.)

# Function to process user input and provide responses
def chat_with_bot():
    print("Welcome to our chatbot! Type 'exit' to stop.")
    while True:
        query = input("You: ")

        if query.lower() == 'exit':
            print("Thank you for using our chatbot!")
            break

        # Initialize an empty chat history for each question
        chat_history = []

        # Split the user's query into chunks if it's too long
        query_chunks = split_text_into_chunks(query, max_chunk_length=1024)

        for chunk in query_chunks:
            result = qa({"question": chunk, "chat_history": chat_history})
            print(f'Chatbot: {result["answer"]}')

# Call the chat_with_bot function to start the conversation
chat_with_bot()
