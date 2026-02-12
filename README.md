# 🇲🇦 Darija-Voice Med

> **Privacy-Preserving Maternal Health Risk Prediction using Federated Learning**

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://python.org)
[![Flower](https://img.shields.io/badge/Flower-FL-pink.svg)](https://flower.dev)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

## 📋 Overview

Darija-Voice Med is a SOTA 2025 AI system that predicts maternal health risks from voice input in **Moroccan Darija** while preserving patient privacy through **Federated Learning**.

### 🎯 Key Features

| Component | Technology | Purpose |
|-----------|------------|---------|
| **ASR** | `ychafiqui/whisper-small-darija` | Voice → Text (Moroccan Darija) |
| **SLM** | `microsoft/Phi-3.5-mini-instruct` | Text → Structured Symptoms (JSON) |
| **FL** | Flower + XGBoost | Federated Risk Prediction |
| **Privacy** | Differential Privacy (Noise Injection) | Data Protection |
| **UI** | Gradio | Interactive Demo |

### 🔒 Privacy Guarantees

- ✅ **Audio**: Never sent to server (processed locally)
- ✅ **Symptoms**: Extracted and stored locally only
- ✅ **Model params**: Noised with Differential Privacy before sharing

---

## 🚀 Quick Start

### 1. Clone the Repository

```bash
git clone https://github.com/Eric-Kambire/AgorAI.git
cd AgorAI
```

### 2. Open in Google Colab (Recommended)

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Eric-Kambire/AgorAI/blob/main/darija_voice_med.ipynb)

### 3. Or Run Locally

```bash
# Create virtual environment
python -m venv venv
source venv/bin/activate  # Linux/Mac
# or: venv\Scripts\activate  # Windows

# Install dependencies
pip install -r requirements.txt

# Launch Jupyter
jupyter notebook darija_voice_med.ipynb
```

---

## 📁 Project Structure

```
AgorAI/
├── darija_voice_med.ipynb   # Main notebook (28 cells)
├── notebookguideline.md     # Architecture documentation
├── README.md                # This file
└── requirements.txt         # Dependencies (optional)
```

---

## 🛠️ Git Commands Guide

### 📥 Initial Setup (First Time)

```bash
# 1. Initialize a new repository
git init

# 2. Add remote origin
git remote add origin https://github.com/Eric-Kambire/AgorAI.git

# 3. Set main branch
git branch -M main
```

### 📤 Push Changes (Upload to GitHub)

```bash
# 1. Check what files changed
git status

# 2. Add files to staging
git add .                    # Add all files
# or
git add filename.ipynb       # Add specific file

# 3. Commit with message
git commit -m "Your commit message here"

# 4. Push to GitHub
git push origin main
# or first time:
git push -u origin main
```

### 📥 Pull Changes (Download from GitHub)

```bash
# Get latest changes from remote
git pull origin main
```

### 🔄 Complete Workflow Example

```bash
# --- First time setup ---
cd D:\ECC\GitHub\AGORAI
git init
git remote add origin https://github.com/Eric-Kambire/AgorAI.git
git add .
git commit -m "Initial commit: Darija-Voice Med notebook"
git branch -M main
git push -u origin main

# --- Daily workflow ---
git pull origin main                    # Get latest changes
# ... make your changes ...
git add .                               # Stage changes
git commit -m "Add new feature X"       # Commit
git push origin main                    # Push to GitHub
```

### 📋 Useful Git Commands

| Command | Description |
|---------|-------------|
| `git status` | Show changed files |
| `git log --oneline` | Show commit history |
| `git diff` | Show unstaged changes |
| `git diff --staged` | Show staged changes |
| `git checkout -- file` | Discard changes to file |
| `git reset HEAD file` | Unstage a file |
| `git remote -v` | Show remote URLs |
| `git branch` | List branches |

### ⚠️ Common Issues & Fixes

```bash
# If remote already exists:
git remote remove origin
git remote add origin https://github.com/Eric-Kambire/AgorAI.git

# If push rejected (remote has changes):
git pull origin main --rebase
git push origin main

# If you need to force push (careful!):
git push -f origin main
```

---

## 📊 Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                     EDGE DEVICE (Tablet)                     │
├─────────────────────────────────────────────────────────────┤
│  🎤 Audio Input                                              │
│       ↓                                                      │
│  🗣️ Whisper-Darija (ASR)                                     │
│       ↓                                                      │
│  🧠 Phi-3.5-mini (Symptom Extraction)                        │
│       ↓                                                      │
│  📊 XGBoost (Local Risk Prediction)                          │
│       ↓                                                      │
│  🔒 Differential Privacy (Noise Injection)                   │
│       ↓                                                      │
│  📤 Send ONLY noised parameters (not data!)                  │
└─────────────────────────────────────────────────────────────┘
                              ↓
┌─────────────────────────────────────────────────────────────┐
│                    FLOWER SERVER                             │
├─────────────────────────────────────────────────────────────┤
│  🌸 FedAvg Aggregation                                       │
│  📈 Global Model Update                                      │
│  📤 Broadcast to all clients                                 │
└─────────────────────────────────────────────────────────────┘
```

---

## 📈 Results

| Metric | Value |
|--------|-------|
| **Final Accuracy** | ~85%+ |
| **Data Reduction** | 250x less transmitted |
| **Privacy Budget (ε)** | 1.0 |
| **FL Rounds** | 3 |
| **Clients** | 3 (Non-IID villages) |

---

## 🤝 Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 👥 Team

- **Eric Kambire** - [GitHub](https://github.com/Eric-Kambire)

---

## 🙏 Acknowledgments

- [Flower](https://flower.dev) - Federated Learning Framework
- [Hugging Face](https://huggingface.co) - Transformers & Models
- [ychafiqui](https://huggingface.co/ychafiqui) - Whisper-Darija Model
- UCI Machine Learning Repository - Maternal Health Dataset

---

<p align="center">
  <b>Built with ❤️ for Moroccan Healthcare</b><br>
  <i>"Privacy-first AI for maternal health in rural Morocco"</i>
</p>
