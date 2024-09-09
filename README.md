# Engineered_CDRH3_MMP9_Binding
# Predicting binding affinity between CDRH3 and MMP9 inhibitors.
  This GitHub repository contains the training file and the model used to predict the binding affinity between synthesized CDRH3 and the MMP9 inhibitors. The 'Models' directory contains all the saved models to load and infer new CDRH3 sequences. 'The training_data' folder contains the cleaned original input data used to train, validate, and test the models.
# Training Data
  TThere are 2,596 unique CDRH3 sequences in the library, with 2,378 having binding affinity and 218 having non-binding affinity. After stratifided shuffling, 1660 CDRH3s were used for training, 416 were used for validation, and the remaining 520 were used for testing the models. The file contains the following columns
    1. Binding - (Positive or Negative)
    2. Binding_Labels - 1 (Positive) or 0 (Negative)
    3. Full_AA_Sequence - This is full aminoacid sequence. This is same as CDRH3 as we use only CDRH3 sequence and not the full sequence.
    4. Count
    5. Start_Idx - This is the start index of the CDRH3 sequence in the full sequence. Since both the CDRH3 and the full sequence are the same, the start index is always zero.
    6. CDRH3_Length - the length (number of aminoacids) of CDRH3 sequence.
# Computation model
  Two pretrained LPLMs were used for extracting the features from the CDRH3 sequences: the Evolutionary Scale Modeling (ESM)-2 models (with 650B, 3B, and 15B parameters) and the AntiBERTy model with 26M parameters. Embeddings extracted for each amino acid position in CDRH3 were padded to the same length and used to train a downstream LSTM model to predict binding affinity with MMP-9.

![image](https://github.com/user-attachments/assets/50ecf7c8-1995-4cd6-a2eb-945cc6b6114a)
# cdrh3-mmpg-inference.py
  The Python module 'cdrh3-mmp9-inference.py' contains the code to infer the binding affinity by passing the CDRH3 sequences and the pretrained PLM to use. The inference returned will contain the CDRH3 sequence, corresponding binding affinity (positive or negative), and the confidence level.
# The notebook Syn_CDRH3_MMP9_Binding_Inference.ipynb
  This Python notebook contains the interactive code to predict the binding affinity between the synthesized CDRH3 and mmp9 inhibitors. Please click the link (https://colab.research.google.com/drive/1n39KvMrcl4VOJZDpcpf5mjF9f7WAt2rE?usp=sharing) to access the note book. Please follow the instructions on the notebook.
