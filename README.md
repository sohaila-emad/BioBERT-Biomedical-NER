# BioNER — Biomedical Named Entity Recognition with BioBERT

A Biomedical Named Entity Recognition (BioNER) project that uses **BioBERT** to identify and classify biomedical entities in scientific text using token-level classification.

The project is built on the **EMBO SourceData** dataset and focuses on extracting biological and experimental entities from scientific research text, including genes, diseases, organisms, cell types, and experimental assays.

The goal is to develop a reliable biomedical information extraction model while investigating how tokenization, label alignment, and model architecture affect entity-level performance.

---

## Project Overview

Biomedical research papers contain large amounts of unstructured scientific text. Extracting meaningful biomedical entities from this text can help organize scientific knowledge and support downstream biomedical NLP applications.

This project addresses that challenge by fine-tuning BioBERT for token-level entity classification using the BIO tagging scheme.

The model predicts a label for each token in a scientific text sequence, allowing the reconstruction of complete biomedical entity spans.

### Key Features

- Fine-tuning BioBERT for biomedical NER.
- Extracting 9 types of biomedical entities.
- BIO-based token classification.
- Subword tokenization and label alignment.
- Exploratory data analysis and annotation inspection.
- Entity-level evaluation using strict IOB2 scoring.
- Comparison of alternative label alignment strategies.
- Experiments with a CRF-based architecture and Dice loss.
- Held-out test set evaluation.
- Saving the trained model and tokenizer for inference.
- Hosting the trained model on Hugging Face for easy access and reuse.

---

## Trained Model

The fine-tuned BioBERT model is hosted on Hugging Face and is available for download and inference.

**Hugging Face Model:** [Sohaila052/biobert_ner](https://huggingface.co/Sohaila052/biobert_ner)

The repository contains the trained model weights, configuration, and tokenizer files required to load the model for inference.

---

## Dataset

**EMBO SourceData — Biomedical Named Entity Recognition**

The dataset is obtained from the EMBO SourceData repository and contains scientific text annotated with biomedical entity labels.

### Dataset Splits

| Split | Number of Examples |
|---|---:|
| Training | 55,250 |
| Validation | 7,951 |
| Test | 6,844 |
| **Total** | **70,045** |

Each example contains:

- `words`: A sequence of words.
- `labels`: BIO annotations corresponding to each word.
- `text`: Associated text metadata.
- `is_category`: Additional metadata.

The dataset is divided into training, validation, and test sets.

The validation set is used for model selection, while the test set is reserved for final evaluation.

---

## Entity Categories

The model recognizes **9 biomedical entity types**.

| Entity Type | Description |
|---|---|
| `GENEPROD` | Genes and gene products |
| `EXP_ASSAY` | Experimental assays and techniques |
| `SMALL_MOLECULE` | Small molecules and chemical compounds |
| `ORGANISM` | Organisms used or mentioned in research |
| `SUBCELLULAR` | Subcellular structures and components |
| `TISSUE` | Biological tissues |
| `CELL_LINE` | Established cell lines |
| `CELL_TYPE` | Biological cell types |
| `DISEASE` | Diseases and pathological conditions |

---

## BIO Tagging Scheme

The dataset uses the BIO tagging scheme to represent entity boundaries.

| Tag | Meaning |
|---|---|
| `O` | Token is outside any entity |
| `B-<ENTITY>` | First token of an entity |
| `I-<ENTITY>` | Continuation of an entity |

For example, an entity spanning multiple words may be represented as:

```text
B-GENEPROD I-GENEPROD
```markdown
# BioBERT Named Entity Recognition (NER)

This repository provides code and instructions for performing biomedical Named Entity Recognition (NER) using a fine-tuned BioBERT model.

---

## Model Inference

You can load the fine-tuned model directly from Hugging Face using the `transformers` library.

### Installation

```bash
pip install transformers torch

```

### Loading the Model

```python
from transformers import AutoTokenizer, AutoModelForTokenClassification

model_name = "Sohaila052/biobert_ner"

tokenizer = AutoTokenizer.from_pretrained(model_name)
model = AutoModelForTokenClassification.from_pretrained(model_name)

```

The model is now ready for token-level biomedical entity classification.

---

## Technologies Used

* **Python**
* **PyTorch**
* **Hugging Face Transformers**
* **BioBERT**
* **Pandas**
* **NumPy**
* **Scikit-learn**

---

## Future Improvements

* Explore additional model architectures for biomedical NER.
* Investigate alternative token-label alignment strategies.
* Improve entity extraction through more advanced decoding methods.
* Evaluate generalization across different biomedical text sources.

---

## Author

**Sohaila Abdelmageed**

* **Hugging Face:** [Sohaila052](https://www.google.com/search?q=https://huggingface.co/Sohaila052&utm_source=gemini)

```

```
