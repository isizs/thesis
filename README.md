# Analyzing the Impact of Date Formats on Temporal Reasoning in Language Models

A Bachelor's Thesis by **Hanna Kulik**  
Submitted to the Department of Computational Linguistics  
Ludwig-Maximilians-Universität München

**Supervisor:** Zeinab Sadat Taghavi  
**Examiner:** Prof. Dr. Hinrich Schütze

---

## Abstract

Pretrained Large Language Models (LLMs) often show limitations in temporal reasoning, particularly when processing time-dependent facts. This thesis investigates a potentially overlooked factor influencing their performance: the syntactic format of date expressions. The central research question explores how different date formats affect LLMs' accuracy on temporal reasoning benchmarks. To address this, the study systematically evaluated the Llama 3 model on the date arithmetic tasks of the TEMPReason benchmark. Questions were presented with date and temporal offset information in four distinct syntactic formats, ranging from naturalistic language to structured ISO 8601 representations. The findings reveal that date format does impact the model's precision. A structured ISO format for base dates achieved the highest Exact Match accuracy, while a fully verbose, word-based format produced the lowest Mean Absolute Error in years, suggesting different forms of errors based on input style. This research concludes that the syntactic representation of dates is a significant factor in LLM temporal reasoning, highlighting the need for greater consideration of format diversity in benchmark design and prompt engineering.

## Repository Structure

The project is organized as follows:

├── code/
│ └── New_Datasets.ipynb # Main notebook for data generation, inference, and evaluation
├── data/
│ ├── original_... .jsonl # Generated datasets with varied formats
│ └── metrics_predictions_...json # Model predictions and final metrics
├── bsc-hanna-kulik-11954006.pdf # The final compiled PDF of the thesis
├── requirements.txt
└── README.md

## Experiment setup
Hardware: A machine with an NVIDIA CUDA-enabled GPU is required for the model inference stage. A modern GPU with at least 16 GB of VRAM is recommended due to the model's size and use of bfloat16.
Software: Python 3.10 or later.
Hugging Face Account: A Hugging Face account with approved access to the Llama 3 models is needed. An access token with read permissions is required for authentication.
# Setup Instructions

Install all required packages:
pip install -r requirements.txt

Execution Workflow
- Launch a Jupyter environment (e.g., jupyter lab or jupyter notebook) with the activated virtual environment.
- Open the notebook code/New_Datasets.ipynb.
- Execute all cells sequentially from top to bottom.
The notebook is structured to perform the following operations in order:
1. Data Generation: Downloads the original TempReason L1 test set, parses it, and generates 12 dataset variants with different date formats. These are saved to a new directory named temp_reason_modified_datasets/.
2. Model Inference: Loads the Llama 3.2 model via the Hugging Face pipeline. It then iterates through the four selected dataset variants, runs inference in batches, and saves the raw model predictions to a new directory named model_predictions_on_4_datasets_BATCHED/.
3. Evaluation: The final cells of the notebook contain the code to load the prediction files and calculate the final metrics (Exact Match, MAE-Year, and Trend Accuracy) for each experimental condition, printing the results directly in the notebook output.
Upon successful completion, all generated data, predictions, and metrics will be available in their respective directories for further analysis.
