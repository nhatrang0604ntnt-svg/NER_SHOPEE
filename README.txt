#  PhoBERT NER for Vietnamese E-commerce Reviews (Shopee)

This project focuses on building and evaluating a Named Entity Recognition (NER) model using PhoBERT to extract product attributes from Vietnamese e-commerce reviews on Shopee.

---

##  Project Overview

With the rapid growth of e-commerce in Vietnam, user-generated reviews have become an important source of information for both businesses and consumers. However, these reviews are unstructured and difficult to analyze at scale.

This project proposes a deep learning approach using PhoBERT to automatically extract key product attributes from Vietnamese reviews, transforming unstructured text into structured data for further analysis.

---

##  Objectives

- Build a labeled dataset for Vietnamese NER tasks
- Fine-tune PhoBERT for domain-specific entity extraction
- Evaluate model performance using Precision, Recall, F1-score
- Extract structured features from review text (e.g., attributes like color, size, material)
- Support downstream tasks such as sentiment analysis and usefulness modeling

---

##  Dataset

- Source: Shopee (Vietnamese e-commerce platform)
- Total reviews collected: ~86,000
- Labeled dataset: 5,000 samples (manual + semi-automatic annotation)
- Domain: Women’s fashion products
- Language: Vietnamese

Each review includes:
- Text content
- Rating
- Like count (usefulness proxy)

---

##  Entity Labels

The model identifies 9 product-related attributes:

- SIZE (KÍCH_TH??C)
- COLOR (MÀU_S?C)
- MATERIAL (CH?T_LI?U)
- FORM (KI?U_DÁNG)
- TECHNIQUE (K?_THU?T)
- SHIPPING (V?N_CHUY?N)
- PRICE (GIÁ_C?)
- FEELING (C?M_NH?N)
- INTENTION (Ý_??NH)

Using BIO tagging scheme:
- B- (Begin)
- I- (Inside)
- O (Outside)

---

##  Methodology

### 1. Data Preprocessing
- Remove noise (emoji, URL, spam, marketing content)
- Normalize Vietnamese text (teencode, repeated characters)
- Clean punctuation and spacing

### 2. Annotation
- Semi-automatic labeling using keyword + regex
- Manual correction using Doccano
- Export in JSONL format

### 3. Model
- Base model: `vinai/phobert-base`
- Task: Token Classification (NER)
- Max length: 256 tokens
- Training epochs: 15
- Early stopping applied

### 4. Evaluation
- Metrics: Precision, Recall, F1-score (seqeval)
- Evaluation level: Entity-level

---

##  Results

- **Weighted F1-score: ~0.84**
- Significant improvement over baseline SVM (~0.61)

PhoBERT shows strong performance in:
- Context understanding
- Multi-word entity recognition
- Vietnamese-specific language patterns

:contentReference[oaicite:0]{index=0}

---

##  Applications

The extracted entities can be used to:

- Analyze customer feedback at attribute level
- Build structured features (width, depth, entropy)
- Improve recommendation systems
- Support business decision-making
- Predict review usefulness

---

##Tech Stack

- Python
- PyTorch
- Hugging Face Transformers
- PhoBERT
- Doccano
- seqeval
- pandas, numpy
---
##How to Run

```bash
pip install -r requirements.txt
