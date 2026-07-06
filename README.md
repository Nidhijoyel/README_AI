# README_AI
# AI Teacher: An AI Chatbot for Enhanced Learning Through Speech, Summarization, and Interactive Quizzing

 **Published** — IEEE, 2025 6th International Conference on Recent Advances in Information Technology (RAIT), 2025
DOI: [10.1109/RAIT65068.2025.11089260](https://doi.org/10.1109/RAIT65068.2025.11089260)
 Co-authors: Nidhi Joyel Gaddala, Thiran Bhavani Naidu, Varshini Valiveti, Suresh Dara, Geethika Pandi

---

## Overview

**AI Teacher** is a 3-module educational AI platform designed to make learning more accessible, engaging, and personalized by combining:

1. **Text Summarization** — condenses lengthy educational content into concise summaries
2. **Voice Output** — converts summaries into natural speech for auditory learners and accessibility
3. **Automated Quiz Generation** — turns summaries into multiple-choice questions for active recall and self-assessment

The goal: reduce educator workload while giving students a more interactive, multi-modal way to learn.

## System Architecture

```
Input Text
   │
   ▼
┌─────────────────────┐
│  BART Summarizer     │  → concise, coherent summary
└─────────┬───────────┘
          │
   ┌──────┴───────┐
   ▼              ▼
┌─────────┐   ┌───────────────┐
│  Google  │   │  Google Gemini │
│  TTS     │   │  API (MCQs)    │
└─────────┘   └───────────────┘
   │              │
   ▼              ▼
 Audio          Interactive
 Output          Quiz
```

## Module Details

### 1. Text Summarization — BART
Uses Facebook AI's **BART** (Bidirectional and Auto-Regressive Transformers), an encoder-decoder transformer pre-trained as a denoising autoencoder. Fine-tuned for abstractive summarization to distill long text into key ideas while preserving meaning.

### 2. Voice Output — Google Text-to-Speech
Converts the generated summary into natural-sounding speech across multiple languages/accents, supporting auditory learners and visually impaired users.

### 3. Automated Quiz Generation — Google Gemini API
Applies NLP techniques to extract key topics from the summary and generates multiple-choice questions with plausible distractors, enabling self-assessment.

## Evaluation

Summarization quality was tracked across training epochs using:
- **ROUGE-1** — precision/recall on key terms, improved through Epoch 1
- **ROUGE-2** — peaked at Epoch 1, followed by variation
- **ROUGE-L** — peaked at Epoch 1, indicating refined summarization consistency

Training loss decreased consistently; validation loss showed signs of potential overfitting after Epoch 1 — a key consideration documented for future fine-tuning.

A structured **feasibility study** (technical, economic, operational) and **test-case validation** (dataset loading, preprocessing, model building, prediction) confirmed the system's viability end-to-end.

## Tech Stack

`Python` · `BART (Transformers)` · `Google Text-to-Speech API` · `Google Gemini API` · `NLP pipelines`

## Repository Structure

```
├── summarization/         # BART fine-tuning & inference
├── tts/                    # Google TTS integration
├── quiz_generation/        # Gemini API-based MCQ generation
├── evaluation/             # ROUGE score tracking, test cases
├── paper/                  # published paper (PDF) and citation info
└── README.md
```

## Citation

If you use this work, please cite:
> N. J. Gaddala, T. B. Naidu, V. Valiveti, S. Dara, G. Pandi, "An AI Chatbot for Enhanced Learning Through Speech, Summarization, and Interactive Quizzing," *2025 6th International Conference on Recent Advances in Information Technology (RAIT)*, IEEE, 2025. DOI: 10.1109/RAIT65068.2025.11089260

## Future Work

- Mitigate overfitting observed after Epoch 1 with regularization/early stopping
- Expand language/accent support for voice output
- Adaptive difficulty tuning for generated quizzes
