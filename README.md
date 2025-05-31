# 📧 Phishing Email Detection Using Persuasion Cues

## 🧠 Overview

Phishing is more than just bad spelling or suspicious links — it’s **psychological manipulation**. Cybercriminals carefully craft emails to **trick, scare, or entice** users into clicking links, revealing credentials, or downloading malware. 

This project dives into the **psychological tactics** behind phishing and builds a **machine learning-based system** that not only detects phishing emails, but also helps answer the question:

> 🧐 *Why* is this email phishing?

Inspired by the research paper:  
**“Phishing Email Detection Using Persuasion Cues”**,  
this project focuses on analyzing **persuasion strategies** — such as *urgency, authority, gain/loss framing* — to improve phishing detection performance and interpretability.

---

## 🎯 Problem Statement

Traditional phishing detection models are often black boxes — they label an email as phishing, but don't explain why. Meanwhile, attackers are getting smarter, employing **persuasion tactics** to mimic legitimate emails and emotionally manipulate users.

**This project addresses two key goals:**
1. Build interpretable phishing email detection using *persuasion cues*.
2. Compare traditional models with persuasion-aware models to evaluate impact.

---

## 🗃 Dataset

- Total Emails: **37,055**
- Collected from a variety of corporate and phishing sources.
- Each email analyzed for:
  - Content (subject, body)
  - Persuasion cues: **gain**, **loss**, **urgency**, **authority**, etc.

---

## 🧼 Data Preprocessing

Email content is messy — think forwards, duplicates, headers, emojis, and typos. We cleaned and prepped the data in 3 stages:

1. **Text Cleaning**: Removed duplicates and non-useful characters.
2. **Text Preparation**:
   - Tokenized using **NLTK**
   - Removed stop words, special symbols (`@`, `#`, etc.)
3. **Text Refinement**:
   - Converted to lowercase
   - **Stemming** to reduce words to base forms (e.g., *retrieved* → *retrieve*)

---

## 🧠 Persuasion Cue Detection

To identify **persuasion tactics**, we trained a **Bi-directional LSTM (Bi-LSTM)** model on a pilot set of human-annotated emails. This model was then used to generate **persuasion labels (gain/loss)** for the entire dataset.

- **Model Used**: Bi-LSTM
- **Purpose**: Predict *gain* or *loss* framing from email content

This gave our system the ability to see the **intent** behind a phishing email — not just its structure.

---

## 💡 Feature Extraction

We used **Word2Vec (W2V)** to transform email text into vector representations that captured semantic meaning.

This helped capture deeper patterns and persuasion context in the text beyond simple bag-of-words models.

---

## 🛠 Models Implemented

We trained and evaluated the following ML classifiers:

- **Naïve Bayes**
- **Logistic Regression**
- **Support Vector Machine (SVM)**
- **Random Forest**

Each model was trained **with** and **without** persuasion cue labels for comparison.

---

## 📊 Evaluation Metrics

To evaluate performance, we used:

- **Accuracy**
- **Precision**
- **Recall**
- **F1 Score**

---

## 🧪 Results & Comparison

| Model                | Without Persuasion Cues | With Persuasion Cues |
|---------------------|-------------------------|-----------------------|
| Naïve Bayes         | Lower accuracy          | ↑ Higher accuracy     |
| Logistic Regression | Moderate                | ↑ Improved            |
| Random Forest       | Strong                  | ↑ Stronger            |
| SVM                 | Moderate                | ↑ Improved            |

> ✅ **Best Performance:** ~95% accuracy with persuasion-aware Random Forest

Incorporating **persuasion cues improved both accuracy and interpretability**, making the model’s predictions more explainable.

---

## 🔍 Key Insights

- **Phishing emails often use emotional manipulation**: gain (rewards), loss (threats), urgency (“act now”), or authority (“your bank”).
- **Detecting these cues helps explain predictions**, improving user trust and cybersecurity training tools.
- **Bi-LSTM + Word2Vec + traditional ML classifiers** is a powerful combo for phishing detection.

---

## 🚀 Next Steps

- Integrate the model into a **real-time email filter or browser extension**.
- Expand persuasion categories (e.g., scarcity, social proof).
- Add more layers of interpretability (e.g., SHAP or LIME explanations).
- Use **transfer learning** with models like BERT for even better results.

---

## 🧑‍💻 How to Run

```bash
# Clone the repository
git clone https://github.com/yourusername/phishing-detection-persuasive
cd phishing-detection-persuasive

# Install dependencies
pip install -r requirements.txt

# Run preprocessing and training
python preprocess.py
python train_models.py
