# Tutor Identity Classification Challenge

A comprehensive solution for automated tutor identity classification using ensemble transformer models and meta-learning techniques.

## 🏆 Competition Results

| Track | Final Macro F1 | Final Accuracy | Leaderboard Rank |
|-------|---------------|----------------|------------------|
| Track 4 | 0.6906 | 0.7482 | - |
| Track 5 | 0.9698 | 0.9662 | - |

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

### Feature Importance Analysis

Top features in our Track 5 meta-model:
1. `Phi3_deberta_large` (18,796)
2. `Llama31405B_deberta_large` (17,536) 
3. `Expert_deberta_large` (14,705)
4. `GPT4_zephyr` (14,491)
5. `Phi3_longformer_large` (12,805)

The analysis reveals that different transformer architectures have specialized strengths in detecting specific tutor identities.
```
## 🔍 Key Insights

1. **Model Specialization**: Different transformer architectures excel at detecting specific tutor types
2. **Meta-Learning Effectiveness**: LightGBM meta-model significantly improves upon simple averaging
3. **Pseudolabeling Impact**: High-confidence pseudolabeling provides substantial performance gains
4. **Cross-Architecture Ensemble**: Combining diverse architectures is crucial for robust performance

## 📈 Ablation Studies

| Component | Track 5 Macro F1 | Improvement |
|-----------|------------------|-------------|
| DeBERTa-large only | 0.8995 | baseline |
| + Other base models | 0.9156 | +0.0161 |
| + Meta-learning | 0.9226 | +0.0070 |
| + Pseudolabeling | 0.9585 | +0.0359 |
| + Final ensemble | 0.9596 | +0.0011 |

## 🚀 Future Work

- Explore prompt engineering for LLM-based features
- Investigate attention visualization for interpretability  
- Experiment with knowledge distillation techniques
- Add temporal modeling for conversation-level context

