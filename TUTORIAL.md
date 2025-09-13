Using RGLRE for circRNA–miRNA Interaction Prediction
Welcome to the tutorial for RGLRE (Residual Graph Learning framework for circRNA–miRNA interaction prediction).
This guide will walk you through all steps: from raw sequences → feature extraction → training the GNN → visualizing results.

1. Installation
    Clone the repository and install dependencies:
    git clone https://github.com/YourUsername/RGLRE-CMI.git
    cd RGLRE-CMI
    pip install -r requirements.txt

2. Data Preparation
    Input files
    
    1 circRNA sequences → data/circRNA_sequence.csv
    2 miRNA sequences → data/miRNA_sequence.csv
    3 Interaction pairs → data/CMI-9589/9589pairs.csv
    
    Each sequence file should contain either:
    1 column: just sequences, or
    2 columns: [ID, sequence]
    The interaction file should contain at least two columns: circRNA. miRNA

3. Extract Features with DNABERT
    Run the feature extraction script to generate embeddings for circRNAs and miRNAs:
    python src/feature_extraction.py
    
    This produces two files in data/:
    circRNA_Extractedfeatures.csv
    miRNA_Extractedfeatures.csv

4. Train and Evaluate the Model
    Now train the GNN with 5-fold cross-validation:
    python src/main.py
    
    This will:
    Train the Residual Graph Attention Model.
    Print performance metrics: Accuracy, Precision, Recall, F1, AUROC, AUPR.
    Save ROC and PR curves in Figures/.

6. Customization
    Change dataset paths in src/feature_extraction.py and src/main.py.
    Adjust hyperparameters in main.py:
    hidden_dim, dropout, learning_rate, etc.
    Modify the model in src/model.py if you want to test new architectures.

7. Citation
    If you use this framework in your research, please cite:
   Elbashir, M. K., et al. "Residual Graph Learning framework (RGLRE) for circRNA–miRNA interaction prediction using Role-aware Graph Embeddings."
[Scientific Reports, 2025]

