# Project 02: Urdu Conversational Chatbot (From Scratch)

This repository contains the complete code and associated files for the "Urdu Conversational Chatbot" assignment. The project involves building a Transformer (Encoder-Decoder) model from scratch using PyTorch to handle contextual Urdu text.

Due to the nature of the provided dataset, the task was implemented as a **Denoising Sentence Completion** model. The model is trained to predict the second half of a sentence based on a corrupted (masked) version of the first half.

---

## Repository Contents

* `Urdu_Chatbot_Project.ipynb`: The main Kaggle notebook containing all 26 steps (Data loading, Preprocessing, Model Architecture, Training, and Evaluation).
* `best_model.pth`: The final, trained PyTorch model weights (saved based on the best Validation BLEU score).
* `urdu_spm.model`: The trained SentencePiece tokenizer model.
* `evaluation_report.docx`: A detailed report summarizing the project's methodology, results, and limitations.
* `qualitative_results.png`: A screenshot of the model's best qualitative results.
* `requirements.txt`: A list of all required Python packages to run the project.

---

## How to Run

### 1. Dataset

This model was trained on the "Urdu Conversational Dataset" available on Kaggle.
[cite_start]**Link:** [https://www.kaggle.com/datasets/muhammadahmedansari/urdu-dataset-20000](https://www.kaggle.com/datasets/muhammadahmedansari/urdu-dataset-20000) [cite: 12]

### 2. Environment Setup

It is highly recommended to run this notebook in a GPU-enabled environment like Kaggle or Google Colab.

1.  Clone this repository (or download the files).
2.  Install all required dependencies:
    ```bash
    pip install -r requirements.txt
    ```

### 3. Running the Project

1.  Upload the `.ipynb` file, `best_model.pth`, and `urdu_spm.model` to your environment (Kaggle/Colab).
2.  Ensure the Kaggle dataset is added to the notebook environment (at `/kaggle/input/urdu-dataset-20000/`).
3.  Open the `Urdu_Chatbot_Project.ipynb` notebook and run the cells sequentially.
    * **To re-train the model:** Run all cells from the beginning.
    * **To run the demo (Gradio UI):** Run cells 1-4 (Setup), 9 (Load Tokenizer), 12-18 (Model Architecture), 22 (Load `best_model.pth`), 24 (Inference Fn), and 25 (Gradio UI).

---

## Final Results (Test Set)

| Metric | Score | Analysis |
| :--- | :--- | :--- |
| **BLEU** | 0.1192 | Proves the model is generating valid word sequences (non-zero score). |
| **chrF** | 0.1057 | Shows valid character-level n-gram matches. |
| **Perplexity** | 274.7 | High PPL indicates significant overfitting due to the small dataset (19k pairs) for a large (8.7M param) model. |

### Qualitative Results

The model successfully learned real-world associations (see `qualitative_results.png` for details), such as associating "Lahore" with "Qalandars" and completing political phrases.
