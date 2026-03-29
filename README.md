# AutoEIT – Automated Scoring System

## Overview

This project implements a deterministic, automated scoring system for the Spanish Elicited Imitation Task (EIT). The objective is to replace manual scoring with a consistent, reproducible, and rubric-aligned evaluation process designed for linguistic research.

## Problem

EIT responses are traditionally scored by human raters, which introduces subjective variability, limits scalability, and makes evaluation time-intensive. While generative language models can assist, they are often non-deterministic and fail to distinguish grammatical errors from meaning preservation. This project addresses these limitations by automating scoring based on semantic equivalence.

## Methodology

The system uses a hybrid rule-based and semantic approach aligned with the Ortega (2000) EIT rubric:

* **Text Preprocessing**
  Normalizes text by removing noise (e.g., hesitations, transcription markers) and standardizing accents/diacritics.

* **Idea Unit Analysis**
  Filters Spanish function words to focus on content-bearing words, isolating core idea units.

* **Semantic Similarity**
  Uses a multilingual sentence transformer model (`paraphrase-multilingual-MiniLM-L12-v2`) to compute cosine similarity and capture meaning beyond lexical overlap.

## Scoring Logic (0–4)

The scoring pipeline maps directly to the EIT rubric:

* **4 — Exact Match:** Normalized stimulus and transcription are identical.
* **3 — Meaning Preserved:** High semantic similarity; grammatical or syntactic errors are tolerated.
* **2 — Partial Meaning:** More than 50% of idea units retained, but meaning is inexact.
* **1 — Limited Meaning:** 50% or fewer idea units retained, or meaning is largely unrelated.
* **0 — No Meaningful Response:** Silence, garbled text, or responses with one or fewer content words.

## Tech Stack

* Python 3.8+
* pandas, openpyxl
* sentence-transformers, PyTorch
* matplotlib, seaborn

## Repository Structure

```text
AutoEIT-Scoring-System/
├── notebook/
│   └── AutoEIT_Scoring.ipynb
├── results/
│   ├── Final_AutoEIT_Scored.xlsx
│   └── EIT_Score_Distribution.png
├── AutoEIT_Scoring.pdf
└── README.md
```
