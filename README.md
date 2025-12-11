# Crowd-Detection-using-WIDERFACE
Crowd Face Detection Using Classical and Deep Learning Approaches

This repository contains the implementation and benchmarking code for crowd face detection using four classical and deep-learning models. Evaluations are conducted on the WIDER FACE dataset to compare performance under challenging conditions such as occlusion, tiny faces, pose variation, and illumination differences.

📌 Overview

Face detection in crowded environments is a difficult computer-vision task. This project evaluates:

Viola–Jones (classical Haar-cascade)

RetinaFace (anchor-based deep detector)

Faster R-CNN (two-stage region proposal network)

YOLOv8n-Face (modern anchor-free YOLO detector)

All models are tested for precision, recall, F1-score, and IoU. Due to compute constraints, lightweight variants were used where applicable.

📂 Dataset: WIDER FACE

The dataset used is the WIDER FACE benchmark, containing:

32,203 images

393,703 annotated faces

Variations in scale, illumination, pose, crowd density

Dataset split:

50% Training

10% Validation

40% Testing

Bounding boxes were visualized to verify label correctness. Augmentation was minimal due to GPU limitations.

🧠 Models Evaluated
1. Viola–Jones (Haar Cascade)

Fast and lightweight

Works mainly for frontal, non-occluded faces

Very poor performance on tiny and rotated faces

2. RetinaFace

Anchor-based single-stage model

Predicts face boxes + 5 keypoints

GPU VRAM constraints limited training

Low recall observed

3. Faster R-CNN

Two-stage detector with RPN

Reliable box quality

Computationally heavy

Struggles with tiny faces

4. YOLOv8n-Face

Anchor-free, lightweight, fast

Strong performance on tiny + occluded faces

Best recall and highest IoU

Best overall model in this study

📏 Evaluation Metrics

Precision

Recall

F1-Score

Mean IoU

📊 Quantitative Results
Model	Precision	Recall	F1 Score	Mean IoU
Viola–Jones	0.7293	0.1187	0.2041	0.6436
RetinaFace	0.2332	0.0182	0.0389	0.6655
Faster R-CNN	0.5942	0.3156	0.4122	0.7300
YOLOv8n-Face	0.9833	0.2985	0.4580	0.8400

YOLOv8n-Face achieves the strongest overall performance.

🖼️ Qualitative Findings

Viola–Jones misses small, occluded, and rotated faces

RetinaFace produces accurate boxes but low recall

Faster R-CNN stable but slow and weak on tiny faces

YOLOv8n-Face detects faces robustly even in dense crowds

🧩 Discussion

YOLOv8n-Face performs best because of:

Anchor-free design

Strong feature pyramids

Good generalization

Real-time inference capability

Classical models lag in modern, unconstrained environments.

⚠️ Limitations

GPU memory restricted batch sizes

Heavy models could not be fully trained

Hard subset of WIDER FACE remains challenging

No mAP scores due to compute constraints

🚀 Future Work

Train larger YOLO variants (m, l)

Incorporate strong augmentation (mosaic, blur, jitter)

Compute mAP@0.5 and mAP@0.5:0.95

Build real-time pipeline for deployment

🏁 Conclusion

YOLOv8n-Face offers the best trade-off between speed and accuracy for crowd face detection. Classical methods are obsolete for real-world high-density scenes, while modern lightweight deep detectors excel.
