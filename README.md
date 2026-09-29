# C-to-x86 LLM Compiler

A Columbia University NLP team project exploring whether large language models can learn to translate C programs into x86 assembly.

We fine-tuned and post-trained **CodeLlama-7B** using supervised fine-tuning and reinforcement-learning methods, then evaluated the models through compilation-based and code-similarity metrics.

> The original team development repository is private.  
> This public repository contains my individual implementation work, the project report, model links, dataset, and evaluation notebooks.

## My Contributions

My work on the project focused on:

- Implementing a **PPO-based post-training pipeline** for CodeLlama-7B
- Building a **few-shot SFT variant** using LoRA/PEFT
- Curating and publishing the **15,000-sample C-to-x86 dataset**
- Building compilation and code-similarity evaluation utilities
- Comparing outputs across the base, SFT, few-shot SFT, GRPO, and PPO models

The GRPO implementation and the primary SFT model were developed by a teammate as part of the broader team project.

## Results

| Model | Compilation Success |
|---|---:|
| Base CodeLlama-7B | 2% |
| GPT-4o-mini | 32% |
| SFT | 38% |
| PPO | **46%** |
| GRPO | 48% |

The PPO model improved compilation success from **2% to 46%** and outperformed GPT-4o-mini on the same evaluation setup.

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
