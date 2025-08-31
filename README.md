# 🍔🥗 Food Calorie & Protein Detector  

## 📌 Overview  
This project detects common foods in images using **YOLOv8** and returns their **estimated calories, protein per serving, nutrition score, and advice**.  
The goal is to demonstrate an **end-to-end computer vision pipeline**: dataset preparation → model training → evaluation → prediction overlay with nutrition info.  

---

## 📂 Dataset  
- ~300 labeled images across **7 food classes**:  
  - `pizza`, `burger`, `fries`, `fried-egg`, `cereal`, `salad`, `steak`  
- Images manually labeled/ pre labelled in **Roboflow**, exported in YOLO format.  
- Train/val/test split configured via `data.yaml`.  

> Full dataset is available separately here: [Roboflow Link](https://app.roboflow.com/ds/qJsgBisufh?key=DYRO4x17CP)  
> (Repo only includes a few sample images for demo.)  

---

## ⚙️ Training  
- **Model:** YOLOv8n (fine-tuned from pretrained weights)  
- **Epochs:** 50  
- **Input size:** 640×640  
- **Frameworks:** `ultralytics`, `pytorch`, `opencv`, `pillow`  

Training code: [`notebooks/00_train.ipynb`](notebooks/00_train.ipynb)  

---

## 📊 Results  

- **mAP@0.5 (all classes): 0.86**  
- Strongest classes: Pizza, Fried-Egg, Cereal (>0.99)  
- Weaker classes: Fries, Steak (~0.67)  

| Metric      | Value |
|-------------|-------|
| mAP@0.5     | 0.859 |
| Precision   | 0.82  |
| Recall      | 0.94  |

### Curves & Plots  

<p align="center">
  <img src="results/BoxF1_curve.png" width="45%">
  <img src="results/BoxP_curve.png" width="45%">
</p>  

<p align="center">
  <img src="results/BoxPR_curve.png" width="45%">
  <img src="results/confusion_matrix_normalized.png" width="45%">
</p>  

<p align="center">
  <img src="results/results.png" width="70%">
</p>  

---

## 🖼️ Predictions with Nutrition Footer  

Each prediction includes:  
- Calories & protein per serving  
- Nutrition grade (A–D)  
- Food-specific advice (e.g., *“Add lean protein to balance this meal”*)  

### Example Outputs  

<p align="center">
  <img src="sample_results/1.jpg" width="45%">
  <img src="sample_results/2.jpg" width="45%">
</p>  

<p align="center">
  <img src="sample_results/3.jpg" width="45%">
  <img src="sample_results/4.jpg" width="45%">
</p>  

<p align="center">
  <img src="sample_results/5.jpg" width="45%">
  <img src="sample_results/6.jpg" width="45%">
</p>  

Code: [`src/03_predict_footer_msg.py`](src/03_predict_footer_msg.py)  

---

## ▶️ How to Run  

### 1. Clone & install dependencies  
```bash
git clone https://github.com/yourname/food-calorie-detector.git
cd food-calorie-detector
pip install -r requirements.txt
