# Agentic AI — Daily Hands-on Learning Journal

Welcome to my personal hands-on repository for Agentic AI! This space documents daily practical exercises, prompt engineering techniques, and progressively intelligent agent architectures.

---

## 📖 Daily Learning Log

### 📂 Day 1: Hello World with LLM APIs & Safety Guardrails
- **Folder:** [`DAY1/`](DAY1/)
- **Notebook:** [`agenticAI_Day1.ipynb`](DAY1/agenticAI_Day1.ipynb)
- **Project:** Sweet Crumbs Bakery Ordering Assistant
- **What I Built & Learned:**
  - How tokenization, temperature, and context length impact generation.
  - Setting up fast inference on Groq using LangChain (`openai/gpt-oss-120b`).
  - Safeguarding model interactions using Meta Llama Prompt Guard to filter jailbreaks and out-of-bounds queries.
  - Notebook UI experiments with interactive prompt scenarios.

---

### 📂 Day 2: Building Agents — Prompts, Memory & Structured JSON
- **Folder:** [`DAY2/`](DAY2/)
- **Notebook:** [`agenticAI_Day2.ipynb`](DAY2/agenticAI_Day2.ipynb)
- **Project:** BrightPage Stationery Store Assistant
- **What I Built & Learned:**
  - **The 4-Pillar System Prompt:** Structuring Role, Facts, Rules, and Format for reliable bot behavior.
  - **Few-Shot Classification:** Accurately categorizing customer messages into `order`, `inquiry`, or `complaint`.
  - **Structured Data Extraction:** Pulling clean, typed JSON order objects from loose natural language.
  - **Conversation Memory by Hand:** Implementing a sliding window memory loop (`MAX_TURNS`) without external framework dependencies.
  - **Resilience:** Gracefully catching API exceptions and rate limits.
  - **Colab Dashboard:** Using `ipywidgets` for an interactive chat simulation interface.

---

## ⚙️ How to Get Started

### Option A: Run in Google Colab (Recommended)
1. Open either notebook directly in Google Colab.
2. In the left panel, click the **Secrets** (🔑) tab.
3. Add a secret named `GROQ_API_KEY` with your free Groq API key and toggle **Notebook access** to ON.

### Option B: Run Locally
1. Ensure Python 3.10+ is installed.
2. Create your `.env` file from `.env.example`:
   ```bash
   cp .env.example .env
   ```
3. Insert your key:
   ```env
   GROQ_API_KEY=your_key_here
   ```
4. Run the notebooks via VS Code or Jupyter Notebook.

---
*Maintained by Posakaveri28.*
