# 🫁 Multi-Disease Chest X-ray AI System

the whole project is stored in : [huggingface_hub](https://huggingface.co/devikand/Multi_disease-chest-xray-ai)

A modular deep learning system that runs multiple independent chest X-ray models in parallel on a single input image.

> ⚠️ **Research / Educational Use Only. Not intended for clinical diagnosis.**

---

## 🔍 Overview

This system detects three categories of chest conditions independently:

- **Tuberculosis** — ResNet-based binary classification
- **COVID-19** — DenseNet-based binary classification with risk mapping
- **NIH Multi-Disease** — DenseNet-based multi-label classification across 14 pathologies

Each model is trained, loaded, and executed independently to avoid label interference and preserve interpretability.

---

## ✨ Features

- Three independent disease-specific deep learning models
- Parallel inference on a single X-ray input
- Grad-CAM explainability for TB and COVID-19 (heatmap overlays)
- Multi-label prediction support for 14 NIH chest pathologies
- Patient information capture (ID, name, age, gender, physician)
- Analyze up to 3 X-rays per session
- Auto-generated PDF medical report with findings and summary
- Clean Streamlit-based UI
- Fully local deployment — no cloud required, VS Code ready

---

## 🗂️ Project Structure

```
├── app.py                  # Main Streamlit application
├── tb/
│   ├── infer.py            # TB inference pipeline
│   └── grad_cam.py         # Grad-CAM for TB model
├── covid/
│   └── infer.py            # COVID-19 inference pipeline
├── multi_disease/
│   └── infer.py            # NIH multi-disease inference pipeline
├── requirements.txt
└── README.md
```

---

## 🚀 How to Run

**Step 1 — Clone the repository**

```bash
git clone https://huggingface.co/devikand/Multi_disease-chest-xray-ai
cd Multi_disease-chest-xray-ai
```

**Step 2 — Install dependencies**

```bash
pip install -r requirements.txt
```

**Step 3 — Launch the app**

```bash
streamlit run app.py
```

Open your browser at `http://localhost:8501`

---

## 🖥️ Usage

1. Fill in the **Patient Information** fields (Patient ID is required)
2. Upload **1 to 3 chest X-ray images** (PNG, JPG, or JPEG)
3. Click **"Analyze All X-rays"**
4. View results for TB, COVID-19, and NIH pathologies per image
5. Download the auto-generated **Combined PDF Report**

---

## 📄 Output

For each X-ray, the system produces:

- TB classification with confidence score and Grad-CAM heatmap
- COVID-19 classification with confidence score and heatmap (where applicable)
- NIH multi-disease probabilities with bar chart visualization
- A downloadable PDF report with all findings, images, and a summary table

---

## 🧰 Dependencies

| Library | Purpose |
|---|---|
| `streamlit` | UI framework |
| `torch` / `torchvision` | Model inference |
| `opencv-python` | Image processing |
| `matplotlib` | Visualizations |
| `reportlab` | PDF report generation |

Install all dependencies:

```bash
pip install -r requirements.txt
```

---

## ⚙️ Model Weights

Model weights should be placed inside their respective module directories (`tb/`, `covid/`, `multi_disease/`) or configured within each `infer.py` file before running the app.

---

## ⚠️ Limitations

- Built for research and educational purposes only
- Results may not generalize across all clinical settings
- Grad-CAM heatmaps are approximations and not standalone diagnostic tools
- Not validated for clinical deployment

---

## 📜 License

This project is intended for academic and research use.
Please review individual model licenses before any commercial application.
