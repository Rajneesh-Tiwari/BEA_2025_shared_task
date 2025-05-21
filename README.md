# Tutor Identity Classification Challenge

A comprehensive solution for BEA 2025, tracks 4 & 5

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
- **Track 5**: Multi-class classification (2 Human classes & 7 LLM classes)

## 📊 Results

### Track 5 Performance
| Model | Val Macro F1 | Val Accuracy | LB Macro F1 | LB Accuracy |
|-------|-------------|-------------|-------------|-------------|
| **Final Ensemble** | **0.9596** | **0.9560** | **0.9698** | **0.9662** |

### Track 4 Performance
| Model | Val Macro F1 | Val Accuracy | LB Macro F1 | LB Accuracy |
|-------|-------------|-------------|-------------|-------------|
| **Final Ensemble** | **0.6551** | **0.7350** | **0.6906** | **0.7482** |

## 🚀 Future Work

- Explore prompt engineering for LLM-based features
- Investigate attention visualization for interpretability  
- Experiment with knowledge distillation techniques
- Add temporal modeling for conversation-level context

