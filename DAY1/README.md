# 🍪 Day 1: Exploring LLM APIs & Safety Guardrails

Welcome to my **Day 1** learning log! This notebook focuses on getting comfortable with programmatic LLM calls, understanding how generative models behave, and adding safety checks to verify customer queries.

---

## 🎯 What I Built & Explored

- **Project:** *Sweet Crumbs Home Bakery Assistant* — a customer service helper for a boutique bakery.
- **Goal:** Connect to high-speed LLM inference via Groq Cloud, test how prompt instructions constrain model outputs, and filter unsafe user inputs using Meta Llama Prompt Guard.

---

## 💡 Key Takeaways & Concepts

1. **How LLMs Work Under the Hood:**
   - **Next-Token Probabilities:** Generative models predict the most likely next token from their training distribution.
   - **Stateless Nature:** LLM endpoints don't retain memory between calls. Every new interaction needs the full prompt context passed in.
   - **Temperature Control:** Using $T=0.2$ keeps bakery facts and prices consistent, while $T=1.2$ introduces noticeable variation.

2. **Inference with LangChain & Groq:**
   - Used LangChain's `ChatGroq` wrapper connecting to `openai/gpt-oss-120b`.
   - Built a simple `ask(question)` function that packages our bakery system rules with each customer question.

3. **Safety First with Prompt Guard:**
   - Implemented Meta's lightweight safety classifier (`meta-llama/llama-prompt-guard-2-22m`).
   - Successfully flagged test jailbreak attempts and off-topic adversarial inputs before they reached the bakery assistant.

---

## 🛠️ Step-by-Step Walkthrough

1. **Setup & Dependencies:** Installed `langchain_groq`, `groq`, and `python-dotenv`.
2. **Bakery Rules:** Defined strict facts:
   - All cakes baked to order with 24 hours advance notice required.
   - Eggless versions available for all cakes.
   - Standard prices: Cupcake (₹80), Sourdough Loaf (₹180), Cheesecake (₹750).
3. **Prompt Guard Integration:** Tested input safety scores against normal customer requests vs. injection attacks.
4. **Interactive Colab UI:** Created an `ipywidgets` testing box with preset questions to simulate customer interactions live.

---

## 📁 Directory Files

| File | Description |
| :--- | :--- |
| [`agenticAI_Day1.ipynb`](agenticAI_Day1.ipynb) | Complete Jupyter notebook with code cells, explanations, and widgets. |
| [`.env.example`](.env.example) | Example environment file showing the `GROQ_API_KEY` setting. |

---

## 🚀 How to Run in Google Colab

1. Open [`agenticAI_Day1.ipynb`](agenticAI_Day1.ipynb) in Colab.
2. In the **Secrets (🔑)** panel on the left, add `GROQ_API_KEY` and enable notebook access.
3. Run all cells (`Ctrl + F9`).

---
*Maintained by Posakaveri28.*
