# 🍲 Multimodal Food Classification (Image + Text)

A deep learning project demonstrating multimodal (image and text) classification using TensorFlow/Keras, specifically designed for execution in a **Google Colab environment** with persistent storage via **Google Drive**.

**Launch the Notebook in Colab:**

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/rghvsrdhtra/Multimodal_Training_Colab/blob/main/Multimodal_Training_Colab.ipynb)

---

## 🚀 Setup & Execution

### Prerequisites

1.  A Google account.
2.  A Google Drive where you can store your dataset and model outputs.

### Google Drive Setup

You must create a folder in your Google Drive to house the project's data and outputs.

1.  Create a folder in your Google Drive (e.g., `Multimodal_Project_Data`).
2.  Inside this main folder, place your dataset following this structure (replace 'Your\_Project\_Folder\_Name' with your actual folder name in the notebook):
    * `/content/drive/My Drive/Your_Project_Folder_Name/images/train/...`
    * `/content/drive/My Drive/Your_Project_Folder_Name/images/test/...`
    * `/content/drive/My Drive/Your_Project_Folder_Name/texts/train_titles.csv`
    * `/content/drive/My Drive/Your_Project_Folder_Name/texts/test_titles.csv`

### 🔄 Performance Optimization: Why Copy Data Locally?

A crucial step in this notebook is copying the image and text files from Google Drive to the local Colab runtime environment (`/content/data`). This is a **performance-critical** step because:

* **Google Drive Latency:** Direct reading from Google Drive, even when mounted, involves high latency and slower I/O operations. This creates a bottleneck when training a deep learning model, as the GPU sits idle waiting for the next batch of data.
* **Speed:** By copying the files to the local Colab file system (SSD storage), data loading and fetching speeds are vastly improved, ensuring the GPU can be fed data quickly and operate at peak efficiency.

### Running the Notebook

1.  Open the notebook via the Colab badge link above.
2.  **Verify the `DRIVE_PROJECT_PATH` variable** in Section 1.2 matches the path to your folder in Google Drive.
3.  Run all cells sequentially.

---

## ⚙️ Key Technologies

* **Platform:** Google Colaboratory (Colab)
* **Storage:** Google Drive (for persistent data and outputs)
* **Deep Learning: TensorFlow 2.x / Keras**
    * Keras was chosen for its **user-friendliness and rapid prototyping capability**. It allows complex architectures, such as this multimodal one that combines a CNN and an RNN, to be built and configured with minimal, clean code. This enables faster research iteration and experimentation.
* **Data Handling:** Pandas, NumPy
* **Vision Model:** EfficientNetB0 (transfer learning from `keras.applications`)
* **Text Model:** LSTM (via Keras Embedding layer)

---

## ✨ Results (Outputs Saved to Drive)

Upon successful training, the following assets will be permanently saved to your specified Google Drive path:

* `best_food_multimodal_model.h5`: The best-performing model weights (saved via `ModelCheckpoint`).
* `text_vectorizer_vocab.pkl`: The pickled vocabulary for the text preprocessing layer.
* `training_accuracy_plot_v2.png`: Plot of training/validation accuracy.
* `training_loss_plot_v2.png`: Plot of training/validation loss.
