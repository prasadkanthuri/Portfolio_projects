# 🛍️ ReviewPulse – A DL-Powered Flipkart Review Analyzer

> **“Don’t read hundreds of reviews — understand them in minutes with DL transformers.”**

---
![Screenshot 2025-07-02 104957](https://github.com/user-attachments/assets/9e9ab09c-5d03-4f4c-a35b-767d06b48253)


## 💡 Idea & Motivation

When shopping online, it's common to waste **10–20 minutes** reading user reviews to decide whether a product is worth it.

- You manually skim through 50–100 reviews.
- You may miss key complaints or praises.
- It’s time-consuming and not scalable for smart shopping.

**ReviewPulse** aims to solve this using **automation + deep learning**.

---

## 🚀 What It Does

- Scrapes up to **200 latest reviews** from any Flipkart product.
- Uses **BART Transformer model** to summarize reviews by sentiment:
  - 🟢 Positive  
  - 🔴 Negative  
  - 🟡 Neutral
- Calculates **cosine similarity** between:
  - Each sentiment’s original reviews and their summary.
  - Helps evaluate **summary quality**.
- Gives a **final summary verdict** using all sentiments.

---

## ⚙️ How It Works

### 🔗 Step 1: URL Input
You paste any valid **Flipkart product URL**.

### 🤖 Step 2: Review Scraping
- Extracts `product ID` and forms review page link.
- Uses **Selenium** to:
  - Launch a headless browser.
  - Sort by **Most Recent**.
  - Collect up to **200 reviews** across multiple pages.

### 🧼 Step 3: Data Cleaning
- Extracts:
  - Review Title  
  - Full Review Content  
  - Rating (1–5 stars)
- Removes **emojis** using the `emoji` Python package.

### 🏷️ Step 4: Sentiment Classification
- **4–5 stars** → Positive  
- **1–2 stars** → Negative  
- **3 stars** → Neutral

### 🧠 Step 5: Summarization using Transformers
- Uses **Facebook’s BART Large CNN model**:
  - Summarizes each group (positive/negative/neutral) separately.
  - Then combines all three summaries to generate the **final verdict**.

### 📐 Step 6: Summary Evaluation
- Uses **TF-IDF + Cosine Similarity** to compare:
  - Original reviews (per sentiment)  
  - ⬄  
  - Summarized output
- Helps quantify how much the summary reflects the full data.

### 🖼️ Step 7: Visual Output
![Screenshot 2025-07-02 102639](https://github.com/user-attachments/assets/8a2ab4fc-53fa-4f3e-81f5-3ec97aa72ed2)

Built using **Gradio** with custom CSS:
- 📷 Product Image
- 📊 Review Stats:
  - Total count  
  - Avg rating  
  - # of Positive / Negative / Neutral reviews
- 📈 Cosine Similarity (for each sentiment)
- 📚 Summary Tabs for each sentiment
- 🧠 Final Verdict (combined summarization)

  

---

## 📦 Why 200 Reviews?

- Balances **speed and quality**:  
  Too many reviews = slower response, more repetition.  
  200 offers a **representative snapshot**.
- For most products, recent 200 reviews are enough to:
  - Catch common issues  
  - Understand general sentiment

---

## 🧪 Cosine Similarity Use

Cosine Similarity is computed between:
- All positive reviews ↔️ their summary  
- All negative reviews ↔️ their summary  
- All neutral reviews ↔️ their summary  

> **Higher the score (closer to 1), better the summary coverage.**

---

## 🖥️ Technologies Used

| Purpose                | Library / Tool                         |
|------------------------|----------------------------------------|
| Web Scraping           | `Selenium`, `BeautifulSoup`            |
| Text Preprocessing     | `emoji`, `pandas`                      |
| NLP Summarization      | `transformers` (`facebook/bart-large-cnn`) |
| Similarity Evaluation  | `scikit-learn` (`TfidfVectorizer`, `cosine_similarity`) |
| UI / Deployment        | `Gradio`                               |

---

## ⚙️ How to Run

1. Install dependencies:

```bash
pip install gradio selenium beautifulsoup4 transformers emoji pandas scikit-learn
