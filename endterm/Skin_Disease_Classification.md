# Skin Disease Classification using YOLOv8

End-term project for Seasons of Code, IIT Bombay (AI for Healthcare track).

**Author:** Shashank Choudhary (Roll No. 25B0371)
**Mentor:** Viren Mehta

## What this is

A YOLOv8-based image classifier that predicts one of nine dermatological
conditions from a dermoscopic skin lesion image. Built and trained on a
Roboflow/ISIC-derived dataset, with three training runs compared to check
whether the accuracy ceiling (~76% top-1) comes from training time, model
capacity, or the data itself.

## Contents

- `end_term_report.pdf` — full end-term report (problem statement, dataset
  fix, training runs, results, limitations)
- `code.ipynb` — full pipeline: data download, class-stratified re-split,
  training (Runs 1–3), and evaluation

## Key result

All three training runs plateau at 75–76% top-1 accuracy. The confusion
matrix shows this comes from a genuine visual-similarity ceiling between
keratinocyte-related lesions, not from insufficient training or model size.
See Section 3 of the report for details.
