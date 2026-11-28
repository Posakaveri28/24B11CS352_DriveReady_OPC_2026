# 🧠 Day 5: Multi-Turn Thread Memory, Vector Search & PDF RAG

Welcome to my **Day 5** learning log! Today was all about solving two of the biggest hurdles in building practical AI agents: giving them **isolated multi-turn conversation memory** and connecting them to **external knowledge bases via RAG (Retrieval-Augmented Generation)** using vector databases.

---

## 🎯 What I Built & Explored

- **Projects:** *BrightPage Stationery Ordering Agent* (with thread memory & FAQ search) & *The Whispering Umbrella PDF RAG Lab*.
- **Models Used:** `openai/gpt-oss-120b` via Groq Cloud (`ChatGroq`, `temperature=0.2`) and `all-MiniLM-L6-v2` embeddings (`sentence-transformers`).
- **Goal:** Maintain independent chat sessions across different customers using LangGraph's `InMemorySaver`, store company FAQs in a local ChromaDB vector store, turn semantic search into an autonomous tool, and build a grounded PDF question-answering assistant.

---

## 💡 Key Takeaways & Concepts

1. **Short-Term Memory vs. Long-Term Memory vs. Knowledge:**
   - **Short-Term (Thread Memory):** Keeps track of messages within a single active conversation (`InMemorySaver` + `thread_id`).
   - **Long-Term Memory:** Remembers persistent facts across separate days (e.g. past orders in a database or sheet).
   - **Knowledge Base (RAG):** Answers store policies and FAQs from reference documents without retraining the model.

2. **Isolating Chats with `thread_id`:**
   - By attaching `config={"configurable": {"thread_id": "ravi"}}`, the model remembered Ravi's paper reams order and his name across multiple turns.
   - Meanwhile, switching to `thread_id="sravani"` started a completely blank conversation with zero risk of data leaking between customers.

3. **Vector Search with ChromaDB:**
   - Split policy text into chunks using an overlapping sliding window (`chunk_size=220`, `overlap=40`).
   - Generated 384-dimensional dense vector embeddings using `all-MiniLM-L6-v2`.
   - Packaged search into a tool: `@tool search_brightpage_faq(question)`, allowing the agent to look up answers on the fly.

4. **18-Row Evaluation Benchmark (94% Passing Score!):**
   - Ran our full automated testing suite across prices, delivery rules, return windows, and out-of-scope items.
   - The agent passed **17 out of 18 test queries (94%)**, easily exceeding our 80% passing threshold!

5. **Multi-Paragraph PDF Document QA Lab:**
   - Parsed *The Whispering Umbrella* ([`story_rag.pdf`](story_rag.pdf)) using `pypdf`.
   - Indexed paragraph chunks in ChromaDB.
   - Verified grounded answers when facts were present in the story, and confirmed honest refusals (*"The answer is not available in the PDF."*) when asked about facts not in the document.

---

## 📁 Directory Files

| File | Description |
| :--- | :--- |
| [`task.ipynb`](task.ipynb) | Day 5 notebook covering thread memory, ChromaDB FAQ RAG, evaluation, and the PDF lab. |
| [`story_rag.pdf`](story_rag.pdf) | 3-paragraph PDF document used for chunking, embedding, and grounded question answering. |
| [`tests.csv`](tests.csv) | 18-query sign-off evaluation test suite. |
| [`brightpage_orders.csv`](brightpage_orders.csv) | Local CSV mirror of the BrightPage Stationery orders sheet. |

---

## 🚀 How to Run in Google Colab

1. Upload [`task.ipynb`](task.ipynb), [`story_rag.pdf`](story_rag.pdf), and [`tests.csv`](tests.csv) to Google Colab.
2. In the **Secrets (🔑)** panel, add `GROQ_API_KEY` and enable notebook access.
3. Run all cells (`Ctrl + F9`). Authenticate with Google Sheets when prompted.

---
*Maintained by Posakaveri28.*
