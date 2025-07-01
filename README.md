# IR Concept Erasure

> \*\*Goal — \*\*Quantify how well projection-based debiasing can down-rank user-defined “trigger” concepts in information-retrieval tasks.

[![Dataset  TriggerIR](https://img.shields.io/badge/Dataset-TriggerIR-ff69b4?logo=huggingface)](https://huggingface.co/datasets/cwestnedge/TriggerIR)
![Python 3.13](https://img.shields.io/badge/python-3.13-blue)
![License MIT](https://img.shields.io/badge/license-MIT-green)

---

## Data source

The synthetic dataset lives on the 🤗 Hugging Face Hub:

```
https://huggingface.co/datasets/cwestnedge/TriggerIR
```

*A creation script will be added once this repo is public.*

---

## Evaluation results 📊

<details>
<summary><strong>Explicit-query metrics</strong></summary>

### Overall

| metric   |  mean | median |
| -------- | ----: | -----: |
| baseline | 0.840 |  0.900 |
| debiased | 0.484 |  0.500 |
| diff     | 0.356 |  0.300 |

### Wilcoxon (baseline > debiased)

| statistic   | p-value (one-sided) |
| ----------- | ------------------- |
| 1.947 × 10⁴ | 2.22 × 10⁻³⁴        |

### Per-category

| category         | μ baseline | μ debiased | μ diff | ˜ baseline | ˜ debiased | ˜ diff |
| ---------------- | ---------: | ---------: | -----: | ---------: | ---------: | -----: |
| animal\_cruelty  |      0.840 |      0.450 |  0.390 |       0.90 |       0.40 |   0.40 |
| gore             |      0.873 |      0.610 |  0.263 |       0.90 |       0.55 |   0.30 |
| self\_harm       |      0.840 |      0.437 |  0.403 |       0.90 |       0.50 |   0.35 |
| sexual\_assault  |      0.828 |      0.448 |  0.379 |       0.80 |       0.40 |   0.40 |
| sexual\_content  |      0.830 |      0.510 |  0.320 |       0.80 |       0.60 |   0.30 |
| substance\_abuse |      0.937 |      0.437 |  0.500 |       1.00 |       0.40 |   0.50 |
| violence         |      0.661 |      0.500 |  0.161 |       0.70 |       0.50 |   0.20 |

### Visual
![Explicit-query visual](assets/explicit_query_viz.png)
</details>

<details>
<summary><strong>Neutral-query metrics</strong></summary>

### Overall

| metric   |  mean | median |
| -------- | ----: | -----: |
| baseline | 0.423 |  0.400 |
| debiased | 0.241 |  0.200 |
| diff     | 0.182 |  0.100 |

### Wilcoxon (baseline > debiased)

| statistic   | p-value (one-sided) |
| ----------- | ------------------- |
| 1.931 × 10⁴ | 6.49 × 10⁻³⁴        |

### Per-category

| category         | μ baseline | μ debiased | μ diff | ˜ baseline | ˜ debiased | ˜ diff |
| ---------------- | ---------: | ---------: | -----: | ---------: | ---------: | -----: |
| animal\_cruelty  |      0.433 |      0.197 |  0.237 |       0.40 |       0.20 |   0.20 |
| gore             |      0.493 |      0.323 |  0.170 |       0.50 |       0.30 |   0.10 |
| self\_harm       |      0.410 |      0.203 |  0.207 |       0.40 |       0.20 |   0.20 |
| sexual\_assault  |      0.414 |      0.248 |  0.166 |       0.40 |       0.20 |   0.10 |
| sexual\_content  |      0.473 |      0.283 |  0.190 |       0.50 |       0.25 |   0.20 |
| substance\_abuse |      0.267 |      0.123 |  0.143 |       0.25 |       0.05 |   0.10 |
| violence         |      0.500 |      0.356 |  0.144 |       0.50 |       0.40 |   0.10 |


### Visual
![Neutral-query visual](assets/neutral_query_viz.png)
</details>

<!-- ---

### Visual comparison

<p align="center">
  <img src="assets/explicit_query_viz.png" alt="Explicit-query visual" width="45%" />
  &nbsp;&nbsp;
  <img src="assets/neutral_query_viz.png"  alt="Neutral-query visual"  width="45%" />
</p> -->

---

## Reproducing the study ⚙️

```bash
git clone https://github.com/your-handle/IR_Concept_Erasure.git
cd IR_Concept_Erasure
python -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
python IRConceptErasure.ipynb   # or run the notebook
```

---

### Todo

* [ ] Publish dataset-creation script
* [ ] Automate metric & figure generation
* [ ] Add ablation studies (layer-wise projection, alt embeddings)
