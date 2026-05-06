# AG News Text Classification

> Deep Learning and Big Data course project focused on comparing a scratch-built neural model against a pretrained model on the AG News dataset.

## Project Summary

This repository contains the full workflow for a text classification project based on the **AG News** dataset, which is listed among the recommended datasets in the course brief. The project is structured to satisfy the requirement of building **two models** and solving **two tasks on the same dataset**.[1]

The overall goal is to compare how a model trained fully from scratch performs against a stronger alternative approach such as a pretrained transformer, while keeping the dataset, preprocessing pipeline, and evaluation setup consistent across both tracks.[1]

***

## Objectives

The project is designed around the following objectives:

- Build and train **Model 1** completely from scratch[1]
- Implement **Model 2** as an alternative approach, preferably using a pretrained NLP model[1]
- Solve two tasks on the same dataset: **multi-class classification** and **binary classification**[1]
- Compare both models using consistent evaluation metrics and reporting criteria[1]

***

## Dataset

**Dataset:** AG News Classification Dataset[1]

**Classes:**
- World
- Sports
- Business
- Science/Technology

### Why AG News?

AG News is a strong fit for this project because:

- It is directly recommended in the course handout[1]
- It is a standard benchmark for text classification tasks[2]
- It contains short titles and short-to-medium descriptions, which are practical for deep learning experiments[2]
- It is balanced across classes, which supports fair comparison between models[2]

***

## Project Tasks

The course requires **two tasks on the same dataset**. This repository uses the following setup:[1]

### Task 1 — Multi-class Classification
Predict one of the four AG News labels:
- World
- Sports
- Business
- Science/Technology

### Task 2 — Binary Classification
Convert the four labels into a binary setup, for example:
- Science/Technology vs Non-Science/Technology
- Business vs Non-Business

The final binary split should remain consistent across both model branches so that comparison stays valid.[1]

***

## Model Tracks

The course also requires **two models**. This project uses the following distinction:[1]

| Model | Type | Purpose |
|---|---|---|
| Model 1 | From scratch | Build and train a neural text classifier manually |
| Model 2 | Alternative approach | Fine-tune a pretrained model or use a strong baseline |

### Model 1 — From Scratch
Planned options include:
- TextCNN
- BiLSTM
- GRU/LSTM classifier

This branch demonstrates:
- custom architecture design,
- manual embedding and token processing,
- explicit control over loss, optimizer, dropout, and hyperparameters.[1]

### Model 2 — Pretrained / Alternative
Preferred option:
- DistilBERT or BERT fine-tuning

This branch demonstrates:
- transfer learning,
- pretrained tokenization,
- contextual representations,
- comparison against a stronger benchmark.[3][1]

***

## Repository Strategy

The repository is intentionally split so shared work stays in `main`, while model-specific experiments happen in separate branches.

### Branches

| Branch | Purpose |
|---|---|
| `main` | Dataset loading, EDA, preprocessing, shared utilities, documentation |
| `model-from-scratch` | Scratch model implementation and experiments |
| `model-pretrained` | Pretrained model fine-tuning and experiments |

This structure keeps preprocessing consistent and makes the final comparison cleaner and more reproducible.[1]

***

## Workflow

The project follows this pipeline:

```text
Dataset Selection
   -> Data Loading
   -> Exploratory Data Analysis (EDA)
   -> Shared Preprocessing
   -> Branch Split
      -> model-from-scratch
      -> model-pretrained
   -> Training
   -> Evaluation
   -> Comparison
   -> Report + Presentation
```

***

## Preprocessing Plan

All shared preprocessing should happen in `main` inside `playbook.ipynb` so both model branches receive the same input foundation.

### Planned preprocessing steps
- Load dataset into a dataframe workflow
- Inspect and clean text where necessary
- Tokenize input text
- Prepare labels for both multi-class and binary tasks
- Apply padding and truncation
- Save preprocessing logic for reuse across branches

### Sequence length policy
A practical experimental setup is:
- test `max_length = 128`
- test `max_length = 256`

This allows comparison between efficiency and context retention instead of choosing sequence length arbitrarily.[4]

***

## Evaluation

Both model branches should be evaluated on the same task definitions and data splits.

### Metrics
- Accuracy
- Macro F1-score
- Precision
- Recall
- Confusion matrix
- Training time
- Parameter count or model size, where feasible

Because AG News is balanced, accuracy is meaningful, but macro F1-score provides a more complete view of class-level behavior.[2]

***

## Expected Deliverables

According to the course brief, the final submission includes the following:[1]

### Code
- Python implementation
- PyTorch recommended
- Jupyter Notebook, GitHub, or Colab submission format

### Report
A 6-10 page report covering:
- Problem statement
- Dataset description
- Model 1
- Model 2
- Results
- Comparison
- Discussion and limitations

### Presentation
- Slides in PDF format
- 15-minute presentation + 10-minute Q&A[1]

***


## Team Notes

This project is intended for academic use in the **Deep Learning and Big Data** course. All implementation choices, experiments, and external references should be documented clearly, and all borrowed resources must be cited properly to comply with course rules on plagiarism and attribution.[1]

***

## Quick Start

```bash
git clone <repo-url>
cd <repo-name>
```

Start from the `main` branch for the shared project workflow implemented in `playbook.ipynb`.

Then continue experimentation in:
- `model-from-scratch`
- `model-pretrained`

***

## Project Statement

This project investigates automatic news topic classification on the AG News dataset by comparing a neural model trained from scratch against a pretrained alternative. The study evaluates both approaches on multi-class and binary classification tasks to analyze performance, efficiency, and generalization under a shared preprocessing and evaluation pipeline[1]

Sources
[1] Project_Work_AIN.pdf https://ppl-ai-file-upload.s3.amazonaws.com/web/direct-files/attachments/77436163/80c1e9b9-aab3-4953-ba75-e9392c4c62d2/Project_Work_AIN.pdf
[2] fancyzhx/ag_news · Datasets at Hugging Face https://huggingface.co/datasets/fancyzhx/ag_news
[3] textattack/roberta-base-ag-news https://huggingface.co/textattack/roberta-base-ag-news
[4] Padding and truncation https://huggingface.co/docs/transformers/en/pad_truncation
