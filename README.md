# Deep Neural Network Based Intrusion Detection System

A Deep Neural Network (DNN) based Intrusion Detection System (IDS) implemented using the NSL-KDD dataset and TensorFlow/Keras.

## Reference Paper

Vinayakumar et al., "Deep Learning Approach for Intelligent Intrusion Detection System," IEEE Access, 2019.

## Dataset

The project uses the NSL-KDD dataset:
- KDDTrain+.txt
- KDDTest+.txt

The dataset is downloaded automatically by the notebook.

The original 41 NSL-KDD traffic features are used. The difficulty field is excluded from the model input.

## Preprocessing

The categorical features protocol_type, service, and flag are processed using One-Hot Encoding.

The numerical features are standardized using StandardScaler.

The preprocessing objects are fitted using the training data and then applied to the test data.

## DNN Architecture

The model contains five fully connected hidden layers.

Each hidden layer contains:
- 1024 neurons
- Batch Normalization
- ReLU activation
- Dropout = 0.01

The optimizer is Adam with a learning rate of 0.001.

## Binary Classification

The binary model uses:
- 1 output neuron
- Sigmoid activation
- Binary Cross-Entropy loss

Classes:
- Normal
- Attack

## Multi-Class Classification

The multi-class model uses:
- 5 output neurons
- Softmax activation
- Sparse Categorical Cross-Entropy loss

Classes:
- Normal
- DoS
- Probe
- R2L
- U2R

## Evaluation Metrics

The system evaluates:
- Accuracy
- Precision
- Recall / True Positive Rate
- False Positive Rate
- F1 Score
- ROC-AUC

The project also generates training curves, confusion matrices, ROC curves, classification reports, and class-wise performance metrics.

## Results

| Metric | Binary | Multi-Class |
|---|---:|---:|
| Accuracy | 79.51% | 76.81% |
| Precision | 96.25% | 72.13% |
| Recall / TPR | 66.59% | 50.82% |
| FPR | 3.43% | 7.82% |
| F1 Score | 78.72% | 51.60% |
| ROC-AUC | 86.52% | 82.80% |

These results are specific to this implementation and should not be interpreted as the exact results reported in the reference paper.

## Repository Structure

```text
nsl-kdd-dnn-ids/
|-- README.md
|-- requirements.txt
|-- .gitignore
|-- notebooks/
|   `-- NSL_KDD_DNN_IDS.ipynb
|-- models/
|   |-- nsl_kdd_dnn_binary.keras
|   `-- nsl_kdd_dnn_multiclass.keras
|-- preprocessors/
|   |-- onehot_encoder.pkl
|   `-- standard_scaler.pkl
`-- results/
```

## How to Run

Install dependencies:

```bash
pip install -r requirements.txt
```

Open:

notebooks/NSL_KDD_DNN_IDS.ipynb

The notebook downloads the NSL-KDD dataset automatically and performs preprocessing, training, and evaluation.

## Technologies

- Python
- TensorFlow
- Keras
- Scikit-learn
- NumPy
- Pandas
- Matplotlib
- Seaborn

## Disclaimer

This repository is an educational/research implementation of a deep-learning-based intrusion detection system. Performance can vary depending on preprocessing, hyperparameters, random seed, TensorFlow version, and hardware.