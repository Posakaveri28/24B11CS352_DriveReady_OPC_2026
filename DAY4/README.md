# 🔧 Day 4: Giving LLMs Superpowers with Tools, Schemas & Sheets

Welcome to my **Day 4** learning log! Today marked a huge milestone: we graduated from simple chatbots into **autonomous agents that can call Python functions**, extract typed Pydantic orders from messy chats, and log customer bookings directly into Google Sheets.

---

## 🎯 What I Built & Explored

- **Projects:** *Sweet Crumbs Bakery* (core tool-calling agent) & *BrightPage Stationery* (retail ordering assistant).
- **Model Used:** `openai/gpt-oss-20b` via Groq Cloud (`ChatGroq`, `temperature=0.2`).
- **Goal:** Equip models with real-world capabilities using LangChain's `@tool` decorator, protect data integrity with Pydantic schemas, trace step-by-step agent decisions, and persist confirmed orders to spreadsheets.

---

## 💡 Key Takeaways & Concepts

1. **Why Docstrings Are the Model's Manual:**
   - When we decorate a Python function with `@tool`, LangChain sends its name, argument types, and docstring to the LLM as its instruction manual.
   - **The Break-It Test:** When we renamed `get_price` to `tool1` with the docstring `"does stuff"`, the model had no idea what it did and generated **0 tool calls**! Restoring clear docstrings immediately brought back accurate tool calls.

2. **Pydantic Validation (`with_structured_output`):**
   - Customers text informal, incomplete, or messy messages (slang, missing punctuation).
   - Using Pydantic models (`Order` and `StationeryOrder`), we reliably extracted customer names, items, quantities, and delivery dates into clean, validated JSON objects every time.

3. **Reading Agent Traces (`pretty_print()`):**
   - An agent doesn't just guess an answer in one go. Looking at the message trace reveals:
     - `HumanMessage`: The customer's multi-part question.
     - `AIMessage`: The agent reasoning and requesting tool calls (`is_open` and `get_price`).
     - `ToolMessage`: The return values from our Python functions.
     - Final `AIMessage`: The synthesized, friendly reply to the customer.

4. **Guarding Persistent Sheets Against Invalid Data:**
   - Tested adversarial inputs (ordering unlisted donuts, ordering 0 cupcakes, missing dates).
   - The agent caught each edge case, explained the policy politely, and **never called `log_order`** on invalid requests — keeping our sheet clean with only confirmed orders.

---

## 📁 Directory Files

| File | Description |
| :--- | :--- |
| [`task.ipynb`](task.ipynb) | Complete Day 4 notebook covering tools, Pydantic schemas, sheet logging, and trace analysis. |
| [`sweet_crumbs_orders.csv`](sweet_crumbs_orders.csv) | Local CSV mirror of the Sweet Crumbs Bakery orders sheet. |
| [`brightpage_orders.csv`](brightpage_orders.csv) | Local CSV mirror of the BrightPage Stationery orders sheet. |

---

## 🚀 How to Run in Google Colab

1. Upload [`task.ipynb`](task.ipynb), [`sweet_crumbs_orders.csv`](sweet_crumbs_orders.csv), and [`brightpage_orders.csv`](brightpage_orders.csv) to Google Colab.
2. In the **Secrets (🔑)** panel on the left, add `GROQ_API_KEY` and toggle **Notebook access** to **ON**.
3. Run all cells (`Ctrl + F9`). When prompted by `auth.authenticate_user()`, sign in to grant Google Sheets access.

---
*Maintained by Posakaveri28.*
