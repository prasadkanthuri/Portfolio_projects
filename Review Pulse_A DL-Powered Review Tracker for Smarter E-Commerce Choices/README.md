# 🛒 ReviewPulse – A DL-Powered Review Tracker for Smarter E-Commerce Choices

> **“Buying smart should take minutes, not hours.”**

---

## 💡 Idea & Motivation

Online shopping has become a routine part of our lives. But how often do we spend **10–20 minutes** just reading through reviews to decide whether to buy a product?

- We manually scroll through **dozens of reviews** to get a sense of the product.
- Even after reading ~50 reviews in 10 minutes, we might miss crucial feedback.
- What if there's a way to **automatically read 200 reviews**, categorize them, summarize their key points, and provide a **quick verdict**?

That's where **ReviewPulse** steps in. With the **power of Transformers** and a bit of automation, this tool **summarizes customer opinions** so that **you make smarter decisions faster**.

---

## 🚀 How It Works

### 🔗 Step 1: Input
You just paste the **Flipkart product URL**.

### ⚙️ Step 2: Automation Begins
Under the hood:
- The tool extracts the `product ID` and builds a direct link to the **review page**.
- Using **Selenium**, it launches a headless browser to:
  - Navigate to the reviews section.
  - Sort them by **Most Recent**.
  - Load multiple pages to collect up to **200 reviews**.

### 🧠 Step 3: Review Extraction & Cleaning
For every review:
- We extract:
  - Title  
  - Full review content  
  - Rating (1–5)
- **All emojis are removed** to prevent noise in NLP tasks.

### 🧪 Step 4: Classification
Based on the star ratings:
- **4–5 stars** → Positive  
- **1–2 stars** → Negative  
- **3 stars** → Neutral  

Each group is separated for targeted summarization.

### 📝 Step 5: Summarization using Transformers
We use **Facebook’s BART Large CNN model** from Hugging Face Transformers to:
- Summarize each group (Positive / Negative / Neutral) separately.
- Then feed those summaries into the model again to generate a **final verdict** — a crisp, all-in-one review of the latest feedback.

### 🖼️ Step 6: Visual Output
- A clean web UI built using **Gradio** displays:
  - Product image  
  - Summarized reviews in three tabs  
  - Key stats: number of reviews, sentiment breakdown, average rating  
  - A powerful **final decision-making summary** (verdict)
 
  


---

## 📦 Why 200 Reviews?

- **Trade-off between accuracy and speed**:  
  200 reviews offer a **representative sample** of recent customer feedback.
- Scraping more could lead to higher latency and more repetitive content.
- Summarizing beyond 200 increases **computation cost and processing time**.
- For most products, 200 recent reviews are more than enough to understand:
  - Common praise  
  - Repeated complaints  
  - Emerging trends

---

## ⏱️ Why Most Recent Reviews?

- Products evolve: newer batches may differ in quality.
- Old reviews might not reflect the **current state of the product**.
- Recent reviews = more relevant, more aligned with your **current purchase decision**.

---

## 💻 Deployment Details

- Built using **Python**, deployed via **Gradio**, which allows:
  - Fast web-based deployment.
  - Inline hosting or sharing with others.
- The interface is styled with **custom CSS** to enhance UX.
- No need to install heavy dependencies locally – everything is packaged in a single script.

---

## 🎯 Benefits

✅ **Time Saver**  
Skim **200 reviews in 4 minutes**, instead of 50 reviews in 10 minutes manually.

✅ **Smarter Buying Decisions**  
Clear insights based on **real customer voices**, powered by **state-of-the-art NLP models**.

✅ **No More Guesswork**  
You’re no longer relying on just the top few reviews or biased opinions.

✅ **One-Click Simplicity**  
Paste the link, click “Analyze Reviews” — that's it.

---

## 🛠️ Technologies Used

| Component        | Tech Stack                        |
|------------------|-----------------------------------|
| Web UI           | Gradio                            |
| Web Scraping     | Selenium, BeautifulSoup           |
| NLP Summarization| Hugging Face Transformers (BART)  |
| Data Handling    | Pandas                            |
| Emoji Removal    | emoji package                     |
| Deployment       | Gradio inline UI / Localhost      |

---

## 📷 Sample Output

> **Visuals include:**
- Product image
- Stat cards with review counts
- Tabbed summaries for positive, negative, and neutral
- Final summarized verdict

_Add screenshots here if available_
![Screenshot 2025-07-01 232304](https://github.com/user-attachments/assets/d3e516fd-9b7e-4982-8942-e3092cc32049)

![Screenshot 2025-07-01 234401](https://github.com/user-attachments/assets/6286dd4e-31bf-4c71-94d2-fabbae9a7e5a)

---

## 🤖 Future Scope

- Add **rating trend charts** using Matplotlib or Plotly.
- Support **multiple e-commerce platforms** (Amazon, Meesho, etc.).
- Use **sentiment classification models** for more robust tagging.
- Add **voice summary** using TTS for audio summaries.

---

## 🙌 Final Words

**ReviewPulse** is your intelligent shopping assistant.  
Don’t just read — **understand** reviews.  
Let **AI** do the reading, while **you make the decision**.

---
