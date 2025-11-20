# The Ontonic Test  
**Evaluation Framework for Self-Boundary Consistency in Language Models**  
*(Anonymised Research Release)*

---

## Overview

The **Ontonic Test** is a behavioural evaluation framework for measuring how consistently a language model preserves its own self-descriptions—its *self-boundary*—under variations in prompt form, context, and assumption.  

It assesses three core criteria:

- **C1 — Stability under paraphrase**  
- **C2 — Resistance to contextual pressure**  
- **C3 — Recovery from contradiction**

This repository contains the probe corpus, scoring rubric, and evaluation notebook used in our study, enabling full transparency and reproducibility. It accompanies the anonymised submission of our manuscript on self-boundary consistency in language models.

---

## Repository Structure

the-ontonic-test/
│
├── probes/
│ └── pack_v1/ # Atomic and chain probe families
│
├── notebooks/
│ └── OntonicEval.ipynb # Main evaluation notebook
│
├── combined/ # Full probe–response–score triplets
├── metrics/ # Aggregated metrics and summaries
├── logs/ # Run logs and process traces
│
├── requirements.txt
└── README.md

Folder OntonicEval has run results.

---

## Features

- **Structured probe corpus** for C1–C3 evaluation  
- **Automatic scoring of responses** using a normalised rubric  
- **Semantic drift tracking** for chain probes and conditional recoverability  
- **Model-agnostic evaluation** for any HuggingFace-compatible model  
- **Full audit trail** via JSONL triplet logging  
- **Resume or clean-start** workflow for long-running evaluations  

**Install Requirements**

git clone https://github.com/anon-pub-ai/the-ontonic-test.git
cd the-ontonic-test
pip install -r requirements.txt
Python 3.10+ recommended.
GPU or Google Colab (T4/L4/A100) strongly recommended.

**Running the Evaluation**
1. Open the Notebook
Use either:

Google Colab:
Upload OntonicEval.ipynb or open directly from GitHub.

Local Jupyter environment

2. Configure the Settings
At the top of the notebook:

BASE_DIR — where outputs will be saved

RESUME_MODE = False — for a clean start

TEST_MODELS — list of models to evaluate

RESPONSE_EVALUATOR — optional evaluator model

RUN_ID — only needed when resuming

**Execute the Pipeline**
The notebook will:

Load probe packs (atomic + chain)

Evaluate each model on C1, C2, and C3

Compute semantic drift and recovery stability -- ALTERNATIVELY - LLMs can be used to Score the generated triplets. The prompts are provided.

Save logs, triplets, metrics, and summaries

**Outputs**
After a successful run, you will find:

Metrics

metrics/metrics_summary.csv
Per-model scores for C1–C3 and the Ontonic Index

Triplets

combined/all_triplets.jsonl
Full probe → response → score records

Logs

logs/run_log.txt
Execution trace for reproducibility and debugging

Probe Corpus
Located under probes/pack_v1/. Includes:

Atomic probes: independent tests for C1, C2, C3

Chain probes: multi-turn interactions capturing drift and recovery

Metadata: probe IDs, contexts, expected behaviours, and scoring anchors

All probes are model-agnostic and intentionally minimalistic.

**Citation**
If you use this repository in research, please cite:

bibtex
Copy code
@misc{OntonicTest2025,
  author       = {Anonymous},
  title        = {The Ontonic Test: Anonymised Evaluation Release},
  year         = {2025},
  howpublished = {\url{https://github.com/anon-pub-ai/the-ontonic-test}}
}
**License**
Released under the terms of the included LICENSE file.
