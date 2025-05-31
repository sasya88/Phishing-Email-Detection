# 📧 Phishing Email Detection Using Persuasion Cues

## Overview

**Phishing** is a form of social engineering in which attackers deceive unsuspecting victims into revealing sensitive information. These deceptive emails often imitate legitimate organizations and use psychological manipulation to trick users into clicking malicious links or downloading harmful attachments.

This project explores the **persuasion tactics** commonly used in phishing emails and presents a **machine learning-based system** that not only detects phishing but also helps explain:

> 🧐 *Why* is this email classified as phishing?

Inspired by the research paper:  
**“Phishing Email Detection Using Persuasion Cues”**,  
the project emphasizes analyzing **persuasion strategies** — such as *urgency, authority, and gain/loss framing* — to enhance phishing detection accuracy and interpretability.

---

## Problem Statement

Traditional phishing detection systems often act as black boxes — they may flag an email as phishing but don’t provide reasons for their decisions. As phishing attacks evolve, attackers use more sophisticated **persuasion techniques** that closely mimic authentic communication.

This project aims to solve two key problems:

1. Develop an interpretable phishing detection model using **persuasion cues**.
2. Evaluate and compare the performance of traditional models **with** and **without** persuasion-based features.

---

## Dataset

- **Total Emails**: 37,055
- **Source**: [Kaggle - Phishing Emails Dataset](https://www.kaggle.com/datasets/subhajournal/phishingemails)
- Each email was analyzed based on:
  - Email content (subject + body)
  - Psychological cues: **gain**, **loss**, **urgency**, **authority**, etc.

---

## Data Preprocessing

Raw email data is typically noisy — with forwarded threads, emojis, headers, and typos. We applied the following preprocessing steps:

1. **Text Cleaning**: Removed duplicates and unnecessary characters.
2. **Text Preparation**:
   - Tokenized text using **NLTK**
   - Removed stop words and special characters (e.g., `@`, `#`)
3. **Text Refinement**:
   - Converted all text to lowercase
   - Applied **stemming** to normalize word forms (e.g., “retrieved” → “retrieve”)

---

## Persuasion Cue Detection

To recognize **persuasion tactics**, a **Bi-directional Long Short-Term Memory (Bi-LSTM)** model was trained on a subset of human-labeled emails. This model was then used to generate **persuasion labels (gain/loss framing)** for the entire dataset.

- **Model**: Bi-LSTM
- **Objective**: Predict persuasive framing (*gain* or *loss*) based on email content

This allowed our system to infer the **intent** behind phishing attempts, beyond just textual features.

---

## Feature Extraction

We used **Word2Vec (W2V)** embeddings to convert textual content into meaningful vector representations that captured the **semantic context** of words and phrases.

This approach enabled deeper understanding of the content, especially the persuasive language patterns.

---

## Models Implemented

We implemented and compared multiple machine learning models:

- **Naïve Bayes**
- **Logistic Regression**
- **Support Vector Machine (SVM)**
- **Random Forest**

Each model was trained twice:
- **Without** persuasion labels (baseline)
- **With** persuasion labels (enhanced)

---

## Evaluation Metrics

We evaluated the models using the following metrics:

- **Accuracy**
- **Precision**
- **Recall**
- **F1 Score**

---

## Results

- **Best Accuracy**: ~95% using **Random Forest** with persuasion features
- **False negatives** were significantly reduced when persuasion cues were included
- Models trained with persuasion labels were **more interpretable** and **more effective**


---

## Key Insights

- **Phishing emails often rely on emotional triggers**: 
  - *Gain* (reward)
  - *Loss* (threat)
  - *Urgency* (“act now”)
  - *Authority* (“from your bank”)

- **Detection of these cues makes model predictions more explainable** and improves user awareness.

- The combination of **Bi-LSTM** (for cue detection), **Word2Vec** (for semantic features), and **traditional ML models** provides a strong pipeline for phishing detection.

---

## 🚀 Future Work

- Build a **real-time phishing email filter** or **browser extension**
- Expand persuasion cue categories (e.g., *scarcity*, *social proof*)
- Integrate **explainable AI tools** (e.g., SHAP, LIME) for better transparency
- Explore **transformer-based models** like **BERT** for deeper language understanding


