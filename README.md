Intro to RAG: Berlin Knowledge Assistant

This project demonstrates a Retrieval-Augmented Generation (RAG) system using FAISS and HuggingFace embeddings/models. It is designed to answer questions about Berlin using a small curated dataset of 61 facts.

The system combines:

Vector-based retrieval of relevant documents.

Generative language models to produce natural-language answers based on retrieved content.

🧩 Features

Document Retrieval: Uses FAISS to find relevant facts from the dataset.

Embeddings: Leverages transformer-based embeddings from HuggingFace.

Generative Responses: Uses a chat-based LLM to generate answers grounded in retrieved facts.

Interactive Queries: Users can input questions and receive concise, factual responses.

📂 Project Structure
RAG-Berlin/
│
├── berlin_facts.py           # Sample dataset and RAG pipeline
├── README.md                 # Project documentation
├── requirements.txt          # Python dependencies
└── data/                     # Optional: additional documents for expansion

🔧 Setup

Install the required libraries:

pip install langchain-huggingface sentence-transformers langchain_community faiss-cpu -q


Set your HuggingFace API token (example for Colab):

from google.colab import userdata
import os

hf_key = userdata.get('HF_TOKEN')
os.environ['HUGGINGFACEHUB_API_TOKEN'] = hf_key

⚙️ Usage

Prepare documents: The dataset contains 61 facts about Berlin. Each fact is wrapped as a Document.

Create embeddings: Use HuggingFaceEmbeddings to encode the documents.

Build FAISS index: Store document embeddings in FAISS for fast similarity search.

Retrieve relevant documents: Use similarity_search to fetch top-k documents based on a user query.

Generate answers: Pass retrieved documents to a HuggingFace chat model to produce a natural-language answer.

Example:

query = "Where is the German Parliament?"
rag(query)

💡 Example Queries

"What is Berlin known for?"

"Where is the German Parliament?"

"Who invented the Pastel de Nata?"

The system will retrieve relevant facts and generate responses only using the retrieved content.

🛠️ Components

FAISS: Efficient similarity search for vector embeddings.

HuggingFace Embeddings: Converts documents into vector space for retrieval.

HuggingFace LLM: Chat model (microsoft/Phi-3.5-mini-instruct) for generation.

RAG Pipeline: Combines retrieval and generative modeling for factual, context-aware answers.

📈 Potential Extensions

Add more documents to cover broader topics.

Replace Phi-3.5-mini-instruct with larger LLMs for richer responses.

Integrate with LangChain for a full multi-step workflow.

Support multi-language queries with language-specific embeddings.

⚡ Notes

This is a proof-of-concept RAG system for educational purposes.

All answers are grounded in the retrieved dataset; the model will explicitly state if information is unavailable.

Ideal for QA systems, chatbots, and domain-specific knowledge assistants.
