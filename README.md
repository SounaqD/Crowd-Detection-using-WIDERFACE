# Crowd Face Detection Using Classical and Deep Learning Approaches

This repository contains the implementation and benchmarking of multiple face-detection models on the challenging **WIDER FACE** dataset. The project compares classical and modern deep-learning models under heavy occlusion, tiny faces, illumination changes, and crowd density.

---

## 📌 Overview

This study evaluates four face-detection models:

- **Viola–Jones** (Haar Cascade)
- **RetinaFace** (anchor-based)
- **Faster R-CNN** (two-stage detector)
- **YOLOv8n-Face** (anchor-free, lightweight)

Models are tested using precision, recall, F1-score, and IoU.

---

## 📂 Dataset: WIDER FACE

The benchmark dataset used:

- **32,203 images**
- **393,703 annotated faces**
- High variation in scale, pose, illumination, and crowd density

**Split:**
- 50% Training  
- 10% Validation  
- 40% Testing  

Minimal augmentation was used due to GPU memory constraints.

---

## 🧠 Models Evaluated

### 1. Viola–Jones (Haar Cascade)
- Fast and lightweight  
- Works for frontal faces  
- Poor performance on small, rotated, or occluded faces  

### 2. RetinaFace
- Anchor-based single-stage detector  
- Predicts bounding boxes + facial keypoints  
- Extremely low recall due to VRAM limitations during training  

### 3. Faster R-CNN
- Two-stage detector: RPN + classifier  
- Good stability and box quality  
- Slow inference and struggles with tiny faces  

### 4. YOLOv8n-Face
- Anchor-free, lightweight YOLO model  
- Great performance on tiny and occluded faces  
- Fastest inference and highest recall in our tests  

---

## 📏 Evaluation Metrics

- **Precision**
- **Recall**
- **F1-score**
- **Intersection-over-Union (IoU)**

---

## 📊 Quantitative Results

| Model          | Precision | Recall  | F1 Score | Mean IoU |
|----------------|-----------|---------|----------|----------|
| Viola–Jones    | 0.7293    | 0.1187  | 0.2041   | 0.6436   |
| RetinaFace     | 0.2332    | 0.0182  | 0.0389   | 0.6655   |
| Faster R-CNN   | 0.5942    | 0.3156  | 0.4122   | 0.7300   |
| YOLOv8n-Face   | 0.9833    | 0.2985  | 0.4580   | 0.8400   |

**YOLOv8n-Face demonstrates the best overall performance.**

---

## 🖼️ Qualitative Analysis

- **Viola–Jones**: fails to detect tiny/occluded faces  
- **RetinaFace**: accurate bounding boxes but very low recall  
- **Faster R-CNN**: reliable but slow and weak for tiny faces  
- **YOLOv8n-Face**: strong generalization across very crowded scenes  

---

## 🧩 Discussion

YOLOv8n-Face leads due to:

- Anchor-free design  
- Efficient feature pyramids  
- Real-time capabilities  
- Strong performance on small and occluded faces  

Classical detectors are insufficient for modern crowd-level detection tasks.

---

## ⚠️ Limitations

- Limited GPU memory restricted batch sizes  
- Heavy models (RetinaFace, Faster R-CNN) couldn't be fully trained  
- WIDER FACE "hard" subset remains tough  
- mAP metrics not computed due to resource constraints  

---

## 🚀 Future Work

- Train larger models (YOLOv8m, YOLOv8l)  
- Use better augmentation (mosaic, motion blur, jitter)  
- Compute mAP@0.5 and mAP@0.5:0.95  
- Build a real-time deployment pipeline  

---

## 🏁 Conclusion

YOLOv8n-Face achieves the best balance between accuracy and speed, making it ideal for real-world crowd face detection. Classical models remain viable only for simple, constrained scenarios, whereas modern lightweight deep-learning models excel in complex, high-density environments.

---

## 📚 References

- WIDER FACE Dataset  
- Viola & Jones (2001) — Haar Cascade  
- Deng et al. (2020) — RetinaFace  
- Ren et al. (2015) — Faster R-CNN  
- Ultralytics YOLOv8 Documentation  


Build real-time pipeline for deployment

🏁 Conclusion

YOLOv8n-Face offers the best trade-off between speed and accuracy for crowd face detection. Classical methods are obsolete for real-world high-density scenes, while modern lightweight deep detectors excel.
