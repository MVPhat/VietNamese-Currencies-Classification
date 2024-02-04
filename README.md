# Vietnamese Currencies Classification

## Overview

Vietnamese Currencies Classification addresses a prevalent challenge in Vietnam - the need to accurately distinguish between various currency denominations. In a country where different currency notes share similar visual elements, this project aims to provide a robust solution for automating the recognition and classification of Vietnamese banknotes.

### Table of Contents

- [Demo](#demo)
- [Prerequisites](#prerequisites)
- [Installation](#installation)

## Demo

Waiting for uploading demo...

## Prerequisites

Before starting the project, you should install necessary dependencies in your device, but I recommend upload the file on [Google Colab](https://colab.research.google.com/) because of several conveniences.

## Dataset Preparation

My dataset usage is downloaded from [Kaggle](https://www.kaggle.com/datasets/nguyentrongdai/vietnamese-currency). This dataset contains 11 currencies of vietnam dong. Nonetheless, The dataset is lack of data if we split into 3 subsets; therefore, you can use different dataset versions from [Roboflow](https://universe.roboflow.com/cv-aal82/vietnamese-currency-detector/dataset/7/images).

The structure of dataset after pre-processing should be:

```json
VietNamese_Currency
|
--- train
|   |
|   --- 000000
|   |   |
|   |   --- 000000_0.jpg
|   |   --- 000000_1.jpg
|   |   --- ...
|   --- 000200
|   |   --- 000200_0.jpg
|   |   --- 000200_0.jpg
|   |   --- ...
|   ...
--- val (identical to train)
|
--- test (identical to train)
```

## Model Architecture

I leverage the pretrained model YOLOv8 (weights: [yolov8n-cls.pt](https://docs.ultralytics.com/tasks/classify/#models)), which is trained on ImageNet dataset.

## Training & Evaluation

In my experiment, I will use some `augmentation data techniques`, including rotation, translation, etc. If you want to modify the configurations, please visit [Ultralytics Docs](https://docs.ultralytics.com/usage/cfg/#train)

After training, the results will be stored in `runs/classify/train`, which includes 2 weights files, best and last, respectively. In addition, some evaluation metrics such as confusion matrix, confusion_matrix_normalized and visualization of training data are stored in the same path.