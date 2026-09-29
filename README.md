# C-to-x86 LLM Compiler

A Columbia University NLP team project exploring whether large language models can learn to translate C programs into x86 assembly.

The project used **CodeLlama-7B** with supervised fine-tuning and reinforcement-learning-based post-training, followed by compilation-based evaluation.

> The original collaborative development repository is private.  
> This public repository contains my individual implementation work, the project report, dataset, model links, and evaluation notebooks.

## My Contributions

My work on the project focused on:

- Implementing a **PPO-based post-training pipeline** for CodeLlama-7B
- Building a **few-shot SFT variant** using LoRA / PEFT
- Curating and publishing a **15,000-sample C-to-x86 dataset**
- Building compilation and model evaluation workflows
- Comparing outputs across different fine-tuning and post-training approaches

The primary SFT model and GRPO implementation were developed by a teammate as part of the broader team project.

## Results

| Model | Compilation Success |
|---|---:|
| Base CodeLlama-7B | 2% |
| GPT-4o-mini | 32% |
| SFT | 38% |
| PPO | **46%** |
| GRPO | 48% |

My PPO implementation improved compilation success from **2% to 46%**, outperforming GPT-4o-mini on the same evaluation setup.

## Repository Structure

```text
.
├── notebooks/
│   ├── ppo_training.ipynb
│   ├── few_shot_sft.ipynb
│   └── model_output_comparison.ipynb
├── compiler_report.pdf
├── requirements.txt
└── README.md
```

## Notebooks

### `ppo_training.ipynb`

My PPO-based post-training implementation for CodeLlama-7B.

The notebook contains the training pipeline, reward-based optimization, model evaluation, and Hugging Face integration used for my PPO experiments.

### `few_shot_sft.ipynb`

My experimental few-shot supervised fine-tuning variant.

The notebook uses LoRA / PEFT to adapt CodeLlama-7B on C-to-x86 examples and evaluates the resulting model.

### `model_output_comparison.ipynb`

A qualitative comparison of generated assembly across multiple models and training approaches, including:

- Base CodeLlama-7B
- SFT
- Few-shot SFT
- GRPO
- PPO

This notebook is used to inspect how different post-training methods affect generated x86 assembly.

## Dataset

I curated and published a dataset containing **15,000 C-to-x86 assembly samples** for model training and evaluation.

**Hugging Face Dataset:**  
[https://huggingface.co/datasets/AzizZeynalli/c2x86-dataset](https://huggingface.co/datasets/AzizZeynalli/c2x86-dataset)

## Models

### PPO Model

[https://huggingface.co/AzizZeynalli/codellama-7b-c2x86-ppo-rl](https://huggingface.co/AzizZeynalli/codellama-7b-c2x86-ppo-rl)

### Few-Shot SFT Model

[https://huggingface.co/AzizZeynalli/codellama-4bit-peft-lora-r32-sft-c2x86-fewshot](https://huggingface.co/AzizZeynalli/codellama-4bit-peft-lora-r32-sft-c2x86-fewshot)

## Tech Stack

- Python
- PyTorch
- Hugging Face Transformers
- TRL
- PEFT / LoRA
- CodeLlama-7B
- Hugging Face Datasets

## Evaluation

The main evaluation metric is **compilation success**: whether the generated x86 assembly can successfully compile.

The project also uses additional similarity-based evaluation to compare generated assembly with reference outputs.

Compilation-based evaluation is particularly important because valid assembly can differ significantly from a reference implementation while still being functionally correct.

## Project Report

The full team project report, including methodology, experiments, and analysis, is available here:

[`compiler_report.pdf`](./compiler_report.pdf)

## Project Context

This project was completed as part of Columbia University's Natural Language Processing coursework.

It was a collaborative team project. This repository is a public portfolio version containing my individual implementation work and supporting project materials. The original collaborative development repository remains private.
