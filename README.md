# AREP- Autonomous Agents with LangChain and RAG

This repository contains a Jupyter notebook that demonstrates the implementation of an autonomous agent system using LangChain and Retrieval-Augmented Generation (RAG). The system is designed to perform task decomposition, retrieve relevant information, and generate responses based on the retrieved context. The notebook leverages various libraries, including langchain, pinecone, and langgraph, to build a robust question-answering system.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/11QOw-motG5PpESJ4bpv-swECRqDZ7AEm)


## Introduction
The notebook demonstrates how to build an autonomous agent system that can decompose complex tasks, retrieve relevant information from a vector store, and generate coherent responses. The system is built using LangChain, which provides a framework for chaining together different components of a language model, and Pinecone, a vector database used for efficient retrieval of relevant documents.

The system is designed to handle tasks such as:

- Task Decomposition: Breaking down complex tasks into smaller, manageable steps.

- Information Retrieval: Fetching relevant documents from a vector store based on a query.

- Response Generation: Generating answers based on the retrieved context

## Installation

To install the required dependencies, run:

```bash
%pip install --quiet --upgrade langchain-text-splitters langchain-community langgraph
pip install -qU "langchain[openai]"
pip install -qU langchain-openai
pip install -qU langchain-pinecone
pip install -qU langchain-pinecone pinecone-notebooks
```
Additionally, you will need to set up your OpenAI and Pinecone API keys:
```python
import getpass
import os

if not os.environ.get("OPENAI_API_KEY"):
  os.environ["OPENAI_API_KEY"] = getpass.getpass("Enter API key for OpenAI: ")

if not os.environ.get("PINECONE_API_KEY"):
    os.environ["PINECONE_API_KEY"] = getpass.getpass("Enter your Pinecone API key: ")
```

## Getting Started
1. Open the notebook in Google Colab.
2. Install dependencies using the command above.
3. Follow the notebook's instructions to run the LangChain LLM workflows.

## Usage
The notebook is divided into several sections, each focusing on a different aspect of the autonomous agent system:

1. Setup: Install dependencies and configure API keys.

2. Vector Store Initialization: Set up Pinecone as the vector store for document retrieval.

3. Document Loading and Chunking: Load and split documents into manageable chunks.

4. Graph Construction: Build a state graph using langgraph to define the workflow of the agent.

5. Task Decomposition: Implement task decomposition using LangChain.

6. Information Retrieval: Retrieve relevant documents from the vector store.

7. Response Generation: Generate responses based on the retrieved context.

8. Interactive Querying: Run the agent interactively to answer questions.

## Key Components

1. LangChain
LangChain is used to chain together different components of the language model, including task decomposition, retrieval, and generation. It provides a flexible framework for building complex workflows.

2. Pinecone
Pinecone is used as a vector store to efficiently retrieve relevant documents based on a query. The documents are embedded using OpenAI's embeddings and stored in Pinecone for quick access.

3. LangGraph
LangGraph is used to define the state graph of the agent. The graph consists of nodes that represent different steps in the workflow, such as task decomposition, retrieval, and generation.

4. Task Decomposition
Task decomposition is implemented using LangChain's Chain of Thought (CoT) technique, which breaks down complex tasks into smaller, manageable steps. This allows the agent to handle more complex queries by dividing them into simpler sub-tasks.

5. Retrieval-Augmented Generation (RAG)
RAG is used to enhance the agent's response generation by retrieving relevant documents from the vector store. The retrieved documents provide additional context, allowing the agent to generate more accurate and informative responses.

## Workflow

The workflow of the autonomous agent system is as follows:

1. Task Decomposition: The agent decomposes the input query into smaller tasks.

2. Information Retrieval: The agent retrieves relevant documents from the vector store based on the decomposed tasks.

3. Response Generation: The agent generates a response based on the retrieved documents and the original query.

4. Interactive Querying: The agent can be run interactively to answer user queries.


## Examples
Example 1: Task Decomposition
```python
input_message = "What is Task Decomposition?"

for step in graph.stream(
    {"messages": [{"role": "user", "content": input_message}]},
    stream_mode="values",
):
    step["messages"][-1].pretty_print()

```

Example 2: Interactive Querying
```python
input_message = "Can you look up some common ways of doing it?"

for step in graph.stream(
    {"messages": [{"role": "user", "content": input_message}]},
    stream_mode="values",
    config=config,
):
    step["messages"][-1].pretty_print()
```



## Dependencies

- langchain
- openai
- requests
- SQLAlchemy
- PyYAML
- typing-extensions
- httpx
- orjson
