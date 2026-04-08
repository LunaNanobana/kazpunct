
# KazPunct — Kazakh Punctuation Restoration

> **NLP Track**  


Punctuation restoration for Kazakh ASR (Automatic Speech Recognition) output using a fine-tuned multilingual RoBERTa model.

---

## The Problem

ASR systems transcribe speech as raw lowercase text with no punctuation:

```
сіз не деп ойлайсыз бұл мәселені шешу керек немесе жоқ
```

Without punctuation this text is unreadable and blocks downstream NLP tasks (summarisation, translation, dialogue systems). The task: predict what punctuation mark (if any) should follow each word.

---

## Approach

| Step | Method |
|---|---|
| Base model | `xlm-roberta-base` (multilingual, handles Kazakh) |
| Task framing | Token classification — predict a label per word |
| Labels | `O` (none) · `,` · `.` · `?` |
| Training | Fine-tuned on labelled Kazakh text corpus |
| Evaluation | Precision / Recall / F1 per punctuation class |

---

## Tech Stack

`Python` · `PyTorch` · `Hugging Face Transformers` · `xlm-roberta-base` · `pandas` · `numpy`

---

## Project Structure

```
kazpunct/
└── KazPunct-Hackathon.ipynb    # Full pipeline: preprocessing → training → evaluation
```

---

## Run It

Open `KazPunct-Hackathon.ipynb` in Jupyter or Google Colab:

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/LunaNanobana/kazpunct/blob/main/KazPunct-Hackathon.ipynb)

```bash
pip install transformers torch datasets pandas numpy
jupyter notebook KazPunct-Hackathon.ipynb
```

---

## Why This Matters

Kazakh NLP is severely under-resourced compared to English or even Russian. Models trained on English punctuation restoration perform poorly on Kazakh due to different sentence structure and morphology. This project is one of very few publicly available Kazakh punctuation restoration implementations.

---

*Built at WISH Hackathon 2026.*
