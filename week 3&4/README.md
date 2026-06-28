# Blood Cell Detection using YOLOv8 (Week 3-4)

## Objective
Train an object detection model that can automatically identify and localize
blood cells in microscope images — Red Blood Cells (RBC), White Blood Cells (WBC),
and Platelets — as a step toward automated blood sample analysis for the
AI for Healthcare project.

## Why this dataset / problem
Manual blood cell counting under a microscope is slow and prone to human error.
An automated detector can assist lab technicians by pre-screening samples,
flagging abnormal cell counts, and speeding up diagnosis — directly relevant
to healthcare screening workflows.

## Dataset
- **Name:** BCCD (Blood Cell Count and Detection)
- **Source:** Roboflow Universe — https://universe.roboflow.com/joseph-nelson/bccd
- **Version used:** v4 (416x416, augmented)
- **Images:** 874 total (765 train / 73 valid / 36 test)
- **Classes (3):** RBC, WBC, Platelets
- **Format:** YOLOv8 (bounding boxes, normalized coordinates)

## Model & Approach
- **Architecture:** YOLOv8n (nano) — pretrained on COCO, fine-tuned on BCCD
- **Why YOLOv8n:** lightweight and fast to train/run while still accurate
  enough for this task; good fit for limited compute/time
- **Framework:** Ultralytics YOLO (Python)
- **Training environment:** Google Colab (T4 GPU)

### Training configuration
| Parameter | Value |
|---|---|
| Base model | yolov8n.pt (pretrained) |
| Epochs | 50 |
| Image size | 416x416 |
| Batch size | 16 |
| Early stopping patience | 10 |

## Results

Final validation metrics (best.pt):

| Class | Precision | Recall | mAP50 | mAP50-95 |
|---|---|---|---|---|
| All (overall) | 0.868 | 0.910 | **0.927** | 0.648 |
| Platelets | 0.837 | 0.908 | 0.903 | 0.489 |
| RBC | 0.798 | 0.822 | 0.892 | 0.640 |
| WBC | 0.968 | 1.000 | 0.987 | 0.816 |

**Overall mAP50 = 0.927** — the model reliably detects and classifies all
three blood cell types, with especially strong performance on WBC detection.

See `/results` folder for:
- `confusion_matrix.png` — per-class prediction breakdown
- `results.png` — training/validation loss and mAP curves over epochs
- `sample_prediction.jpg` — example output with bounding boxes drawn on a test image

## Files in this submission
| File | Description |
|---|---|
| `BCCD_Blood_Cell_Detection.ipynb` | Full training notebook (dataset download → train → validate → predict) |
| `best.pt` | Final trained model weights |
| `results/` | Training graphs, confusion matrix, and sample prediction images |

