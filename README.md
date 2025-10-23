# GNNFingers Reproduction 

This repository contains a full reproduction of the paper:
> **GNNFingers: A Fingerprinting Framework for Verifying Ownerships of Graph Neural Networks**

All implementations are done in **PyTorch Geometric** and verified in **Google Colab**.

---

##  Folder Structure

```
gnnfingers/
├── Graph_Matching/
│   ├── LINUX/
│   │   ├── Graph_Matching_LINUX.ipynb
│   │   ├── models/
│   │   │   ├── target/
│   │   │   ├── positive/
│   │   │   └── negative/
│   │   ├── verifier/
│   │   └── results/
│   │       ├── evaluation_results.csv
│   │       └── summary.json
│   │
│   └── AIDS/
│       ├── Graph_Matching_AIDS.ipynb
│       ├── models/
│       │   ├── target/
│       │   ├── positive/
│       │   └── negative/
│       ├── verifier/
│       └── results/
│           ├── evaluation_results.csv
│           └── summary.json
│
├── Link_Prediction/
│   ├── Citeseer/
│   │   ├── Link_prediction_Citeseer.ipynb
│   │   ├── models/
│   │   │   ├── target/
│   │   │   ├── positive/
│   │   │   └── negative/
│   │   ├── verifier/
│   │   └── results/
│   │       ├── evaluation_results.csv
│   │       └── summary.json
│   │
│   └── Cora/
│       ├── Link_prediction_Cora.ipynb
│       ├── models/
│       │   ├── target/
│       │   ├── positive/
│       │   └── negative/
│       ├── verifier/
│       └── results/
│           ├── evaluation_results.csv
│           └── summary.json
│
├── Node_Classification/
│   ├── Citeseer/
│   │   ├── Node_classification_Citeseer.ipynb
│   │   ├── models/
│   │   │   ├── target/
│   │   │   ├── positive/
│   │   │   └── negative/
│   │   ├── verifier/
│   │   └── results/
│   │       ├── evaluation_results.csv
│   │       └── summary.json
│   │
│   └── Cora/
│       ├── Node_classification_Cora.ipynb
│       ├── models/
│       │   ├── target/
│       │   ├── positive/
│       │   └── negative/
│       ├── verifier/
│       └── results/
│           ├── evaluation_results.csv
│           └── summary.json
│
└── Graph_Classification/
    └── PROTEIN/
        ├── Graph_classification_PROTEIN.ipynb
        ├── models/
        │   ├── target/
        │   ├── positive/
        │   └── negative/
        ├── verifier/
        └── results/
            ├── evaluation_results.csv
            └── summary.json
```

---

## Setup and Execution

1. Open any `.ipynb` file in **Google Colab**.  
2. Run all cells sequentially — each notebook handles its own dataset and task.  
3. The pipeline automatically:
   - Downloads the dataset (via PyTorch Geometric)
   - Trains a target model
   - Generates positive and negative models
   - Creates graph fingerprints
   - Trains a verifier and evaluates results
4. All trained models and outputs are saved under `/gnnfingers/` folders.

---

##  Summary of Reproduction Results

| Task | Dataset | Model | Paper Accuracy | Reproduced Accuracy |
|------|----------|--------|----------------|---------------------|
| Node Classification | Cora | GCN | 1.00 | 1.00 |
| Node Classification | Citeseer | GraphSAGE | 1.00 | 1.00 | 
| Graph Classification | PROTEIN | GCN | 1.00 | **1.00** |
| Graph Matching | AIDS | SimGNN | 1.00 | 1.00 |
| Graph Matching | LINUX | GCN | 1.00 | 1.00 | 
| Link Prediction | Cora | GCN | 1.00 | 1.00 | 
| Link Prediction | Citeseer | GraphSAGE | 1.00 | 1.00 |

> *Due to GPU limitations, the number of surrogate models (positive/negative) was reduced, but performance remained stable or improved.*

---

##  Novel Research Extension (Ongoing)

I am currently developing an enhancement to **GNNFingers** by integrating **Large Language Models (LLMs)** to intelligently design and evaluate fingerprints.

> "Instead of random or heuristic subgraphs, an LLM can reason about the data's semantics to create highly discriminative fingerprints, or act as an explainable verifier interpreting model responses."

This aims to make model ownership verification more **accurate, explainable, and robust** against fine-tuning or model-stealing attacks.

---
