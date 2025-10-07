# Multi-Agent QA on Financial Documents

This repo implements **Prepathon 2025 NLP project**:

* **Task 1**: Build a document retriever for financial reports for which I used **Jina embeddings** + **FAISS**.
* **Task 2**: Extend to a **dynamic multi-agent swarm** for which I used **Groq LLM** for query answering, reasoning, and explainability.

---

## 📂 Project Structure

```
.
├── retriever.ipynb     # Task 1: PDF → Embeddings → FAISS → Retrieval → RAPTOR-like clustering
├── multi_agent.ipynb   # Task 2: Dynamic multi-agent orchestration with Groq API
├── data/               # Stored embeddings, indexes, memory
├── outputs/            # JSON traces of agent runs
├── requirements.txt    # Dependencies
├── .gitignore
├── report.pdf
└── README.md
```

---

## ⚙️ Installation

### 1. Clone repo & install deps

```bash
git clone <https://github.com/s4kr3d-w0r1d/FinanceRAG.git>
cd <FinanceRAG>
pip install -r requirements.txt
```

### 2. Environment variables

You need 2 API keys:

* **Jina API key** for embeddings
* **Groq API key** for agent orchestration

Set them in your environment:

```bash
export JINA_API_KEY="your_jina_key_here"
export GROQ_API_KEY="your_groq_key_here"
```

---

## 🚀 Usage

### Task 1: Retriever

Open `retriever.ipynb` and run:

1. Convert PDF → images
2. Embed images with Jina
3. Build FAISS index
4. Query → Retrieve pages
5. Parse pages → Build RAPTOR clusters
6. Answer query

### Task 2: Multi-Agent QA

Open `multi_agent.ipynb` and run:

1. Initialize agents: Retriever, Table, Math, Summarizer
2. Groq Supervisor dynamically decides next agent
3. Run any query (e.g., YoY growth, risk analysis)
4. Get final human-readable answer + JSON trace in `outputs/`

---

## 📊 Example Query

```python
query = "Compare the YoY revenue growth and R&D spending between 2021 and 2022, and summarize the risks affecting future revenue."
result = system.run(query)

print(result["final_answer"])
```

---

## ✅ Deliverables for Submission

* Working Code in both notebooks
* JSON Logs of agent traces saved in `/outputs/`
* Report (architecture, sample runs, evaluation)

---

## 📌 Notes

* The system currently extracts tables heuristically; accuracy depends on the PDF structure.
* Groq is used as the Supervisor Reasoner and Summarizer for dynamic decision-making.
* Jina embeddings handle page-level image + text retrieval.
