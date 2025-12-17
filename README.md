# FFT_Transformed_MFCC_Audio_MOS

Two different colab codes were shared. First file named as Feature_Extractor_for_VoiceMOS_2022_dataset.ipynb and used to extract features from Voice MOS 2022 dataset. Second file named as NN_Models_Train_Test_for_VoiceMOS_2022_Data.ipynb and used to describe models and their traning testing processes. In these codes, it was assumed that the Voice MOS dataset was already extracted and saved to local Google Drive folder named as DATA. The extraction of it was explained in its original webpage here: https://zenodo.org/records/6572573. Its last version will be like this:

DATA
  sets
    DEVSET
    TESTDET
    TRAINSET
    train_mos_list.txt
    test_mos_list.txt
    val_mos_list.txt
  wav
    sysff05c-uttfcd6c20.wav
    sysff05c-uttef6436d.wav
    ....
  mydata_system.csv

  In here, wav directory consist of all 4974 train, 1066 validation, 1066 test data total 7106 audio wav files. In feature extractor code, the DATA file location should be arranged according to its new location. The DATA location and the output features location should be defined here:
  
  # Define base paths according to your place
DRIVE_BASE_PATH = #'/content/drive/MyDrive/BUU_PHD_THESIS/datasets_with_MOS/main/main/' # original path is comment out

WAV_DIR = os.path.join(DRIVE_BASE_PATH, 'DATA/wav')
MOS_LISTS_DIR = os.path.join(DRIVE_BASE_PATH, 'DATA/sets')

# Define output feature directories (using /content/ for faster I/O)
OUTPUT_BASE_PATH = #'/content/drive/MyDrive/BUU_PHD_THESIS/VoiceMOS_2022_features' # original path is comment out

TRAIN_OUTPUT_DIR = os.path.join(OUTPUT_BASE_PATH, 'VoiceMOS_2022_train_data_features')
TEST_OUTPUT_DIR = os.path.join(OUTPUT_BASE_PATH, 'VoiceMOS_2022_test_data_features')
VAL_OUTPUT_DIR = os.path.join(OUTPUT_BASE_PATH, 'VoiceMOS_2022_validation_data_features')

The features are grouped into 3 different directories as VoiceMOS_2022_train_data_features, VoiceMOS_2022_train_data_features, VoiceMOS_2022_train_data_features. The overall structure is given in here:

VoiceMOS_2022_features
  VoiceMOS_2022_train_data_features
    mos_scores.npy
    mfcc_features.npy
    utt_ids.npy
  VoiceMOS_2022_validation_data_features
    mos_scores.npy
    mfcc_features.npy
    utt_ids.npy
  VoiceMOS_2022_test_data_features
    mos_scores.npy
    mfcc_features.npy
    utt_ids.npy

In second file, these features are uploaded and used in trainig and testing 5 different designed NN models. To do this, again the locations should be arranged accordingly:


# Define the paths where you saved your data
BASE_FEATURE_DIR = # '/content/drive/MyDrive/BUU_PHD_THESIS/VoiceMOS_2022_features/' => define the location here where main feature directory saved

TRAIN_FEAT_DIR = os.path.join(BASE_FEATURE_DIR, 'VoiceMOS_2022_train_data_features')
VAL_FEAT_DIR = os.path.join(BASE_FEATURE_DIR, 'VoiceMOS_2022_validation_data_features')
TEST_FEAT_DIR = os.path.join(BASE_FEATURE_DIR, 'VoiceMOS_2022_test_data_features')


After feature directory definition, the savepoints for models would be defined in below, which used to save trained models and resume laterwards wimilar to fine tuning in code.


CNN_MLP_CHECKPOINT_PATH = '/content/drive/MyDrive/BUU_PHD_THESIS/Voice_MOS_2022_data_trained_models/CNN_MLP_classic_mos_model.pth'  => DEFINE THEM ACCORDINGLY
RESNET_CHECKPOINT_PATH = '/content/drive/MyDrive/BUU_PHD_THESIS/Voice_MOS_2022_data_trained_models/ResNet18_mos_model.pth'
LSTM_CHECKPOINT_PATH = '/content/drive/MyDrive/BUU_PHD_THESIS/Voice_MOS_2022_data_trained_models/LSTM_mos_model.pth'
GRU_CHECKPOINT_PATH = '/content/drive/MyDrive/BUU_PHD_THESIS/Voice_MOS_2022_data_trained_models/GRU_mos_model.pth'
TRANSFORMER_CHECKPOINT_PATH = '/content/drive/MyDrive/BUU_PHD_THESIS/Voice_MOS_2022_data_trained_models/TRANSFORMER_mos_model.pth'




At last part, the training and testing was done by selecting the model and its save path in here :

# CNN_MLP_CHECKPOINT_PATH
# RESNET_CHECKPOINT_PATH
# LSTM_CHECKPOINT_PATH
# GRU_CHECKPOINT_PATH
# TRANSFORMER_CHECKPOINT_PATH

# model_CNN_MLP
# model_ResNet
# model_LSTM
# model_GRU
# model_Transformer


# --- Execution Variables ---

# select model and checkpoint using above names

selected_model = model_Transformer
selected_path = TRANSFORMER_CHECKPOINT_PATH

local_save_path = '/content/temp_checkpoint.pth' # Use a unique name per model

local_save_path is used to temp save the model, no need to change. The selected model and its path could be selected from given names in comment out code.





