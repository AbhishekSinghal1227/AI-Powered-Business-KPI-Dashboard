# 📊 AI-Powered Business KPI Dashboard

> Ask questions about your business data in **plain English** — get instant SQL queries and interactive charts powered by OpenAI GPT.

---

## 🎯 What This Project Does

Upload any CSV or Excel file and ask natural language questions like:

- *"What are the total sales by Region?"*
- *"Show me the top 10 products by revenue"*
- *"Show the monthly sales trend over time"*
- *"Which category has the highest profit?"*

The AI translates your question into SQL, runs it against your data, and automatically renders the best chart — bar, line, scatter, or pie.

---

## 🖼️ Demo

| Question | Chart Type |
|---|---|
| Total sales by Region | Bar Chart |
| Monthly revenue trend | Line Chart |
| Revenue share by Category | Pie Chart |
| What is total profit? | Metric Card |
| Top 10 products by sales | Bar Chart |

---

## 🏗️ How It Works

```
Your Question (plain English)
         ↓
 Schema injected into prompt
         ↓
  OpenAI GPT generates SQL
         ↓
  SQL runs on SQLite (in RAM)
         ↓
  Plotly renders the chart
```

**Key design decisions:**
- ✅ Raw data never leaves your machine — only column names + 3 sample values are sent to the API
- ✅ SQLite in-memory database — no server needed, disappears when notebook closes
- ✅ Multi-turn conversation — follow-up questions maintain context
- ✅ JSON-forced output — GPT always returns structured data, never free text

---

## 🚀 Quick Start

### 1. Clone the repository
```bash
git clone https://github.com/AbhishekSinghal1227/AI-Powered-Business-KPI-Dashboard
cd AI-Powered-Business-KPI-Dashboard
```

### 2. Install dependencies
```bash
pip install -r requirements.txt
```

### 3. Get your OpenAI API Key
- Go to [platform.openai.com/api-keys](https://platform.openai.com/api-keys)
- Create a new secret key
- Copy it — starts with `sk-`

### 4. Add your API key
Open `AI_Powered_KPI_Dashboard.ipynb` and in **Cell 3**, replace:
```python
os.environ['OPENAI_API_KEY'] = 'your-openai-api-key-here'
```
with your actual key.

### 5. Add your data
- Download the Superstore dataset from [Kaggle](https://www.kaggle.com/datasets/vivek468/superstore-dataset-final)
- Or use any CSV / Excel file you have
- Place it in the same folder as the notebook
- Update `FILE_PATH` in Cell 4 with your file name

### 6. Launch Jupyter and run!
```bash
jupyter notebook
```
Open `AI_Powered_KPI_Dashboard.ipynb` and run cells from top to bottom.

---

## 📁 Project Structure

```
ai-kpi-dashboard/
├── AI_Powered_KPI_Dashboard.ipynb   ← Main notebook
├── requirements.txt                  ← Python dependencies
├── README.md                         ← This file
└── .gitignore                        ← Keeps secrets + data out of GitHub
```

---

## 🔧 Tech Stack

| Technology | Purpose |
|---|---|
| Python 3.11 | Core language |
| OpenAI GPT-4o-mini | Natural language to SQL translation |
| Pandas | Data loading and manipulation |
| SQLite (in-memory) | SQL query execution engine |
| Plotly | Interactive chart rendering |
| Jupyter Notebook | Development environment |

---

## 💡 Example Questions to Try

```python
# Basic analysis
query("What are the total sales by Region?")
query("What is the total profit?")

# Rankings
query("Show me the top 10 products by total sales")
query("Which are the bottom 5 cities by profit?")

# Time series
query("Show the monthly sales trend over time")
query("Which month had the highest revenue?")

# Comparisons
query("Which Category has the highest profit margin?")
query("Compare sales across different Ship Modes")

# Follow-up questions (multi-turn)
query("Show sales by Sub-Category")
query("Now show only the top 5 from that result")   # GPT remembers context!
```

---

## 🔒 Security Note

⚠️ **Never commit your API key to GitHub.**

Your `.gitignore` already excludes `.env` files. For extra safety, use environment variables:

```python
# Safer approach — set key in terminal before launching Jupyter
# Windows:  set OPENAI_API_KEY=sk-your-key-here
# Mac/Linux: export OPENAI_API_KEY=sk-your-key-here

# Then in the notebook, just use:
client = OpenAI()  # automatically reads from environment
```

---

## 🛠️ Troubleshooting

| Error | Fix |
|---|---|
| `ModuleNotFoundError: openai` | Run `pip install openai` in terminal |
| `AuthenticationError` | Check your API key in Cell 3 |
| `JSONDecodeError` | Reset history: `conversation_history = []` and retry |
| `OperationalError: near "Name"` | Column has spaces — already handled in prompt |
| Chart not showing | Re-run Cell 7 to reload the chart function |

---

## 📈 What I Learned Building This

- **Prompt Engineering** — How to instruct an LLM to return structured JSON reliably
- **Text-to-SQL** — Converting natural language questions into valid SQLite queries
- **Schema Injection** — Sending column metadata (not raw data) to the API for privacy
- **Multi-turn Conversations** — Managing conversation history for context-aware follow-ups
- **Safe Query Execution** — Only running SQL SELECT statements, never arbitrary code

---

## 🔮 Future Improvements

- [ ] Connect to real databases (PostgreSQL, Snowflake)
- [ ] Export charts and analysis to PDF report
- [ ] Add Streamlit frontend for non-technical users
- [ ] Scheduled email reports with auto-generated insights
- [ ] Support for multiple CSV files with JOIN queries

---

## 👤 Author

**Your Name**
- LinkedIn: [Abhishek Singal](https://www.linkedin.com/in/abhishek-singhal-351399170/)
- GitHub: [@AbhishekSinghal1227](https://github.com/AbhishekSinghal1227/AI-Powered-Business-KPI-Dashboard)

---

## 📄 License

MIT License — feel free to use and modify for your own projects.

---

*Built as part of an AI Data Analyst portfolio project*
