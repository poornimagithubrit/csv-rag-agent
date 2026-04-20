# 📊 CSV RAG Agent — Conversational BI Chatbot

> A Retrieval-Augmented Generation (RAG) agent that converts natural language questions into SQL/pandas operations on CSV data — with dynamic chart visualization and business analytics output.

---

## 🧩 Problem

Business analysts without SQL knowledge struggle to extract insights from data files. Writing queries takes time, and most BI tools have steep learning curves.

## ✅ Solution

A conversational AI agent that lets anyone query CSV data in plain English:
- **"What are the top 5 products by revenue this quarter?"**
- **"Show me a bar chart of monthly sales trends"**
- **"Which region had the highest growth compared to last year?"**

---

## 🏗️ Architecture

```
User Natural Language Query
        │
        ▼
  GPT-4o (Query Understanding)
        │
        ▼
  RAG Pipeline
  (Schema-aware context retrieval)
        │
        ▼
  Code Generator
  (SQL or Pandas operations)
        │
        ├──► Pandas Executor (for CSV files)
        │
        └──► Chart Generator (Matplotlib/Plotly)
                  │
                  ▼
            Formatted Answer + Visualization
```

---

## 🛠️ Tech Stack

| Component | Technology |
|---|---|
| LLM | OpenAI GPT-4o |
| RAG Framework | LangChain |
| Data Processing | Pandas, NumPy |
| Visualization | Matplotlib, Plotly |
| Vector Store | FAISS |
| Backend | FastAPI |
| Language | Python 3.10+ |

---

## 📂 Project Structure

```
csv-rag-agent/
├── agent/
│   ├── csv_agent.py            # Core LangChain CSV agent
│   ├── schema_extractor.py     # Extract CSV schema for RAG context
│   └── prompts.py              # System prompts
├── data/
│   └── sample_data.csv         # Sample dataset for testing
├── visualization/
│   └── chart_generator.py      # Dynamic chart creation
├── api/
│   └── main.py                 # FastAPI endpoints
├── requirements.txt
├── .env.example
└── README.md
```

---

## ⚙️ Setup

```bash
git clone https://github.com/poornimagithubrit/csv-rag-agent
cd csv-rag-agent
pip install -r requirements.txt
cp .env.example .env
# Add your OpenAI API key
```

---

## 🔑 Environment Variables

```env
OPENAI_API_KEY=your_openai_api_key_here
```

---

## 🚀 Usage

```bash
# Start the API
uvicorn api.main:app --reload

# Upload a CSV and ask questions
POST /upload-csv          # Upload your CSV file
POST /query               # Ask a natural language question
GET  /chart/{query_id}    # Get the generated chart
```

**Example Query:**
```json
{
  "question": "What are the top 5 products by total sales in 2025?",
  "chart_type": "bar"
}
```

**Example Response:**
```json
{
  "answer": "The top 5 products by total sales are...",
  "chart_url": "/charts/query_123.png",
  "pandas_code": "df.groupby('product')['sales'].sum().nlargest(5)"
}
```

---

## 📊 Sample Queries You Can Try

- *"Show me monthly revenue trends as a line chart"*
- *"Which customer segment has the highest average order value?"*
- *"Compare Q1 vs Q2 performance by region"*
- *"Find all orders above ₹50,000 in March 2025"*

---

## 📊 Results

- ✅ Natural language → pandas/SQL in under 2 seconds
- ✅ Supports bar, line, pie, and scatter chart generation
- ✅ Works with any CSV structure — schema-aware RAG context
- ✅ No SQL knowledge required for end users

---

## 📦 Requirements

```
langchain
openai
fastapi
uvicorn
pandas
numpy
matplotlib
plotly
faiss-cpu
python-dotenv
python-multipart
```

---

## 📄 License

MIT License
