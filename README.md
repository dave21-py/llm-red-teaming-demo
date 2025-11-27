### LLM Adversarial Alignment & Red Teaming Suite

![Python](https://img.shields.io/badge/Python-3.10%2B-blue)
![PyTorch](https://img.shields.io/badge/PyTorch-2.0%2B-red)
![Model](https://img.shields.io/badge/Model-Mistral--7B-green)

#### Overview
This repository contains a set of experiments investigating **Large Language Model (LLM) Safety**. It progresses from manual vulnerability analysis (Social Engineering) to a fully automated, multi-agent reinforcement learning loop (RLAIF) for red teaming.

The goal is to demonstrate how open-weights models (Mistral-7B) can be compromised by adversarial prompts and how to engineer robust defenses.

#### Modules

### 1. [Baseline Analysis & Defense](./1.ipynb)
*   **Objective:** Establish baseline safety behaviors and test manual jailbreak techniques.
*   **Methodology:** Implemented "Persona Adoption" attacks (e.g., The Grandma Attack) to bypass safety filters.
*   **Defense:** Engineered a **Constitution-based System Prompt** that successfully reduced the attack success rate from **66% to 0%** without fine-tuning.

#### 2. [Automated Adversarial Agents (RLAIF)](./2.ipynb)
*   **Objective:** Scale red teaming by removing the human from the loop.
*   **Architecture:** Built a **Multi-Agent System** using a single LLM to simulate three distinct roles:
    1.  **Attacker:** Generates and mutates adversarial prompts.
    2.  **Target:** The safety-aligned model under test.
    3.  **Judge:** Evaluates the attack and provides *feedback* to the Attacker.
*   **Result:** Demonstrated **In-Context Learning** where the Attacker agent evolved its strategy (from "Journalist" to "Authority Figure") based on the Judge's feedback.

#### Tech Stack
*   **Core:** Python, PyTorch, Transformers (Hugging Face).
*   **Optimization:** BitsAndBytes (4-bit Quantization / NF4) for A100 GPU efficiency.
*   **Techniques:** Prompt Engineering, System Prompting, Chain-of-Thought, In-Context Learning.
