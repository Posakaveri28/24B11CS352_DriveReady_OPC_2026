# 🧪 Day 3: Composable Chains, Test Evaluation & Agent Sneak Peek

Welcome to my **Day 3** learning log! In this session, we upgraded our workflow to modern **LangChain LCEL chains**, implemented automated test suites to measure prompt quality objectively, and got our first preview of autonomous multi-step agents using the **Google Gemini API**.

---

## 🎯 What I Built & Explored

- **Projects:** *Sweet Crumbs Bakery* (evaluation baseline) & *BrightPage Stationery* (prompt tuning & decision framework).
- **Model Used:** `gemini-3.5-flash-lite` via `ChatGoogleGenerativeAI` (`langchain-google-genai`).
- **Goal:** Replace manual string-formatting with composable LCEL pipelines (`prompt | llm | StrOutputParser()`), automate prompt testing with CSV assertion files, and learn when to choose plain Python vs. an LLM call vs. an Agent.

---

## 💡 Key Takeaways & Concepts

1. **Composable LCEL Pipelines:**
   - Used `ChatPromptTemplate.from_messages` to cleanly separate system instructions, multi-turn memory (`MessagesPlaceholder("history")`), and customer input.
   - Piped directly: `prompt | llm | StrOutputParser()`, producing clean text strings automatically.

2. **Automated Prompt Testing (No More Guesswork):**
   - Built a testing function `run_tests()` that runs benchmark questions from a CSV file.
   - Automated assertions using `must_include` keywords (e.g. checking that an inquiry about plum cake returns `500`).
   - Generates exact percentage pass rates so we know immediately if a prompt change caused regressions.

3. **Prompt Iteration (V1 vs. V2):**
   - Evaluated BrightPage Stationery against [`brightpage_tests.csv`](brightpage_tests.csv).
   - Iterated on the prompt to improve handling of Sunday hours, delivery rules, and return policies, watching the pass rate jump.

4. **Tool Selection Strategy:**
   - **Plain Code:** Perfect for arithmetic, totals, discounts, and delivery fees (100% accurate, instant, free).
   - **Single LLM Call:** Best for semantic understanding (intent classification, sentiment, tone).
   - **Autonomous Agent:** Necessary when tasks require multi-step reasoning and dynamic tool execution (e.g. checking stock, computing discounts, placing the order).

---

## 📁 Directory Files

| File | Description |
| :--- | :--- |
| [`task.ipynb`](task.ipynb) | Day 3 notebook containing LCEL chains, test evaluation functions, and agent preview cells. |
| [`tests.csv`](tests.csv) | 10 benchmark test queries and expected assertions for Sweet Crumbs Bakery. |
| [`brightpage_tests.csv`](brightpage_tests.csv) | 10 benchmark test queries and expected assertions for BrightPage Stationery. |

---

## 🚀 How to Run in Google Colab

1. Upload [`task.ipynb`](task.ipynb), [`tests.csv`](tests.csv), and [`brightpage_tests.csv`](brightpage_tests.csv) to Colab.
2. Under the **Secrets (🔑)** panel, add **`GOOGLE_API_KEY`** (get one free at [aistudio.google.com](https://aistudio.google.com/)) and toggle **Notebook access** to ON.
3. Run all cells (`Ctrl + F9`).

---
*Maintained by Posakaveri28.*
