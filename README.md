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

