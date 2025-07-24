## Fine-Tuning and Results

### Fine-Tuning Approach

In this project, transformer-based models (such as ParsBERT and RoBERTa) were fine-tuned for the extractive question answering task using a custom dataset. The fine-tuning process involved:

- Formatting the data into question/context/answer triplets.
- Using HuggingFace's `Trainer` and `transformers` library to train the models on the QA dataset.
- Evaluating model performance on a held-out validation set.

Hyperparameters (such as learning rate, batch size, and number of epochs) were optimized for best validation performance. Training was performed using GPU acceleration for faster convergence.

### Results

Below is a summary of the performance of both models on the validation set. Results include standard metrics such as **Exact Match (EM)** and **F1-score**.

<div align="center">

<!-- Upload your result image (e.g., metrics.png, results_chart.png) and update the filename below -->
<img src="results.png" alt="Fine-tuning Results" width="600"/>

</div>

**Key observations:**
- **ParsBERT** performed better on Persian contexts, achieving higher EM and F1 on Persian QA samples.
- **RoBERTa** demonstrated robust performance across diverse contexts but showed slightly lower scores on language-specific samples.
- The error analysis CSVs provide detailed breakdowns of each model’s failure cases.

---

*For a detailed breakdown, see the error analysis files: `parsbert_errors.csv` and `roberta_errors.csv`.*

