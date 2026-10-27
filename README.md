PyGPR
Deep Learning for Ground Penetrating Radar Image Processing

PyGPR is an experimental computer vision project built with Python and PyTorch for detecting steel-related objects and pipes in Ground Penetrating Radar (GPR) images. It explores deep learning for subsurface imaging, infrastructure inspection, and potential anomaly analysis.

Visual Results
Figure 1. Dataset Summary

Overview of the dataset and annotation statistics.

<p align="center">
<img src="outputs/1.data.png" alt="Figure 1 — Dataset summary" width="85%">
</p>

Figure 2. Model Evaluation

Initial evaluation results showing the current detection performance.

<p align="center">
<img src="outputs/2.evaluate.png" alt="Figure 2 — Model evaluation" width="85%">
</p>

Figure 3. Prediction Example

Example detection output on a GPR image.

<p align="center">
<img src="outputs/3.prediction.jpg" alt="Figure 3 — Steel and pipe detection example" width="85%">
</p>

Dataset

The dataset is based on the P-GPR: A Ground Penetrating Radar Dataset for Pipeline Detection publication.

Split	Images	Labels
Training	188	188
Validation	54	54
Test	31	31
Total	273	273

Detection classes

0 — Steel
1 — Pipe

Annotations use normalized bounding boxes:

text
class_id x_center y_center width height

Dataset Citation

Yue, J., Qin, Y., Zhu, M., Ye, S., & Wang, Y. (2026). P-GPR: A Ground Penetrating Radar Dataset for Pipeline Detection. Proceedings of the 35th ACM International Conference on Information and Knowledge Management (CIKM '26), Rome, Italy. ACM.

Please consult the original publication and dataset license for applicable usage terms.

Methodology
Custom CNN-based object detector implemented in PyTorch.
No pretrained YOLO weights or Ultralytics detection/training pipeline.
Dataset validation and annotation analysis.
Model training and object detection evaluation.
Bounding-box visualization and non-maximum suppression (NMS).
GPU acceleration when CUDA is available.
Quick Start

Run commands from the project directory.

1. Validate the dataset

bash
python 00.diagnose_dataset.py


2. Test the dataset loader and model

bash
python dataset.py
python model.py


3. Train the model

bash
python train.py


4. Evaluate the detector

bash
python evaluate.py


5. Run predictions

bash
python predict.py --source "dataset/test/images" --confidence 0.25


Prediction images and evaluation outputs are saved under outputs/.

Adjust script names or arguments if your local files use different names.

Initial Evaluation

The initial test evaluation reported:

Metric	Steel	Pipe
Precision	0.0214	0.0042
Recall	0.5306	0.6667
AP@0.50	0.0154	0.0508

Initial mAP@0.50: 0.0331

These preliminary results indicate that detection accuracy requires substantial improvement. The model is an experimental prototype and is not validated for operational or safety-critical use.

Limitations
Multiple objects assigned to the same grid cell may cause target-assignment conflicts.
Bounding-box decoding and evaluation require further validation.
Confidence scores are not necessarily calibrated probabilities.
NMS may suppress legitimate overlapping detections.

Future work includes improving target assignment, training stability, detection accuracy, and evaluation reliability.

License

The project code is distributed under the MIT License.

The dataset is attributed to its original authors and remains subject to its own license and terms of use.

Author

Naeim Mousavi

Copyright © 2026 Naeim Mousavi.