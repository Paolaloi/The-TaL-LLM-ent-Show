# The taL(LM)ent Show  
**A Structured Evaluation Framework for Creative Prompting in Large Language Models**

## Overview

*The taL(LM)ent Show* is an experimental framework designed to evaluate how Large Language Models (LLMs) respond to creative, role-based, and emotion-focused prompting under controlled conditions.  
The project adopts a **“talent show” metaphor**: fictional artists perform texts, fictional judges evaluate them, and a presenter summarizes the results.  
This setup allows systematic observation of the balance between **structure, creativity, and alignment** in open-access LLMs.

The study integrates both **quantitative metrics** (e.g., entropy, log-probability margins, JSON validity) and **qualitative analyses** (stylistic fidelity, affect calibration, and saliency interpretation).

## Experimental Goals

- Compare instruction-tuned models across roles and decoding regimes.  
- Assess how alignment depth influences structural control and stylistic coherence.  
- Examine whether creative sampling parameters improve expressiveness without loss of consistency.  
- Explore saliency-based interpretability to identify which prompt tokens drive model behavior.

## Models Evaluated

| Model | Size | Type |
|:------|:-----:|:------|
| GPT-2 Large | 774M | Baseline |
| Falcon 3 1B Instruct | 1B | Instruction-tuned |
| LLaMA 3.2 3B Instruct | 3B | Instruction-tuned |
| Mistral 7B Instruct (v0.2) | 7B | Instruction-tuned |
| Hermes-2-Pro-Mistral-7B | 7B | Instruction + Chat fine-tuning |

All models were executed in a local environment (Google Colab Pro / PyTorch CUDA) using Hugging Face `transformers`, with consistent decoding APIs to ensure fair comparability.

## Prompting Modes

| Mode | Description |
|:-----|:-------------|
| **Zero-Shot** | Neutral baseline without persona conditioning. |
| **Role-Based** | The model adopts the linguistic and evaluative style of a judge. |
| **Emotion-Role** | Adds explicit affective emphasis (“high emotion” setting). |
| **Presenter Wrap-Up** | Synthesizes multiple judge perspectives in a concise summary. |

Each mode is tested under two decoding regimes:

- **Controlled** → low temperature, narrow top-p/top-k sampling (stability).  
- **Creative** → higher temperature and sampling breadth (expressive variation).

