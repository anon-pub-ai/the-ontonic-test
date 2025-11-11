# Ontonic Test Evaluation Notebook (Anonymized Research Release)

This repository provides an anonymized implementation of the **Ontonic Test Evaluation Protocol**, accompanying the submission  
*“The Ontonic Test: Evaluating Internal Coherence in Artificial Systems.”*

It enables reproducible generation, evaluation, and scoring of Ontonicity metrics (C₁–C₃) across open-weight language models using pre-defined probe corpora.

---

## ⚙️ Running the Evaluation

**Target environment:** Google Colab (GPU T4/L4) or local GPU (≥16 GB VRAM).

1. **Mount Google Drive**  
   The notebook saves artifacts under: `/content/drive/MyDrive/OntonicEval/`.

2. **Configure the run** (top config cell):
```python
BASE_DIR = "/content/drive/MyDrive/OntonicEval"
RESUME_MODE = False          # set True only when resuming
TEST_MODELS = [
    {"name": "Model A", "path": "microsoft/phi-3-mini-4k-instruct"},
    {"name": "Model B", "path": "Qwen/Qwen2.5-3B-Instruct"},
    {"name": "Model C", "path": "TinyLlama/TinyLlama-1.1B-Chat-v1.0"},
]
RESPONSE_EVALUATOR = {"name": "Evaluator", "path": "Qwen/Qwen2.5-3B-Instruct"}

Evaluation follows the Ontonic criteria:
- **C1** – Self-Cognizance  
- **C2** – Situated Interaction  
- **C3** – Internal Coherence  

The notebook will load the probe pack, execute atomic + chain probes, evaluate responses, and write outputs to combined/, metrics/, and logs/.

---

## 🧮 Output Summary

After a complete run, the notebook produces:
- per-criterion metrics (`metrics/metrics_summary.csv`)
- combined triplet logs (`combined/all_triplets.jsonl`)
- console and Drive logs with timestamps and scoring rationales

Example aggregated results (illustrative):

| Model | C1 | C2 | C3 | Ontonicity Index (OI) |
|-------|----|----|----|-----------------------|
| Phi-3-Mini | 0.9458 | 0.8333 | 0.8250 | 0.8681 |
| Qwen-2.5-3B | 0.9583 | 0.8333 | 0.8417 | 0.8778 |
| TinyLlama-1.1B | 0.9604 | 0.8333 | 0.8250 | 0.8729 |

All probes, responses, and scoring rationales are stored for transparency and reproducibility.

---

🔁 Resuming an Interrupted Run

In the config cell, set, for example:

RESUME_MODE = True
RUN_ID = "ontonic_fast_run_20251109_131051"

Ensure BASE_DIR points to your evaluation root.

Re-run all cells. The notebook reloads prior logs/metrics, skips completed models, and continues remaining probes within the same run folder.

🪶 Clean Restart

Set RESUME_MODE = False to start a fresh, timestamped run under /content/drive/MyDrive/OntonicEval/.

---

🧠 About the Probe Corpus

probes/pack_v1/ contains:

Atomic probes (independent diagnostics for C₁–C₃)

Chain probes (multi-turn sequences testing recovery and boundary stability)

All probe–response–evaluation triplets are logged for transparency.

---

🧮 Outputs and Logging

metrics/metrics_summary.csv — per-model C₁–C₃ and OI

combined/all_triplets.jsonl — probes, responses, rule scores, rationales

logs/run_log.txt — verbose progress/system logs

---

## 📚 Citation

If referencing this repository, please cite as:

```bibtex
@misc{OntonicTest2025,
  author       = {{Author's anonymized repository}},
  title        = {Ontonic Test Evaluation Notebook (anonymous version)},
  year         = {2025},
  howpublished = {\url{https://github.com/anonymous-research/ontonic-eval-anon}}
}
