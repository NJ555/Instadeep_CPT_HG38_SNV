# Instadeep_CPT_HG38_SNV
🧬 SNV-Based Pathogen Ranker using InstaDeep 500M Transformer

A deep learning framework for pathogenicity ranking of Single Nucleotide Variants (SNVs) using representation learning from the InstaDeep 500M parameter genomic transformer and BF16 training. The model learns biologically meaningful DNA representations and achieves strong predictive performance with high recall and ROC-AUC.

## 📌 Overview

This project presents an end-to-end pipeline for building a high-performance SNV pathogenicity ranking system. The system leverages large-scale genomic transformer embeddings combined with curated clinical and population features.

---

## Key highlights:

Uses pretrained InstaDeep 500M genomic transformer for DNA representation learning

Custom SNV dataset constructed by integrating multiple genomic databases

Trained using BF16 precision for efficient large-model training

Achieves high recall and ROC-AUC performance

Includes ablation studies and SHAP-based interpretability analysis

Demonstrates that DNA sequence features are dominant predictors

🧠 Model Architecture

Base model: InstaDeep Genomic Transformer (500M parameters)

Input components:

DNA sequence embeddings from transformer

Clinical annotations

Population frequency features

Functional annotations

Training setup:

Precision: BF16

Task: Binary classification (Pathogenic vs Benign)

Objective: Pathogenicity ranking

Framework: PyTorch

📊 Results
Metric	Score
ranking TOP 10% =75%

These results demonstrate strong discrimination ability and effective pathogenic variant prioritization.

🧬 Dataset Construction

The dataset was built from scratch to ensure high quality and prevent information leakage.

Data Sources

ClinVar

dbNSFP

hg38 reference genome

gnomAD population database

Processing Steps

Extracted SNVs from integrated genomic databases

Mapped variants to hg38 reference genome

Combined clinical, functional, and population features

Removed leakage-prone identifiers:

HGVS IDs

Variant identifiers

Direct labels encoded in features

Eliminated identity leakage and duplicate variants

Ensured strict train-test separation

This ensured the model learned biological patterns rather than memorizing identifiers.

🔬 Feature Importance Analysis (SHAP)

SHAP analysis was performed to understand model decision behavior.

Key findings:

DNA sequence features: 65% contribution

Clinical and annotation features combined: 35% contribution

This confirms that the transformer successfully learned meaningful biological representations from raw DNA.

📈 SHAP Visualizations
Global feature importance

SHAP summary plot

🧪 Ablation Studies

Ablation experiments were conducted to evaluate contribution of each component.

Configuration	ROC-AUC
Full model	0.91

![modality score feature importance](https://github.com/user-attachments/assets/d835d6d4-90c7-461f-b913-3ca3ebcad23c)
![ablation studies](https://github.com/user-attachments/assets/a6a7fb8f-0b9c-4a51-82a9-90a767910de5)
![shap](https://github.com/user-attachments/assets/67080ca5-3a43-422b-aa50-180584ba1bd3)




🚀 Key Contributions

Built a leakage-free SNV pathogenicity dataset from multiple genomic sources

Successfully applied large genomic transformer embeddings to pathogenicity ranking

Demonstrated strong performance with ROC-AUC of 0.91

Showed biological validity using SHAP interpretability

Verified model robustness through ablation studies

Proved DNA representation learning is dominant signal (65% importance)

💡 Why This Works

The model achieves strong performance because it learns directly from DNA sequence context using a large pretrained genomic transformer. Unlike traditional models relying mostly on clinical annotations, this approach captures biological patterns embedded in genomic sequences.

🔮 Future Work

Extend to other variant types (insertions, deletions)

Train on larger genomic datasets

Fine-tune full transformer instead of feature extraction

Deploy as clinical decision support tool
