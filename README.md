![DobbyGPT Demo](assets/demo.png)

# DobbyGPT – Harry Potter AI Chatbot

LLM | RAG | Vector Search | FAISS | Python

DobbyGPT is a Harry Potter themed AI chatbot designed to answer questions about the wizarding world using a Retrieval-Augmented Generation (RAG) pipeline.

The assistant combines a language model with a local knowledge base so that answers are generated using relevant context instead of relying only on the base model.

The system also adds small interactive elements inspired by the Harry Potter universe, such as house-based responses and wizarding world updates.

---

## Features

* Harry Potter themed conversational AI
* Retrieval-Augmented Generation (RAG) pipeline
* Vector similarity search using FAISS
* SentenceTransformer embeddings for semantic retrieval
* LLM-powered responses with Qwen-Plus
* Prompt injection protection and domain filtering
* Conversation logging system

### Wizarding World Features

* **House-based interaction**
  Users can select a Hogwarts house (Gryffindor, Slytherin, Ravenclaw, or Hufflepuff).
  The assistant adapts its tone and responses based on the selected house.

* **Wizarding News Updates**
  The chatbot can generate short newspaper-style updates inspired by the wizarding world, similar to the *Daily Prophet*.

* **Lore-aware responses**
  Answers are grounded in a Harry Potter knowledge base stored locally in the project.

---

## System Architecture

### Data & Embedding Layer

The knowledge base consists of Harry Potter related documents stored locally as text files.

Documents are converted into vector embeddings using the **SentenceTransformers `all-MiniLM-L6-v2` model**, allowing the system to search for semantically relevant information.

---

### Retrieval Layer

User queries are embedded and compared with the document vectors using **FAISS**.

The system retrieves the **Top-K most relevant passages** using vector similarity.

Additional filtering is applied:

* Euclidean distance metric
* Threshold filtering to prevent off-topic answers

---

### Security Layer

Basic prompt injection protection is implemented before sending queries to the language model.

Safeguards include:

* Regex-based filtering for suspicious instructions
* Structural checks for malicious tokens
* Semantic boundary filtering using FAISS distance thresholds

If a query falls outside the knowledge scope, the assistant politely declines.

---

### LLM Inference Layer

The retrieved context is passed to the language model to generate the final answer.

Model configuration:

* **LLM:** Qwen-Plus
* **API:** OpenAI-compatible endpoint
* **Temperature:** 0.4 for consistent responses

The model acts purely as a response generator and does not directly access the knowledge base.

---

### Logging & Interface

All conversations are stored in a CSV file for later inspection.

Stored information includes:

* Timestamp
* Dialogue ID
* User question
* Assistant response

The interface is built with **CustomTkinter**, providing a simple desktop chat interface with persistent sessions.

---

## Tech Stack

* Python 3
* SentenceTransformers (all-MiniLM-L6-v2)
* FAISS vector search
* Qwen-Plus LLM API
* CustomTkinter
* NumPy
* CSV-based logging

---

## Running the Project

Clone the repository:

```bash
git clone https://github.com/aleynadedee/DobbyGPT-Project.git
cd DobbyGPT-Project
```

Install dependencies:

```bash
pip install -r requirements.txt
```

Create a `.env` file and add your API key:

```
QWEN_API_KEY=your_api_key_here
```

Run the application:

```bash
python main.py
```

---

## Author

Aleyna Dede
Artificial Intelligence Engineer
