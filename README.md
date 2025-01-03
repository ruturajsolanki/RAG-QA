# RAG-QA System

A Question-Answering system built using Retrieval-Augmented Generation (RAG) with Cohere embeddings and Pinecone vector database.

## Overview

This project implements a document-based question-answering system that uses RAG architecture to provide accurate answers based on the content of uploaded PDF documents. It leverages Cohere's embedding model for text vectorization and Pinecone for efficient vector storage and retrieval.

## Prerequisites

- Python 3.x
- Cohere API key
- Pinecone API key
- AWS account (for Pinecone serverless)

## Required Packages

```bash
pip install cohere pinecone-client langchain
```

## Environment Variables

The following environment variables need to be set:

- `COHERE_API_KEY`: Your Cohere API key
- `PINECONE_API_KEY`: Your Pinecone API key
- `PINECONE_ENV`: Your Pinecone environment (e.g., 'us-east-1')

## Project Structure

The project consists of several main components:

1. **Document Processing**
   - PDF document loading using PyPDFLoader
   - Text splitting using RecursiveCharacterTextSplitter
   - Configurable chunk size and overlap

2. **Vector Storage**
   - Pinecone index creation and management
   - Document vectorization using Cohere embeddings
   - Vector storage and retrieval

3. **Query Processing**
   - Question processing
   - Relevant document retrieval
   - Answer formatting

## Usage

1. **Initialize the Environment**
   ```python
   import os
   import cohere
   from pinecone import Pinecone, ServerlessSpec
   # Set your environment variables
   ```

2. **Load and Process Documents**
   ```python
   data = read_data_from_doc('your_document.pdf')
   splits = make_chunks(data)
   ```

3. **Create and Setup Vector Store**
   ```python
   embeddings = CohereEmbeddings(model="embed-english-v3.0")
   vectorstore = index_documents_in_pinecone(splits, embeddings)
   ```

4. **Query the System**
   ```python
   answer = query_pinecone("Your question here", vectorstore)
   ```

## Configuration Options

- **Chunk Size**: Default is 1000 characters
- **Chunk Overlap**: Default is 200 characters
- **Embedding Model**: Using Cohere's "embed-english-v3.0"
- **Vector Dimension**: 1024
- **Similarity Metric**: Cosine similarity

## Key Functions

- `read_data_from_doc(file_path)`: Loads PDF documents
- `make_chunks(docs, chunk_len, chunk_overlap)`: Splits documents into manageable chunks
- `index_documents_in_pinecone(chunks, embeddings)`: Indexes document chunks in Pinecone
- `query_pinecone(prompt, vectorstore)`: Retrieves relevant information for a given query

## Important Notes

1. Always protect your API keys and never commit them directly in the code
2. Ensure your Pinecone index specifications match your subscription tier
3. Consider implementing rate limiting for API calls
4. Monitor your API usage to manage costs

## Contributing

Feel free to contribute to this project by submitting issues or pull requests.

## Contact  

For inquiries or collaboration opportunities, feel free to reach out:  

- **Name**: Ruturaj Solanki  
- **Email**: [Email](mailto:ruturajsolanki43@gmail.com)  
- **LinkedIn**: [Linkedin](https://www.linkedin.com/in/ruturajsolanki)  
- **GitHub**: [Github](https://github.com/ruturajsolanki) 
