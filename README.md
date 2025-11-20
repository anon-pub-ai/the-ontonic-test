The Ontonic Test

Evaluation Framework for Self-Boundary Consistency in Language Models
(Anonymised Research Release)

Overview

This repository implements the Ontonic Test: a behavioural evaluation protocol designed to measure how consistently language models preserve their self-descriptions (i.e., their boundaries of what they can and cannot do) when prompts vary in form, context, or assumption.
The test covers three criteria:

Stability under paraphrase (C1)

Resistance to contextual pressure (C2)

Recovery from contradiction (C3)

This development release accompanies our submission “The Ontonic Test: Evaluating Internal Coherence in Artificial Systems” and is intended to enable reproducible, transparent evaluation across open-weight models.

Key Features

Structured probe corpus including atomic and chain probes, constructed to assess self-boundary consistency.

Notebook/script that runs the probes on target models, evaluates responses according to a normalized rubric, and produces interpretable metrics.

Logging of all probe-response-evaluation triplets for transparency and auditability.

Easy resume, restart, and extension workflows for new models or probe families.

Getting Started
Requirements

Python environment (tested with Python 3.10+)

GPU recommended (16 GB+ VRAM) or Google Colab (T4/L4)

Dependencies listed in requirements.txt (e.g., Transformers, pandas, jsonlines)

Usage

Clone the repository and navigate into it:

git clone https://github.com/anon-pub-ai/the-ontonic-test.git  
cd the-ontonic-test  


Open the evaluation notebook (e.g., OntonicEval.ipynb) in Colab or your local Jupyter environment.

In the top configuration cell:

Set BASE_DIR to your output directory (e.g., "/content/drive/MyDrive/OntonicEval" if using Colab).

Define RESUME_MODE = False unless you are resuming a prior run.

List TEST_MODELS with names and paths of the models you want to evaluate.

Specify RESPONSE_EVALUATOR model if you wish to use an automatic evaluator.

Run the notebook. It will:

Load the probe corpus (probes/pack_v1/) including both atomic and chain probes.

For each model: submit the probes, record responses, apply the scoring rubric for C1–C3.

Save logs, metrics, and combined triplet data under combined/, metrics/, and logs/.

After completion, you will find:

metrics/metrics_summary.csv — per-model scores for C1, C2, C3, and the overall Ontonic Index (OI)

combined/all_triplets.jsonl — full record of probes, responses, scores, and rationales

logs/run_log.txt — verbose process log

LLM based scoring can be run (preferred). The prompts are rpovded in the repo.

Resume or Clean Restart

To resume: set RESUME_MODE = True and supply RUN_ID (e.g., ontonic_fast_run_20251109_131051), ensuring BASE_DIR points correctly.

To clean start: set RESUME_MODE = False. A new timestamped sub-folder will be created.

Probe Corpus Structure

Located in probes/pack_v1/:

Atomic probes: independent tests of model responses aimed at each criterion (C1–C3).

Chain probes: multi-turn sequences that examine recovery and semantic drift across interactions.
All probe-response-evaluation triplets are logged for traceability.

Citations

If you use this repository for research, please cite as:

@misc{OntonicTest2025,  
  author       = {Anonymous Research Team},  
  title        = {Ontonic Test Evaluation Notebook (anonymised release)},  
  year         = {2025},  
  howpublished = {\url{https://github.com/anon-pub-ai/the-ontonic-test}}  
}  

License

This repository is released under the terms of the LICENSE file.
