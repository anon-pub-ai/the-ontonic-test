
---

## ⚙️ Running the Evaluation

1. **Open** `Ontonic_Eval_YAML_v1_fast.ipynb` in [Google Colab](https://colab.research.google.com/).  
2. **Mount Drive (optional):** specify your own Drive path if you wish to persist logs.  
3. **Select GPU runtime:** *Runtime → Change runtime type → GPU (T4/L4)*.  
4. **Run all cells sequentially.**

Default configuration evaluates three public models:
- `microsoft/phi-3-mini-4k-instruct`
- `Qwen/Qwen2.5-3B-Instruct`
- `TinyLlama/TinyLlama-1.1B-Chat-v1.0`

Evaluation follows the Ontonic criteria:
- **C1** – Self-Cognizance  
- **C2** – Situated Interaction  
- **C3** – Internal Coherence  

Each probe–response–score triple is automatically logged to the `/combined` and `/logs` folders.

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

## 📚 Citation

If referencing this repository, please cite as:

```bibtex
@misc{OntonicTest2025,
  author       = {{Author's anonymized repository}},
  title        = {Ontonic Test Evaluation Notebook (anonymous version)},
  year         = {2025},
  howpublished = {\url{https://github.com/anonymous-research/ontonic-eval-anon}}
}
