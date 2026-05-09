# PulmoScan AI — Lung Cancer Detection using VGG16

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.9%2B-blue?style=for-the-badge&logo=python"/>
  <img src="https://img.shields.io/badge/TensorFlow-2.13%2B-orange?style=for-the-badge&logo=tensorflow"/>
  <img src="https://img.shields.io/badge/Streamlit-1.32%2B-red?style=for-the-badge&logo=streamlit"/>
  <img src="https://img.shields.io/badge/License-Academic-green?style=for-the-badge"/>
</p>

**PulmoScan AI** is a deep learning web application that classifies lung histopathology slides into three categories — **Adenocarcinoma**, **Squamous Cell Carcinoma**, and **Normal** — using a VGG16 transfer learning model trained on the LC25000 dataset.

---

## Live Demo

**Streamlit App:** https://lungcancer-detection-using-vgg16-bxbe8gmaflb3rqdn7vwwn3.streamlit.app/

Upload a lung tissue biopsy image and get an instant AI diagnosis with confidence score and probability breakdown for all three classes.

---

## Features

| Feature | Details |
|---|---|
| Model | VGG16 Transfer Learning (ImageNet weights) |
| Dataset | LC25000 — 25,000 labeled lung histopathology slides |
| Classes | Lung Adenocarcinoma · Lung Normal · Lung Squamous Cell Carcinoma |
| Accuracy | ~96% (Adenocarcinoma), ~99% (Squamous), ~100% (Normal) |
| Speed | Results in under 2 seconds |
| Input | JPG / PNG / TIFF histopathology images |
| Deployment | Streamlit Community Cloud |

---

## Project Structure

```
LungCancer-detection-using-VGG16/
│
├── app.py                    # Main Streamlit application
├── requirements.txt          # Python dependencies
├── lung_cancer_model.h5      # Trained VGG16 model (add to repo)
└── README.md                 # This file
```

---

## Model Architecture

```
VGG16 (pretrained on ImageNet, frozen)
    └── GlobalAveragePooling2D
        └── Dense(1024, relu)
            └── Dense(512, relu)
                └── Dense(3, softmax)   <- 3 lung cancer classes
```

- **Input size:** 224 × 224 × 3 (BGR)
- **Optimizer:** Adam
- **Loss:** Sparse Categorical Crossentropy
- **Training:** 5 epochs on LC25000 dataset

---

## Run Locally

### 1. Clone the repository
```bash
git clone https://github.com/ahmedfadlallah1/LungCancer-detection-using-VGG16.git
cd LungCancer-detection-using-VGG16
```

### 2. Install dependencies
```bash
pip install -r requirements.txt
```

### 3. Add the model file
Place `lung_cancer_model.h5` in the project root directory.

### 4. Run the app
```bash
streamlit run app.py
```

Open your browser at `http://localhost:8501`

---

## Requirements

```
streamlit>=1.32.0
numpy>=1.24.0
opencv-python-headless>=4.8.0
Pillow>=10.0.0
tensorflow-cpu>=2.13.0
keras>=2.13.0
requests>=2.31.0
```

---

## Deploy on Streamlit Cloud

1. Push all files (including `lung_cancer_model.h5`) to your GitHub repo
2. Go to [share.streamlit.io](https://share.streamlit.io)
3. Connect your GitHub repo
4. Set **Main file path** to `app.py`
5. Click **Deploy**


---

## Dataset — LC25000

The model was trained on the **LC25000 Lung and Colon Histopathological Image Dataset**:

- **25,000** total images (lung + colon)
- **3 lung classes** used in this project:
  - `lung_aca` — Lung Adenocarcinoma (malignant)
  - `lung_n` — Lung Normal (benign)
  - `lung_scc` — Lung Squamous Cell Carcinoma (malignant)
- Image resolution: 768 × 768 pixels (resized to 224 × 224 for training)

---

## Note: Disclaimer

> This application is developed **for academic research purposes only** at **Alamein International University**. It is **not** a substitute for professional medical diagnosis. Always consult a licensed medical professional for clinical decisions.

---

## Author

**Ahmed Fadlallah**
Alamein International University — Computer Science

---

## License

This project is for academic use only. The LC25000 dataset is publicly available for research purposes.
