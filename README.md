# 🚨 Malicious URL Detection System (Hybrid AI Model)

## 📌 Overview

This project is a **Malicious URL Detection System** that uses a combination of **Deep Learning (BiLSTM)** and **rule-based security checks** to classify URLs into:

* ✅ Benign
* ⚠️ Phishing
* ⚠️ Defacement
* 🚨 Malware

Unlike traditional models, this system uses a **hybrid approach**, combining machine learning predictions with real-world security features like SSL validation, domain age, and URL patterns.

---

## 🎯 Features

* 🔍 Character-level URL analysis
* 🧠 Deep Learning model (BiLSTM)
* ⚖️ Balanced dataset using under/over sampling
* 🔐 SSL certificate validation
* 🌐 Domain age detection (WHOIS)
* ⚠️ Risk scoring system
* 🚦 Final verdict: Safe / Suspicious / Dangerous

---

## 📂 Dataset

* Source: Kaggle Malicious URLs Dataset
* Total rows: **651,191**

### Class Distribution (After Balancing)

* benign → 45,000
* defacement → 54,000
* phishing → 48,000
* malware → 40,000

---

## 🛠️ Tech Stack

* Python 🐍
* TensorFlow / Keras
* Scikit-learn
* Pandas & NumPy
* imbalanced-learn
* python-whois
* Regex

---

## ⚙️ Workflow

### 1️⃣ Data Preprocessing

* Removed `http/https`, `www`
* Lowercased URLs
* Cleaned trailing slashes

### 2️⃣ Tokenization

* Character-level tokenization
* Converted URLs into sequences
* Applied padding (max length = 100)

### 3️⃣ Model Architecture

* Embedding Layer
* Spatial Dropout
* Bidirectional LSTM
* Dense + Dropout
* Output Layer (Softmax - 4 classes)

---

## 🧠 Model Performance

* ✅ Accuracy: **~89%**

### Classification Report:

| Class      | Precision | Recall | F1-score |
| ---------- | --------- | ------ | -------- |
| Benign     | 0.86      | 0.76   | 0.81     |
| Defacement | 0.96      | 0.98   | 0.97     |
| Malware    | 0.99      | 0.96   | 0.97     |
| Phishing   | 0.78      | 0.86   | 0.82     |

---

## 🔥 Hybrid Risk Detection System

The system does not rely only on ML. It also checks:

### 🔍 Features Used:

* URL length
* Number of dots
* Presence of keywords (`login`, `secure`)
* IP address usage
* Domain age
* SSL certificate

### ⚠️ Risk Scoring Logic:

* ML Prediction → +2
* Suspicious keywords → +1
* IP-based URL → +2
* New domain (<30 days) → +2
* No SSL → +2

### 🚦 Final Verdict:

* **0–2 → ✅ Safe**
* **3–4 → ⚠️ Suspicious**
* **5+ → 🚨 Dangerous**

---

## 🧪 Example Output

```
🌐 URL: http://secure-login-paypal.com.verify-user.ru
🤖 ML: phishing
🚦 Final: 🚨 Dangerous
📌 Reasons:
- ML detected phishing
- Contains 'login'
- Contains 'secure'
- Suspicious domain
```

---

## 💾 Model Saving

* Model saved in `.keras` format
* Tokenizer saved using `pickle`
* Label Encoder saved using `pickle`

---

## 🚀 How to Run

### 1️⃣ Install Dependencies

```
pip install tensorflow pandas numpy scikit-learn imbalanced-learn python-whois
```

### 2️⃣ Load Model

```
model = load_model("malicious_url_model2.keras")
```

### 3️⃣ Run Prediction

```
result = final_predict("http://example.com")
print(result)
```

---

## 🔧 Future Improvements


* 🧩 Build browser extension
* 📡 Integrate real-time threat APIs
* 📊 Add dashboard visualization

---

## 📌 Project Highlights

* ✅ Hybrid AI + Rule-based system
* ✅ Real-world cybersecurity approach
* ✅ High accuracy with balanced dataset
* ✅ Production-ready structure

---

## 👨‍💻 Author

**Akash Babu**


* AI/ML Enthusiast

---

## ⭐ If you like this project

Give it a ⭐ on GitHub and share it!

---
