# Pediatric-ECG-Fine-Tuned-OpenTSLM
Code repository for a thesis project on pediatric ECG interpretation using OpenTSLM fine-tuning, ECG digitization, data harmonization, and model evaluation.

## Project Overview

Pediatric ECG interpretation is challenging because the physiological characteristics of children differ from those of adults, including age-dependent variations in heart rate, conduction intervals, waveform morphology, and cardiac electrical axis.

This project develops and evaluates a prototype pediatric ECG interpretation system based on OpenTSLM through fine-tuning optimization. The computational workflow includes ECG image digitization, signal post-processing, data harmonization, dataset preparation for OpenTSLM, model fine-tuning, inference, and multi-level evaluation.

The dataset used in this study consisted of pediatric ECG images and clinical metadata from RSAB Harapan Kita. Due to privacy, ethical, and institutional restrictions, the dataset is not publicly shared in this repository.

## Research Workflow

The main workflow of this study consists of:

1. ECG image curation and anonymization
2. ECG image digitization using Open ECG Digitizer
3. Signal post-processing and data harmonization
4. Dataset formatting for OpenTSLM
5. Preliminary fine-tuning using the Gemma backbone
6. Main fine-tuning using the LLaMA backbone
7. Retraining using a masked custom collator
8. Evaluation using generative, classification, and clinical metrics

## Repository Structure

```text
Pediatric-ECG-Fine-Tuned-OpenTSLM/
│
├── README.md
│
└── notebooks/
    ├── 01_ecg_digitizer_model.ipynb
    ├── 02_post_processing_and_harmonization.ipynb
    ├── 03_finetuned_gemma_preliminary_experiment.ipynb
    └── 04_finetuned_llama_main_experiment.ipynb
```
## Notebook Description
| Notebook                                          | Description                                                                                                                     |
| ------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| `01_ecg_digitizer_model.ipynb`                    | Runs the ECG digitization pipeline to convert pediatric ECG images into numerical time-series signals using Open ECG Digitizer. |
| `02_post_processing_and_harmonization.ipynb`      | Performs signal post-processing, data harmonization, formatting, and dataset preparation for OpenTSLM.                          |
| `03_finetuned_gemma_preliminary_experiment.ipynb` | Contains the preliminary fine-tuning experiment using the Gemma backbone.                                                       |
| `04_finetuned_llama_main_experiment.ipynb`        | Contains the main OpenTSLM fine-tuning experiment using the LLaMA backbone, including retraining and model evaluation.          |

## Model Development

This study uses OpenTSLM as the main time-series language model framework. Gemma was used as a preliminary backbone experiment to verify the pipeline, while LLaMA was used as the main model backbone.

The main LLaMA fine-tuning process consisted of:
- Initial fine-tuning for 8 epochs
- Retraining for 5 epochs using a masked custom collator
- Loss calculation focused on answer tokens during retraining
- Final evaluation using generative, classification, and clinical evaluation metrics

## Evaluation Summary
The final model was evaluated using three levels of evaluation: generative evaluation, classification evaluation, and clinical evaluation.

### Generative Evaluation
| Metric       | Score |
| ------------ | ----: |
| BLEU-1       | 0.411 |
| BLEU-4       | 0.275 |
| METEOR       | 0.485 |
| ROUGE-L      | 0.469 |
| BERTScore-F1 | 0.906 |

### Classification Evaluation
| Metric            | Score |
| ----------------- | ----: |
| Accuracy          | 0.647 |
| Weighted F1-score | 0.508 |
| Macro F1-score    | 0.196 |

The classification evaluation showed that all predictions were mapped as Normal, resulting in all abnormal samples being incorrectly classified as Normal. Therefore, the classification performance should be interpreted cautiously.

### Clinical Evaluation
Clinical evaluation was conducted using an LLM-as-a-Judge approach.
| Clinical Dimension       |      Score |
| ------------------------ | ---------: |
| Diagnostic accuracy      |  2.529 / 5 |
| Clinical consistency     |  2.235 / 5 |
| Pediatric relevance      |  4.353 / 5 |
| Safety                   |  4.000 / 5 |
| Overall clinical quality | 5.529 / 10 |

The BERTScore-F1 value reflects textual semantic similarity and should not be interpreted as evidence of clinical diagnostic correctness. The safety score reflects the linguistic safety style of the generated output and does not guarantee clinical safety.

## Data Availability
The pediatric ECG dataset from RSAB Harapan Kita is not publicly available due to privacy, ethical, and institutional restrictions.

The following files and folders are not included in this public repository:
```
images/
output_digitizer/
opentslm_ready/
metadata_ecg_rsab.csv
train_data.csv
val_data.csv
test_data.csv
```
These files contain patient-derived ECG data, clinical metadata, or dataset split information. This repository only provides cleaned research notebooks, documentation, and aggregate evaluation results.

No original ECG images, patient-derived ECG signals, patient-level metadata, clinical labels, patient-level predictions, or fine-tuned model checkpoints are included in this repository.

## Clinical Disclaimer
This project is intended for research purposes only. The developed system is not intended for standalone clinical diagnosis, triage, or decision-making.

Further dataset expansion, physician validation, improved grounding to ECG signals, and prospective clinical evaluation are required before any clinical application.

## Thesis Information

Title: Pengembangan dan Evaluasi Sistem Interpretasi Elektrokardiogram Pediatrik Berbasis Open Time-Series Language Model melalui Optimasi Fine-Tuning

Author: Aliyah Fathimah Assagaf
Institution: Biomedical Engineering, Faculty of Engineering, Universitas Indonesia
Dataset Source: RSAB Harapan Kita

## Citation

If you use or refer to this repository, please cite the related thesis or publication.
```
@thesis{assagaf2026pediatricecgopentslm,
  title={Pengembangan dan Evaluasi Sistem Interpretasi Elektrokardiogram Pediatrik Berbasis Open Time-Series Language Model melalui Optimasi Fine-Tuning},
  author={Assagaf, Aliyah Fathimah},
  year={2026},
  school={Universitas Indonesia}
}
```
