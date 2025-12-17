# FFT Transformed MFCC Audio MOS

This repository contains the implementation for predicting Mean Opinion Score (MOS) from audio files using FFT-transformed MFCC features. The project is split into two main phases: feature extraction and neural network training/testing.

## 📁 Repository Structure

* `Feature_Extractor_for_VoiceMOS_2022_dataset.ipynb`: Processes the raw VoiceMOS dataset into training-ready features.
* `NN_Models_Train_Test_for_VoiceMOS_2022_Data.ipynb`: Implements, trains, and evaluates 5 different architectures (CNN-MLP, ResNet18, LSTM, GRU, and Transformer).

---

## 🛠️ Step 1: Data Preparation

The code uses the **VoiceMOS 2022 Dataset**. You must download and organize the data before running the notebooks.

1. **Download:** Get the dataset from the [Official Zenodo Repository](https://zenodo.org/records/6572573).
2. **Organization:** Ensure your data folder (named `DATA`) follows this structure:

```text
DATA/
├── sets/
│   ├── DEVSET
│   ├── TESTSET
│   ├── TRAINSET
│   ├── train_mos_list.txt
│   ├── test_mos_list.txt
│   └── val_mos_list.txt
├── wav/
│   ├── sysff05c-uttfcd6c20.wav (Total 7106 .wav files)
│   └── ...
└── mydata_system.csv
```

---

## 🧪 Step 2: Feature Extraction

Open Feature_Extractor_for_VoiceMOS_2022_dataset.ipynb. You need to point the code to your data location.

Required Changes: Update the following variables in the notebook to match your Google Drive or local path:
```text
DRIVE_BASE_PATH = 'path/to/your/DATA_folder' 
OUTPUT_BASE_PATH = 'path/to/save/features'
```


The notebook will generate the following feature structure:
```text
VoiceMOS_2022_features/
├── VoiceMOS_2022_train_data_features/       (mos_scores.npy, mfcc_features.npy, utt_ids.npy)
├── VoiceMOS_2022_validation_data_features/  (...)
└── VoiceMOS_2022_test_data_features/        (...)
```


---

## 🤖 Step 3: Model Training & Evaluation

Open NN_Models_Train_Test_for_VoiceMOS_2022_Data.ipynb to train the models.

1. Set Feature Paths
Update BASE_FEATURE_DIR to point to the features generated in Step 2.

2. Set Checkpoint Paths
Define where you want to save the trained .pth models:

* `CNN_MLP_CHECKPOINT_PATH`
* `RESNET_CHECKPOINT_PATH`
* `LSTM_CHECKPOINT_PATH`
* `GRU_CHECKPOINT_PATH`
* `TRANSFORMER_CHECKPOINT_PATH`

3. Select Model for Execution
In the Execution Variables section, choose which model to run by assigning the selected_model and selected_path:
```text
# Example: Running the Transformer Model
selected_model = model_Transformer
selected_path = TRANSFORMER_CHECKPOINT_PATH
```


---

## 📊 Models Implemented

This research compares five different architectures:

* `CNN-MLP`: Classic convolutional layers combined with multi-layer perceptron.
* `ResNet18`: Residual networks for deep feature learning.
* `LSTM`: Long Short-Term Memory for sequential audio dependencies.
* `GRU`: Gated Recurrent Units.
* `Transformer`: Attention-based architecture for global context.







