<!--
Project: Advanced NLP Sarcasm & Irony Classification
-->

# Advanced NLP Project

**Sarcasm Detection in News Headlines and Tweets**

This repository contains code and resources for fine-tuning transformer and training Bi-LSTM models to detect sarcasm and irony in short text.

---


## Datasets

* **Sarcasm Headlines Dataset**: Source: [Kaggle Sarcasm Headlines](https://www.kaggle.com/datasets/rmisra/news-headlines-dataset-for-sarcasm-detection)
* **Tweets Dataset**: Source: [Kaggle Tweets with Sarcasm and Irony](https://www.kaggle.com/datasets/nikhiljohnk/tweets-with-sarcasm-and-irony)

---

## Key Features

* **Transformer Fine-Tuning**: BERT (DistilBERT) adapted for binary sarcasm classification.
* **Bidirectional LSTM**: Custom Bi-LSTM architecture trained from scratch on cleaned text.
* **Fast Bi-LSTM**: Lightweight model with mixed-precision (AMP) for rapid hyperparameter sweeps.
* **Cross-Domain Evaluation**: Train on headlines → evaluate on tweets, and vice versa.
* **Hyperparameter Tuning**: Grid search over learning rates, batch sizes, epochs, and sequence lengths.

---

## Performance Metrics

| Model                | Task             | Accuracy | F1 score |
| -------------------- | ---------------- | -------- | -------- |
| **BERT (headlines)** | val on headlines | 0.87     | 0.86     |
| **BERT (tweets)**    | val on tweets    | 0.83     | 0.82     |
| **BERT H→T**         | cross-eval       | 0.79     | 0.78     |
| **BERT T→H**         | cross-eval       | 0.81     | 0.80     |
| **Bi-LSTM**          | val on combined  | 0.75     | 0.74     |
| **Fast Bi-LSTM**     | val on headlines | 0.73     | 0.72     |
| **LSTM H→T**         | cross-eval       | 0.68     | 0.67     |
| **LSTM T→H**         | cross-eval       | 0.70     | 0.69     |

---

## License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.
