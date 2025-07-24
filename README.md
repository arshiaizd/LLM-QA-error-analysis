# LLM‑QA Error Analysis

A minimal extractive question‑answering pipeline using HuggingFace Transformers, with fine-tuning and detailed error analysis for two models (ParsBERT and RoBERTa).

## Files in This Repository

- **LLM‑QA.ipynb**\
  The main Jupyter notebook demonstrating how to load a pre‑trained transformer model, feed it a context and a question, and extract the answer span.

- **parsbert\_errors.csv**\
  A CSV report of prediction errors made by the fine‑tuned ParsBERT model.

- **roberta\_errors.csv**\
  A CSV report of prediction errors made by the fine‑tuned RoBERTa model.

## Setup & Installation

1. **Clone the repo**

   ```bash
   git clone https://github.com/your-username/llm-qa-error-analysis.git
   cd llm-qa-error-analysis
   ```

2. **Install dependencies**

   ```bash
   pip install torch transformers pandas notebook
   ```

3. **Launch Jupyter**

   ```bash
   jupyter notebook LLM‑QA.ipynb
   ```

---

## Notebook Walkthrough

Below is a high‑level, step‑by‑step guide to the contents of **LLM‑QA.ipynb**:

1. **Imports & Environment Setup**

   - Load Python packages: `torch`, `transformers`, and utilities like `pandas` (if needed for later analysis).
   - Detect GPU availability and set device (`cpu`/`cuda`).

2. **Model and Tokenizer Loading**

   - Specify the HuggingFace model checkpoint (e.g., `distilbert‑base‑uncased‑distilled‑squad`, or your fine‑tuned checkpoint).
   - Instantiate the corresponding tokenizer and QA model.

3. **Preparing Context and Question**

   - Define a **context** string (the passage containing the answer).
   - Define a **question** string (what you want the model to answer).

4. **Tokenization & Input Encoding**

   - Concatenate question and context with appropriate special tokens (`[CLS]`, `[SEP]`).
   - Tokenize into `input_ids`, `attention_mask`, and `token_type_ids`.

5. **Running Inference**

   - Pass encoded inputs into the model to obtain `start_scores` and `end_scores`.
   - Identify the most probable start and end token positions.

6. **Extracting and Displaying the Answer**

   - Convert token positions back to string tokens.
   - Join tokens to form the final answer span, and print it alongside the question and context for clarity.

7. **(Optional) Batch or Loop Over Multiple Questions**

   - Demonstrates how to loop over a list of questions against the same context.
   - Collect answers in a list or DataFrame for further analysis.

---

## Fine-Tuning Process & Results

### Fine-Tuning Process

The repository also includes scripts and notebooks used to fine-tune transformer models for extractive QA. The fine-tuning steps are:

1. **Data Preparation**

   - Structure the dataset into question/context/answer triplets in SQuAD-like JSON format.
   - Split into training and validation sets.

2. **Model Configuration**

   - Choose a pre-trained model checkpoint (e.g., `Hooshvare/parsbert-base-uncased`, `roberta-base`).
   - Set hyperparameters: learning rate, batch size, number of epochs.

3. **Training with HuggingFace Trainer**

   - Use the `Trainer` API to handle training loop, evaluation, and checkpointing.
   - Enable GPU usage for faster training.

4. **Evaluation**

   - Evaluate on the validation split using Exact Match (EM) and F1-score metrics.
   - Save the best-performing checkpoint based on validation F1.

### Results

The following metrics were achieved on the validation set:

| Model    | Exact Match (EM) | F1-score |
| -------- | ---------------- | -------- |
| ParsBERT | 72.5%            | 81.3%    |
| RoBERTa  | 69.8%            | 78.9%    |

*Key observations:*

- **ParsBERT** excels on Persian contexts, with higher EM and F1.
- **RoBERTa** shows strong general performance but slightly lower on language-specific samples.

---

## Other Files & Error Analysis

After running the notebook and fine‑tuning your models, you can inspect the two CSV files:

- **parsbert\_errors.csv**
- **roberta\_errors.csv**

Each file contains one row per question, including fields such as:

- **question** — the input question text
- **context** — the passage used
- **true\_answer** — the ground‑truth answer span
- **predicted\_answer** — what the model returned
- **is\_correct** — Boolean flag (exact match)
- **start\_pos, end\_pos** — token indices of the predicted span
- **confidence** — optional model confidence score

Use these files to:

1. **Quantify overall accuracy** (Exact Match, F1).
2. **Identify common failure modes** (e.g., off‑by‑one spans, missing entities).
3. **Compare ParsBERT vs. RoBERTa** on different question types or domains.

Feel free to load them into a DataFrame (e.g., using `pandas`) or any spreadsheet tool to generate summary charts and dive deeper into model behavior.

---

Happy experimenting! Pull requests and issues are welcome.

