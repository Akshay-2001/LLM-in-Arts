# LLMs in Arts: Music Genre Classification & Chord Progression Generation

This project explores the intersection of **Natural Language Processing (NLP)** and **music**, applying fine-tuned large language models (LLMs) to:
- **Task 1:** Classify a song's genre from its lyrics.
- **Task 2:** Generate appropriate chord progressions from lyrics.

Developed as part of my NLP course milestone, the solution combines deep learning, transfer learning, and model deployment using Hugging Face models and Streamlit/Gradio UI.

---

## Features

-  **Music Genre Classification**:
  - Predicts genres like pop, rock, hip-hop, etc. from lyrics.
  - Models used: `meta-llama/Llama-3.1-8B`, `FacebookAI/roberta-base`, custom `BiLSTM-GRU`.

-  **Chord Progression Generation**:
  - Generates chord sequences from lyrical themes.
  - Model used: `TinyLlama-v1.1` (decoder-only, LoRA-fine-tuned).

-  Evaluation with **BERTScore** to assess semantic alignment.

-  Deployment via **Gradio** for interactive lyric input and prediction.

---

##  Models & Techniques

### Task 1: Genre Classification
- **LLaMA 3.1 8B**:
  - Fine-tuned using QLoRA + 4-bit quantization.
  - Trainer used with gradient accumulation.

- **RoBERTa-base**:
  - Fine-tuned using predictions from a custom BiLSTM-GRU model.
  - Trained for 5 epochs with early stopping.

- **BiLSTM-GRU**:
  - Custom classifier trained on top 100 genres.
  - Used as a feature augmenter for RoBERTa.

### Task 2: Chord Progression Generation
- **TinyLlama v1.1**:
  - Fine-tuned with LoRA and PEFT.
  - Used 4-bit quantization for efficient memory use.

---

##  Results

### Task 1: BERTScore
| Model     | Precision | Recall  | F1 Score |
|-----------|-----------|---------|----------|
| LLaMA     | 0.7436    | 0.8026  | 0.7715   |
| RoBERTa   | **0.9349**| **0.8927** | **0.9119** |

### Task 2: Chord Progression (TinyLlama)
| Metric    | Score     |
|-----------|-----------|
| Precision | 0.7715    |
| Recall    | 0.7694    |
| F1 Score  | 0.7700    |

---

##  Deployment

- Web UI built with **Gradio**
- Users can:
  - Input lyrics
  - Choose between genre classification or chord generation
  - View predictions in real-time

>  Requires GPU for model loading due to resource-intensive models.

---

##  Future Work

- Optimize deployment for real-time usage with lower GPU usage
- Incorporate audio features and staff notation
- Integrate with DAWs (Digital Audio Workstations) for music production
- Expand training data to improve model diversity and generalization

---

##  References

1. [Genius Expertise Dataset](https://www.cs.cornell.edu/~arb/data/genius-expertise/)
2. [MusicPile Dataset](https://huggingface.co/datasets/m-a-p/MusicPile)
3. [LLaMA 3.1 Model](https://huggingface.co/meta-llama/Llama-3.1-8B)
4. [RoBERTa-base Model](https://huggingface.co/FacebookAI/roberta-base)

---

