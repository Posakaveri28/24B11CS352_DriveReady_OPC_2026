# ✏️ Day 2: Building Conversational Agents — Prompts, Memory & JSON

Welcome to my **Day 2** learning log! Today was all about taking the leap from single API calls to building an interactive, stateful sales assistant for a stationery shop.

---

## 🎯 What I Built & Explored

- **Project:** *BrightPage Stationery & Office Supplies Assistant*
- **Goal:** Design a robust 4-pillar system prompt, build an intent classifier using few-shot prompting, extract structured order data in JSON format, and create multi-turn conversation memory by hand.

---

## 💡 Key Takeaways & Concepts

1. **The 4-Pillar System Prompt Framework:**
   - **Role:** Friendly and efficient assistant for BrightPage Stationery.
   - **Facts:** Fixed prices (A4 Ream ₹320, Gel Pens Pack ₹150, Spiral Notebook ₹85, Highlighter Set ₹120), free shipping over ₹500 (otherwise ₹50), 10% discount for 10+ items.
   - **Rules:** Never make up unlisted items; answer with *"I'll check with the store manager and get back to you."* Never promise same-day delivery.
   - **Format:** Under 60 words, using bullet points when listing multiple items.

2. **Few-Shot In-Context Prompting:**
   - Provided concrete examples in the prompt to teach the model to classify user messages cleanly into `order`, `inquiry`, or `complaint`.

3. **Extracting Clean JSON Orders:**
   - Transformed messy, informal customer messages (e.g. *"I need 2 packs of gel pens and a ream of paper"*) into validated, typed JSON order dictionaries.

4. **Handcrafted Conversation Memory:**
   - Built a custom loop keeping track of recent chat turns.
   - Implemented a sliding window (`MAX_TURNS`) so long chats don't blow past model token limits.
   - Wrapped API calls in `try / except` to gracefully handle rate limit (HTTP 429) errors.

5. **Student Verification Experiments:**
   - **Temperature Test:** Tested how $T=0.2$ maintains factual accuracy while $T=1.2$ can lead to hallucinated items.
   - **Boundary Test:** Verified that asking for non-catalogue items (like fountain pens) triggers the store manager fallback response.
   - **Memory Trimming:** Confirmed that turns older than `MAX_TURNS` are discarded while recent names and preferences are remembered.

---

## 📁 Directory Files

| File | Description |
| :--- | :--- |
| [`agenticAI_Day2.ipynb`](agenticAI_Day2.ipynb) | Complete Day 2 Jupyter notebook with code cells, widgets, and experiments. |

---

## 🚀 How to Run in Google Colab

1. Open [`agenticAI_Day2.ipynb`](agenticAI_Day2.ipynb) in Colab.
2. Ensure `GROQ_API_KEY` is present in the **Secrets (🔑)** panel and toggled ON.
3. Run all cells (`Ctrl + F9`).

---
*Maintained by Posakaveri28.*
