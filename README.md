# Hardhat & Workwear Dataset (YOLOv5)

This dataset contains annotated images of safety helmets and workwear (including reflective vests and coveralls). It comprises 2,000 original labeled images and, after data augmentation, 6,000 images in total. All annotations are provided in YOLOv5 format

## Acknowledgements

Huge thanks to the original dataset provider: [https://github.com/lijfrank-open/SFCHD-SCALE](https://github.com/lijfrank-open/SFCHD-SCALE) — this repository served as an important resource and inspiration for our data collection and preprocessing.


## Dataset overview

This repository contains a YOLOv5-format dataset for detecting **safety helmets** and **workwear** (including reflective vests and coveralls).

* **Original labeled images:** 2,028
* **After augmentation:** 6,084
* **Format:** YOLOv5 (`images/` and `labels/`, one `.txt` annotation file per image with `class x_center y_center width height` normalized coordinates)


## Directory structure

```
dataset/
├── data.yaml
├── images/
│   ├── 000001.jpg
│   ├── 000002.jpg
│   └── ...
└── labels/
    ├── 000001.txt
    ├── 000002.txt
    └── ...
```

* `data.yaml` — dataset config for training (class names, train/val paths, etc.).
* `images/` — all image files (jpg/png).
* `labels/` — YOLO-format annotation files (one `.txt` per image).


## Data augmentation

To enrich the dataset and improve model robustness, the following augmentation pipeline was applied to the original images to expand 2,028 images to 6,084 images (3×):

* **Flip:** Horizontal flip (applied to a subset of images)
* **Rotation:** Random rotation between **-15° and +15°**
* **Noise:** Random noise added to up to **0.1%** of pixels

Note: Augmentation preserved original annotation coordinates by transforming bounding boxes accordingly (rotation and flip applied to both images and labels).


## Examples

Three example images and their corresponding label files are included under `dataset/images/` and `dataset/labels/`:

* `dataset/images/example_01.jpg` + `dataset/labels/example_01.txt`
* `dataset/images/example_02.jpg` + `dataset/labels/example_02.txt`
* `dataset/images/example_03.jpg` + `dataset/labels/example_03.txt`

You can replace these placeholder filenames with any three representative images from the dataset; keeping examples in the repository helps others quickly inspect annotation quality.


## Usage notes

* This dataset follows the standard YOLOv5 layout. To train with YOLOv5, set `data.yml` `train:` and `val:` paths to the `dataset/images` (or split them into `train`/`val` folders as desired).



