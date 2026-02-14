# 🇲🇦 Darija-Voice Med

> **Privacy-Preserving AI Health Assistant for Rural Morocco**
> **نظام ذكي للصحة في المناطق القروية بالمغرب**

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://python.org)
[![Flower](https://img.shields.io/badge/Flower-FL-pink.svg)](https://flower.dev)
[![MedGemma](https://img.shields.io/badge/MedGemma-4B-green.svg)](https://huggingface.co/google/medgemma-4b-it)
[![TTS](https://img.shields.io/badge/TTS-Darija-orange.svg)](https://github.com)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

## 📋 Overview

Darija-Voice Med is a comprehensive **AI health assistant for rural Morocco** that:
- 🎤 Understands **Moroccan Darija** voice input
- 🔊 **SPEAKS BACK in Darija** for illiterate patients ✨ **NEW!**
- 🧠 Uses **MedGemma-4B** for medical-grade analysis
- 💊 **Translates prescriptions** FR/EN → Darija + Audio
- 📷 **Analyzes medical images** (X-rays, scans)
- 👨‍⚕️ **Summarizes consultations** for doctors (Darija → FR/EN)
- 🔒 Preserves **patient privacy** with Federated Learning

---

## 🔊 NEW: Audio Response for Illiterate Patients

```
┌─────────────────────────────────────────────────────────────┐
│  👩‍🌾 Patient: "Rassi kaydor w tansion tal3a..."              │
│                           ↓                                  │
│  🧠 AI Analysis: High Risk Detected                          │
│                           ↓                                  │
│  🔊 Audio Response:                                          │
│     "Khouya, 3andek mochkil kbir. Khassek tmchi l tabib     │
│      daba daba. Ma tssennach!"                               │
│                           ↓                                  │
│  👂 Patient HEARS the advice (no reading required!)          │
└─────────────────────────────────────────────────────────────┘
```

---

## 🎯 Interface Complète (4 Onglets)

| Tab | Fonctionnalité | Pour qui | Audio? |
|-----|---------------|----------|--------|
| 🩺 **Diagnostic** | Voix → Symptômes → Risque | Patient | ✅ Oui |
| 💊 **Ordonnances** | FR/EN → Darija expliqué | Patient rural | ✅ Oui |
| 👨‍⚕️ **Médecin** | Darija → FR/EN rapport | Médecin | ❌ |
| 🔬 **Radio/Scan** | Image → Analyse | Agent santé | ❌ |

### Stack Technique

| Component | Technology | Purpose |
|-----------|------------|---------|
| **ASR** | `whisper-small-darija` | Voice → Text |
| **SLM** | `MedGemma-4B` | Medical AI |
| **TTS** | `gTTS (Arabic)` | Text → Audio Darija |
| **FL** | Flower + XGBoost | Federated Learning |
| **Privacy** | Differential Privacy | Data Protection |

### 🔒 Privacy Guarantees

- ✅ **Audio**: Never sent to server (processed locally)
- ✅ **Symptoms**: Extracted and stored locally only
- ✅ **Images**: Analyzed locally, never uploaded
- ✅ **Model params**: Noised with Differential Privacy

---

## 🏥 Use Cases: Santé Rurale Maroc

```
┌────────────────────────────────────────────────────────────────┐
│               🏥 SANTÉ RURALE MAROC                             │
├────────────────────────────────────────────────────────────────┤
│                                                                │
│  👩‍🌾 PATIENT RURAL (ne parle que Darija)                       │
│      │                                                         │
│      ▼                                                         │
│  🎤 "Rassi kaydor w tansion tal3a l 140..."                    │
│      │                                                         │
│      ▼                                                         │
│  ┌──────────────────────────────────────────┐                  │
│  │ 🩺 DIAGNOSTIC                             │                  │
│  │    → Extraction symptômes                 │                  │
│  │    → Niveau de risque: 🟡 MODÉRÉ         │                  │
│  └──────────────────────────────────────────┘                  │
│      │                                                         │
│      ▼                                                         │
│  ┌──────────────────────────────────────────┐                  │
│  │ 💊 TRADUCTION ORDONNANCE                  │                  │
│  │    "Paracétamol 500mg 3x/jour" →          │                  │
│  │    "Khod 7abba f sba7, f 12, w l3chiya"  │                  │
│  └──────────────────────────────────────────┘                  │
│      │                                                         │
│      ▼                                                         │
│  ┌──────────────────────────────────────────┐                  │
│  │ 📷 ANALYSE RADIO                          │                  │
│  │    Image échographie → Analyse MedGemma   │                  │
│  │    ⚠️ Aide au diagnostic                  │                  │
│  └──────────────────────────────────────────┘                  │
│      │                                                         │
│      ▼                                                         │
│  📋 RÉSUMÉ FR → Agent Santé / Médecin                          │
│                                                                │
└────────────────────────────────────────────────────────────────┘
```

---

## 🚀 Quick Start

### Option 1: Google Colab (Recommandé)

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Eric-Kambire/AgorAI/blob/main/darija_voice_med.ipynb)

> ⚠️ **MedGemma** nécessite d'accepter la licence: [google/medgemma-4b-it](https://huggingface.co/google/medgemma-4b-it)

### Option 2: Local

```bash
git clone https://github.com/Eric-Kambire/AgorAI.git
cd AgorAI
pip install -r requirements.txt
jupyter notebook darija_voice_med.ipynb
```

---

## ⚡ Optimisations Notebook Pro (v2.0)

Le notebook a été optimisé pour les environnements avec **GPU + RAM limitée**:

### Changements Clés

| Modification | Avant | Après | Impact |
|-------------|-------|-------|--------|
| **Modèle SLM** | Phi-3.5-mini | **MedGemma-4B** | Spécialisé médical 🏥 |
| **Fallback** | Aucun | TinyLlama-1.1B | Pour T4/CPU |
| **Gestion mémoire** | Aucune | `clear_memory()` | Évite OOM |
| **FL Simulation** | gRPC | Séquentiel | Compatible Colab |

### Modèles par GPU

| GPU | VRAM | Modèle |
|-----|------|--------|
| H100/A100 | ≥35GB | MedGemma-4B (4-bit) |
| L4 | 24GB | MedGemma-4B (4-bit) |
| T4 | 16GB | TinyLlama-1.1B |

### Fonction de Nettoyage Mémoire

```python
def clear_memory():
    gc.collect()
    if torch.cuda.is_available():
        torch.cuda.empty_cache()
        torch.cuda.synchronize()
```

### Configuration Gradio Recommandée (Notebook Pro)

```python
demo.launch(
    share=True,              # REQUIS pour lien public
    debug=False,             # Évite conflits
    server_name="0.0.0.0",   # Écoute toutes interfaces
    server_port=7860
)
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
│  🧠 TinyLlama-1.1B (Symptom Extraction) ← Optimisé RAM       │
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
| **VRAM Usage** | ~2-3 GB (optimisé) |

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
- [TinyLlama](https://huggingface.co/TinyLlama) - Lightweight LLM
- UCI Machine Learning Repository - Maternal Health Dataset

---

<p align="center">
  <b>Built with ❤️ for Moroccan Healthcare</b><br>
  <i>"Privacy-first AI for maternal health in rural Morocco"</i>
</p>
