# 📓 My Agentic AI Journey · Hands-on Lab Notebook

> *"Documenting daily implementations, prompt designs, and agent architectures from the ground up."*

Welcome! 👋 This repository is my personal collection of daily lab exercises, code walkthroughs, and architectural experiments built during the **Agentic AI Series**. Every module includes working code, comprehensive documentation, and automated test suites.

---

## 🗺️ Sprints & Milestones

### 🍰 Day 01 — First LLM API Calls & Safety Guardrails
* **Domain:** Sweet Crumbs Home Bakery Assistant
* **Key Learnings:**
  * Understanding tokenization, sampling temperature, and stateless API interactions.
  * Setting up ultra-fast inference with LangChain and the Groq Cloud API.
  * Implementing Meta Llama Prompt Guard to detect prompt injections and malicious inputs before they reach the model.
* **Direct Access:** [Read Day 1 Lab Notes ➔](DAY1/README.md) · [Open Day 1 Notebook ➔](DAY1/agenticAI_Day1.ipynb)

---

### 📦 Day 02 — Agent Foundations: Memory, Prompts & JSON
* **Domain:** BrightPage Stationery & Office Supplies Assistant
* **Key Learnings:**
  * Crafting production-grade prompts using the **4-Pillar Framework** (Role, Facts, Rules, Format).
  * High-accuracy customer intent classification using in-context few-shot prompting.
  * Transforming casual customer conversations into structured, typed JSON order records.
  * Building a custom sliding-window conversation memory loop (`MAX_TURNS`) with graceful HTTP 429 rate limit error handling.
* **Direct Access:** [Read Day 2 Lab Notes ➔](DAY2/README.md) · [Open Day 2 Notebook ➔](DAY2/agenticAI_Day2.ipynb)

---

### ⚡ Day 03 — LCEL Composable Chains & Test Suites
* **Domain:** Bakery & Stationery Dual-Evaluation
* **Key Learnings:**
  * Refactoring raw message lists into composable **LangChain Expression Language (LCEL)** chains (`prompt | llm | StrOutputParser()`).
  * Moving from subjective testing to objective, test-driven prompt evaluation using automated CSV assertion suites.
  * Exploring the **Google Gemini API** (`gemini-3.5-flash-lite`) and previewing autonomous reasoning loops with `create_agent`.
  * Learning the practical decision framework: when to write plain code vs. a single LLM call vs. an autonomous agent.
* **Direct Access:** [Read Day 3 Lab Notes ➔](DAY3/README.md) · [Open Day 3 Notebook ➔](DAY3/task.ipynb)

---

### 🛠️ Day 04 — Tool-Calling Agents, Schemas & Sheets
* **Domain:** Bakery & Stationery Autonomous Ordering
* **Key Learnings:**
  * Converting regular Python functions into model-invocable tools with LangChain's `@tool` decorator.
  * Discovering how docstrings act as the model's manual (and how vague descriptions like `"does stuff"` break tool selection).
  * Enforcing Pydantic schemas (`Order` and `StationeryOrder`) to parse messy chats into database-ready records.
  * Connecting live order logging to Google Sheets (`gspread`) and local CSV mirrors while rejecting invalid edge-case queries.
  * Tracing the complete agent lifecycle (`HumanMessage` ➔ `AIMessage` tool request ➔ `ToolMessage` result ➔ final answer).
* **Direct Access:** [Read Day 4 Lab Notes ➔](DAY4/README.md) · [Open Day 4 Notebook ➔](DAY4/task.ipynb)

---

### 🧠 Day 05 — Thread Memory, ChromaDB RAG & PDF Intelligence
* **Domain:** BrightPage Stationery Agent & Story Document QA
* **Key Learnings:**
  * Isolating concurrent customer sessions using LangGraph's `InMemorySaver` with unique `thread_id`s.
  * Building semantic vector search over 16 store policies and FAQs using `ChromaDB` and `all-MiniLM-L6-v2`.
  * Exposing knowledge retrieval as an autonomous `@tool` to ground answers and prevent hallucination.
  * Passing 17/18 (94%) automated evaluation tests across pricing, policies, and edge cases.
  * Multi-paragraph PDF RAG lab (`story_rag.pdf`): text extraction, semantic chunking, and grounded Q&A with refusal.
* **Direct Access:** [Read Day 5 Lab Notes ➔](DAY5/README.md) · [Open Day 5 Notebook ➔](DAY5/task.ipynb)

---

## 💡 How to Run the Code

### 🔹 Running in Google Colab (Zero-Setup Method)
1. Open any notebook link above directly in **Google Colab**.
2. Open the **Secrets (🔑)** panel on the left sidebar.
3. Add your free API keys and toggle **Notebook access** to **ON**:
   * `GROQ_API_KEY`: For Day 1, Day 2, Day 4 & Day 5 (free from [console.groq.com](https://console.groq.com/))
   * `GOOGLE_API_KEY`: For Day 3 (free from [aistudio.google.com](https://aistudio.google.com/))
4. Select **Runtime ➔ Run all** (`Ctrl + F9`).

### 🔹 Running Locally
```bash
# 1. Clone repository
git clone https://github.com/Posakaveri28/24B11CS352_DriveReady_OPC_2026.git
cd 24B11CS352_DriveReady_OPC_2026

# 2. Configure environment
cp .env.example .env
# (Insert your GROQ_API_KEY and GOOGLE_API_KEY inside .env)

# 3. Install packages & start
pip install langchain langchain-groq langchain-google-genai langgraph chromadb sentence-transformers pypdf gspread openai pydantic ipywidgets python-dotenv
jupyter notebook
```

---

## 📂 Project Organization

* **`DAY1/`** — `agenticAI_Day1.ipynb` · `README.md` · `.env.example`
* **`DAY2/`** — `agenticAI_Day2.ipynb` · `README.md`
* **`DAY3/`** — `task.ipynb` · `tests.csv` · `brightpage_tests.csv` · `README.md`
* **`DAY4/`** — `task.ipynb` · `sweet_crumbs_orders.csv` · `brightpage_orders.csv` · `README.md`
* **`DAY5/`** — `task.ipynb` · `story_rag.pdf` · `tests.csv` · `brightpage_orders.csv` · `README.md`

---
✨ *Crafted & maintained by **Posakaveri28**.*
