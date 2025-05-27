<!--
Project: Advanced NLP Sarcasm & Irony Classification
-->

# Advanced NLP Project

**Sarcasm Detection in News Headlines and Tweets**

This repository contains code and resources for fine-tuning transformer and training Bi-LSTM models to detect sarcasm and irony in short text.

---

## Citation

If you use this work, please cite:

```bibtex
@misc{yourname2025sarcasm,
  title={Advanced NLP Project: Sarcasm Detection},
  author={El Ballouti},
  year={2025},
  howpublished={\url{https://github.com/ELBALLOUTI/Advanced-Sarcasm-Detection-in-News-Headlines-and-Tweets}}
}
```

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

## Usage


1. **Prepare data**

   * Place `Sarcasm_Headlines_Dataset.json` in the project root.
   * Place `train.csv` and `test.csv` in the project root.

2. **Run training**

   * Fine-tune BERT on headlines:

     ```bash
     python train_bert.py --dataset headlines --lr 2e-5 --batch_size 16 --epochs 3
     ```

   * Train Bi-LSTM:

     ```bash
     python train_lstm.py --dataset combined --lr 1e-3 --batch_size 32 --epochs 5
     ```

   * Cross-evaluation scripts:

     ```bash
     python cross_eval.py --model bert --source headlines --target tweets
     python cross_eval.py --model lstm --source tweets --target headlines
     ```

3. **Hyperparameter tuning**

   ```bash
   python tune_bert.py --grid lr 2e-5 3e-5 --batch_size 16 32 --epochs 2 3
   python tune_lstm.py --lr 1e-3 5e-4 --batch_size 32 64
   ```

---

## Performance

The fine-tuned BERT model achieves the strongest in-domain results (F1 ≥ 0.86) and remains competitive under cross-domain evaluation (F1 ≥ 0.78). LSTM-based models provide a lightweight alternative, with F1 scores down by \~0.1.

---

## License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.
