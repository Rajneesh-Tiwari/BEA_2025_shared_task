# Tutor Identity Classification Challenge

A comprehensive solution for automated tutor identity classification using ensemble transformer models and meta-learning techniques.

## 🏆 Competition Results

| Track | Final Macro F1 | Final Accuracy | Leaderboard Rank |
|-------|---------------|----------------|------------------|
| Track 4 | 0.6906 | 0.7482 | 6 |
| Track 5 | 0.9698 | 0.9662 | 1 |

## 📋 Overview

This repository contains our solution for the Tutor Identity Classification Challenge, focusing on distinguishing between human expert tutors and various large language models (LLMs) in educational conversations. Our approach leverages ensemble methods combining multiple transformer architectures with meta-learning for superior performance.

### Problem Statement

The task involves classifying tutor responses across multiple categories:
- **Track 4**: Multi-class classification 
- **Track 5**: Binary classification (Human vs. AI)

**Tutor Categories**:
- Human Expert Tutors
- Large Language Models: GPT-4, Claude Sonnet, Gemini, Llama 3.1 (8B/405B), Phi3, Mistral

## 🚀 Methodology

### Model Architecture

Our solution employs a two-stage ensemble approach:

#### Stage 1: Base Models
- **DeBERTa-v3** (small, base, large)
- **Longformer-base-4096**
- **BigBird-RoBERTa-large** 
- **Qwen-2.5-0.5B**
- **Zephyr-7B-alpha**

#### Stage 2: Meta-Learning
- **LightGBM meta-model** for combining base model predictions
- **Feature engineering** using probability outputs from all base models
- **Pseudolabeling** with high-confidence predictions (probability > 0.85)

### Key Techniques

1. **Cross-Validation**: 5-fold stratified CV for robust validation
2. **Ensemble Methods**: 
   - Model-level averaging
   - Class-specific weighting
   - Meta-learning with LightGBM
3. **Data Augmentation**: Pseudolabeling with constraint satisfaction
4. **Feature Selection**: Importance-based feature ranking

## 📊 Results

### Track 5 Performance
| Model | Val Macro F1 | Val Accuracy | LB Macro F1 | LB Accuracy |
|-------|-------------|-------------|-------------|-------------|
| DeBERTa-v3-large | 0.8995 | 0.8914 | 0.9034 | 0.8958 |
| LightGBM meta-model | 0.9226 | 0.9172 | 0.9268 | 0.9215 |
| **Final Ensemble** | **0.9596** | **0.9560** | **0.9698** | **0.9662** |

### Track 4 Performance
| Model | Val Macro F1 | Val Accuracy | LB Macro F1 | LB Accuracy |
|-------|-------------|-------------|-------------|-------------|
| DeBERTa-v3-large | 0.6360 | 0.7112 | 0.6392 | 0.7145 |
| **Final Ensemble** | **0.6551** | **0.7350** | **0.6906** | **0.7482** |

## 🚀 Future Work

- Explore prompt engineering for LLM-based features
- Investigate attention visualization for interpretability  
- Experiment with knowledge distillation techniques
- Add temporal modeling for conversation-level context

