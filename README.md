# Brain Tumor Segmentation using Attention U-Net

An end-to-end deep learning pipeline for automatic brain tumor 
segmentation from MRI scans, with an interactive Gradio demo app.

## Results
| Metric | Our Model | 2017 U-Net Paper |
|--------|-----------|-----------------|
| Dice Score | 0.8388 | ~0.84 |
| IoU Score | 0.7270 | Not reported |

## Architecture
- **Model:** Attention U-Net with Residual Blocks
- **Input:** RGB MRI slices (256×256)
- **Output:** Binary tumor segmentation mask
- **Parameters:** 32.7 Million
- **Loss:** Combined Dice + BCE Loss
- **Optimizer:** Adam with Cosine Annealing LR

## Key Improvements Over Original Paper
- Attention gates focus model on tumor regions
- Residual connections for better gradient flow
- Combined Dice + BCE loss for stability
- IoU metric added (paper never reported this)
- Full Gradio deployment pipeline
- Mixed precision training (2x faster)

## Dataset
- LGG Brain MRI Segmentation Dataset
- 112 patients, 3929 image-mask pairs
- Source: Kaggle (mateuszbuda/lgg-mri-segmentation)

## How to Run

### 1. Install dependencies
pip install -r requirements.txt

### 2. Train the model
Run all cells in brain_tumor_segmentation.ipynb

### 3. Launch demo app
The Gradio app launches automatically at the end of the notebook

<img width="1687" height="912" alt="image" src="https://github.com/user-attachments/assets/e0ecf387-faf2-4abe-a845-2f414879d8e4" />


## Project Structure
```
brain-tumor-segmentation/
├── brain_tumor_segmentation.ipynb  ← main notebook
├── requirements.txt                ← dependencies  
├── best_model.pth                  ← trained weights
├── training_curves.png             ← loss/dice plots
├── predictions_8samples.png        ← results
└── README.md                       ← this file
```

## What This Project Does
Given a brain MRI slice, the model automatically highlights 
the tumor region in red. This can help doctors:
- Save hours of manual annotation time
- Get consistent, reproducible measurements
- Track tumor growth/shrinkage over time
- Plan surgery with precise tumor boundaries

## References
- Ronneberger et al., U-Net (2015)
- Oktay et al., Attention U-Net (2018)  
- Dong et al., Brain Tumor Segmentation with U-Net (2017)
- LGG MRI Dataset: Buda et al. (2019)
