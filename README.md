#🫁 Multi-Disease Chest X-ray AI System
A modular deep learning system that runs multiple independent chest X-ray models — Tuberculosis, COVID-19, and NIH Multi-Disease — in parallel on a single input image, with PDF report generation and Grad-CAM explainability.

⚠️ Research / Educational Use Only. Not intended for clinical diagnosis.

Features
Three independent disease-specific models running in parallel with no label interference
Grad-CAM explainability for TB and COVID-19 detection (heatmap overlays)
Multi-label prediction for 14 NIH chest pathologies using sigmoid output
Patient information capture — ID, name, age, gender, referring physician
Multi-image support — analyze up to 3 X-rays per session
Automated PDF report generation with findings, heatmaps, and summary table
Streamlit-based UI with a clean black-and-white clinical aesthetic
Fully local deployment — no cloud dependency, VS Code ready
System Overview
The application orchestrates three independent inference pipelines:

Model	Architecture	Task	Output
Tuberculosis Detection	ResNet-based	Binary classification	TB Positive / Negative + confidence
COVID-19 Detection	DenseNet-based	Binary classification with risk mapping	COVID Positive / Negative + confidence
NIH Multi-Disease Detection	DenseNet-based	Multi-label classification	14 pathology probabilities (sigmoid)
Each model is trained, loaded, and executed independently to preserve interpretability and avoid cross-label interference.

Project Structure
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

How to Run
1. Clone the repository

git clone https://huggingface.co/devikand/Multi_disease-chest-xray-ai
cd Multi_disease-chest-xray-ai

2. Install dependencies

pip install -r requirements.txt

3. Launch the app

streamlit run app.py

Then open your browser at http://localhost:8501

Usage
Fill in the Patient Information fields (Patient ID is required)
Upload 1–3 chest X-ray images (PNG, JPG, or JPEG)
Click "Analyze All X-rays"
View per-image results for TB, COVID-19, and NIH pathologies
Download the auto-generated combined PDF report
Output
For each X-ray, the system produces:

TB classification result with confidence score and Grad-CAM heatmap
COVID-19 classification result with confidence score and heatmap (where applicable)
NIH multi-disease probabilities with a bar chart visualization
A downloadable PDF medical report including all findings, images, and a summary table
Dependencies
Key libraries used:

streamlit — UI framework
torch / torchvision — model inference
opencv-python — image processing
matplotlib — visualizations
reportlab — PDF report generation
Install all via:

pip install -r requirements.txt

Models
The three models are loaded independently at inference time. Model weights should be placed in their respective module directories (tb/, covid/, multi_disease/) or configured within each infer.py file.

Limitations
This system is built for research and educational purposes only
Model performance depends on training data distribution — results may not generalize to all clinical settings
Grad-CAM heatmaps are approximations and should not be used as sole diagnostic indicators
Not validated for clinical deployment
License
This project is intended for academic and research use. Please review model licenses before any commercial application.
