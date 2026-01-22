# LPCV-track-3

# LLM-as-a-Judge: Reasoning Similarity Evaluator

This notebook implements an **automated evaluation pipeline** to quantify the similarity between LLM-generated explanations and "Ground Truth" expert labels. It uses the **Llama-3.1-8B-Instruct** model via the Hugging Face Inference API to act as a judge.

---

## 🚀 Overview

The primary goal of this tool is to evaluate how well an AI model explains its reasoning when detecting AI-generated images. Instead of simple keyword matching, this script uses a second LLM to perform a **semantic and logical comparison**.



---

## 🛠️ Features

* **Semantic Scoring:** Moves beyond BLEU/ROUGE scores by evaluating the *meaning* and *logic* of the output.
* **Structured Evaluation:** The judge model follows a specific 6-step rubric:
    1. Summarize Ground Truth.
    2. Summarize User Output.
    3. Verify Conclusion Accuracy.
    4. Score Reasoning Similarity ($0.0 - 1.0$).
    5. Score Content Similarity ($0.0 - 1.0$).
    6. Calculate a balanced Final Score.
* **Robust Parsing:** Uses Regex to extract the final numeric score even if the model provides conversational metadata.
* **Lightweight Inference:** Utilizes `huggingface_hub` for serverless inference, requiring no local GPU.

---

## 📋 Prerequisites

To run this notebook, you need to install the following dependencies:

```python
!pip install -U "transformers>=4.35.0" accelerate safetensors huggingface_hub
