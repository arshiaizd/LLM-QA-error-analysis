# LLM-QA Error Analysis

This repository provides a simple and extensible pipeline for **question answering (QA)** using large language models (LLMs), along with detailed error analysis for multiple transformer models (ParsBERT and RoBERTa). The project demonstrates how to perform extractive question answering with a pre-trained model, and provides tools to analyze and compare model performance.

## Table of Contents

- [Overview](#overview)
- [Files](#files)
- [How to Use](#how-to-use)
- [Error Analysis](#error-analysis)
- [Dependencies](#dependencies)
- [License](#license)
- [Acknowledgements](#acknowledgements)

## Overview

This repository includes:
- A Jupyter notebook (`LLM-QA.ipynb`) that demonstrates how to use a pre-trained transformer-based language model to perform extractive question answering on custom contexts.
- Error analysis CSV files for ParsBERT and RoBERTa models, enabling users to inspect and compare model mistakes.

The project is useful for anyone interested in natural language processing, question answering, or benchmarking transformer models on QA tasks.

## Files

- **LLM-QA.ipynb**: Main notebook demonstrating QA using HuggingFace transformers.
- **parsbert_errors.csv**: Error analysis results for the ParsBERT model.
- **roberta_errors.csv**: Error analysis results for the RoBERTa model.

## How to Use

1. **Clone the Repository**

    ```bash
    git clone https://github.com/your-username/llm-qa-error-analysis.git
    cd llm-qa-error-analysis
    ```

2. **Install Dependencies**

    Install Python dependencies (see [Dependencies](#dependencies)):

    ```bash
    pip install -r requirements.txt
    ```

    *(If `requirements.txt` is missing, main requirements are: `torch`, `transformers`, `pandas`, and `notebook`.)*

3. **Run the Notebook**

    Open the Jupyter notebook:

    ```bash
    jupyter notebook LLM-QA.ipynb
    ```

4. **Explore Error Analysis**

    Use any spreadsheet or data analysis tool (e.g., pandas, Excel) to explore `parsbert_errors.csv` and `roberta_errors.csv`.

## Error Analysis

The error CSV files contain model predictions and errors for QA tasks on a benchmark dataset. Each row typically includes:

- **Question**: The input question.
- **Context**: The passage/context where the answer is found.
- **True Answer**: The correct answer span.
- **Predicted Answer**: The model's predicted span.
- **Is Correct**: Whether the prediction matches the ground truth.
- **Other metrics**: (e.g., start/end positions, confidence, etc.)

You can use these files to:
- Analyze common failure modes.
- Compare model performance.
- Visualize results (accuracy, F1, error types).

## Dependencies

Main libraries used:

- [PyTorch](https://pytorch.org/)
- [Transformers (HuggingFace)](https://huggingface.co/transformers/)
- [Pandas](https://pandas.pydata.org/)
- [Jupyter Notebook](https://jupyter.org/)

Install via:

```bash
pip install torch transformers pandas notebook
