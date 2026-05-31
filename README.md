# Alzheimer’s Disease Classification from Structural MRI Using Three-View Transfer Learning and Similarity-Based Retrieval

This project focuses on classifying Alzheimer's disease stages from structural MRI scans using a transfer learning approach combined with similarity-based case retrieval. By leveraging deep learning and medical imaging techniques, the project aims to support early diagnosis while improving model interpretability through clinically relevant case comparisons.

## Project Overview

Alzheimer’s disease (AD) is a progressive neurodegenerative disorder and one of the leading causes of dementia worldwide. Early and accurate diagnosis is essential for timely intervention, improved patient management, and better long-term outcomes.

This project utilizes structural MRI scans from the Alzheimer's Disease Neuroimaging Initiative (ADNI) dataset to classify patients into three diagnostic categories:

* Cognitively Normal (CN)
* Mild Cognitive Impairment (MCI)
* Alzheimer's Disease (AD)

To improve transparency and clinical usability, the project combines:

* Three-view MRI representation (Axial, Coronal, Sagittal)
* Transfer Learning using ResNet18
* Similarity-Based Retrieval using FAISS
* Retrieval-Based Classification
* Automated Clinical Report Generation
* LLM-Enhanced Clinical Interpretation

## Project Structure

### Data Preprocessing & Exploratory Analysis

The initial phase focuses on understanding and preparing the MRI data:

#### Exploratory Data Analysis (EDA)

* Analysis of diagnostic class distribution.
* Subject-level and longitudinal scan analysis.
* Age and sex distribution assessment.
* MRI visualization and quality inspection.

#### Data Preparation

* Subject-level splitting to prevent data leakage.
* Training, validation, and test set creation.
* Metadata integration and label mapping.

### MRI Preprocessing & Three-View Extraction

The MRI volumes undergo a standardized preprocessing pipeline:

#### MRI Preprocessing

* Orientation alignment.
* Voxel resampling.
* Intensity normalization.
* Spatial cropping.
* Standardized volume preparation.

#### Three-View Representation

Three anatomical views are extracted from each MRI volume:

* Axial View
* Coronal View
* Sagittal View

These views are stacked into a three-channel image that can be processed by pretrained convolutional neural networks.

### Deep Learning & Transfer Learning

The core of the project involves building a deep learning classification pipeline:

#### Model Architecture

* Pretrained ResNet18
* Transfer Learning Strategy
* Fine-Tuning of Classification Layers

#### Training Configuration

* Cross-Entropy Loss
* Adam Optimizer
* Class Weighting for Imbalanced Data
* Validation-Based Model Selection

### Model Evaluation

Performance is assessed using multiple classification metrics:

* Accuracy
* Precision
* Recall
* F1-Score
* Confusion Matrix

The model is evaluated on a completely unseen test set using subject-level separation.

### Similarity-Based Retrieval (FAISS)

To improve interpretability, the project implements a similarity-based retrieval system.

#### Embedding Extraction

* Deep features are extracted from the trained CNN.
* MRI scans are represented in a learned latent feature space.

#### FAISS Indexing

* Fast Approximate Nearest Neighbor Search (FAISS)
* Efficient retrieval of similar patient cases

#### Case-Based Interpretation

For each query patient:

* Similar historical cases are retrieved.
* Diagnostic labels of nearest neighbors are analyzed.
* Predictions are supported by clinically comparable examples.

### Retrieval-Based Classification

The learned embeddings are also used for classification through similarity-based reasoning.

#### k-Nearest Neighbour Classification

* Classification based on retrieved cases.
* Comparison with CNN predictions.
* Evaluation of embedding-space quality.

### Clinical Report Generation

To make predictions more clinically meaningful, the project generates structured reports.

#### Template-Based Reports

* Predicted diagnosis
* Similar patient evidence
* Confidence summary
* Retrieval explanations

#### LLM-Enhanced Reports

* Natural language clinical summaries
* Improved readability and interpretability
* Evidence-grounded report generation

### Report Export

Generated reports can be exported as PDF documents for presentation and clinical review.

## Dataset Variables

The project uses structural MRI scans and associated clinical metadata from the ADNI dataset.

### Input Features

* Structural MRI Brain Scans
* Subject Information
* Diagnostic Labels
* Demographic Variables

### Target Variable

**Diagnostic Category**

* CN = Cognitively Normal
* MCI = Mild Cognitive Impairment
* AD = Alzheimer's Disease

## Technologies Used

* Python
* Pandas
* NumPy
* Matplotlib
* Seaborn
* PyTorch
* Torchvision
* MONAI
* Nibabel
* Scikit-Learn
* FAISS
* OpenAI API
* ReportLab

## How to Run

To replicate the analysis and model training, follow these steps:

### 1. Clone the Repository

```bash
git clone https://github.com/nour-abuhassira/Alzheimers-Disease-Classification.git
cd Alzheimers-Disease-Classification
```

### 2. Install Required Libraries

```bash
pip install pandas numpy matplotlib seaborn scikit-learn torch torchvision monai nibabel faiss-cpu openai reportlab
```

### 3. Prepare the Dataset

Download and organize the ADNI MRI dataset and metadata files according to the project structure.

### 4. Execute the Notebook

Open and run:

```bash
Alzheimers_Disease_Classification.ipynb
```

to view the complete pipeline including preprocessing, exploratory analysis, transfer learning, similarity-based retrieval, evaluation, and report generation.

## Key Outcomes

* Developed an end-to-end MRI-based Alzheimer's disease classification pipeline.
* Applied transfer learning using a pretrained ResNet18 architecture.
* Implemented a three-view MRI representation for efficient deep learning.
* Built a similarity-based retrieval system using FAISS.
* Compared direct CNN classification with retrieval-based classification.
* Generated explainable clinical reports supported by similar patient evidence.
* Enhanced report generation using large language models (LLMs).
* Improved interpretability of medical AI predictions through case-based reasoning.
