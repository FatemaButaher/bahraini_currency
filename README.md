# Bahraini Currency Recognition with YOLO26

A deep-learning object detection project that recognizes Bahraini currency notes in images.

## Features

- Upload a currency image or take a photo with your device camera.
- Detect notes with bounding boxes and confidence scores.
- Download the annotated prediction image.
- Adjust the confidence threshold.

## Model and training

- **Architecture:** Ultralytics YOLO26n object detector
- **Dataset:** Bahraini currency images labeled in Roboflow, with 10 classes
- **Image size:** 224 × 224
- **Epochs:** 50
- **Augmentations:** rotation (`degrees=10`), scale (`scale=0.2`), horizontal flip (`fliplr=0.5`), and brightness (`hsv_v=0.2`)
- **Preprocessing:** image resizing and automatic input pixel scaling within YOLO

The model was trained on Google Colab. A local Jupyter Notebook can run real-time detection using a webcam. This Streamlit app supports **photo capture**, not continuous webcam video.

> **Evaluation note:** The initial run logged 362 usable training images and only 11 validation images; 9 training items were ignored for mixed detection/segmentation label formats. Verify dataset annotations and use a larger independent test set before claiming generalization. Add verified Precision, Recall, mAP50, and mAP50-95 results here after final evaluation.

## Files

```text
Bahraini_Currency_Streamlit/
├── app.py
├── best.pt                 # Add your trained model here
├── requirements.txt
├── packages.txt
├── .gitignore
├── .streamlit/
│   └── config.toml
└── README.md
```

**Important:** `best.pt` is **not included** in the starter ZIP. Download the final file from Colab (`runs/detect/train-2/weights/best.pt`) and put it next to `app.py`.

## Run locally

Use a terminal in the same folder:

```bash
pip install -r requirements.txt
streamlit run app.py
```

Streamlit opens in your browser. Upload an image or take a picture to see detections.

## Deploy on Streamlit Community Cloud

1. Create a GitHub repository for this project.
2. Upload `app.py`, `best.pt`, `requirements.txt`, `packages.txt`, `README.md`, `.gitignore`, and `.streamlit/config.toml`.
3. Open https://share.streamlit.io and select **Create app**.
4. Choose your repository, branch `main`, and entrypoint `app.py`.
5. Deploy and test with a new photo.

For compatibility, choose a supported Python version (for example, Python 3.11) in advanced app settings if needed. The app uses CPU inference on Streamlit Community Cloud, so speed may differ from Colab's GPU.

## Next improvements

- Clean mixed segmentation/detection labels in the Roboflow dataset.
- Add more validation and test examples from unseen backgrounds and lighting conditions.
- Measure Precision, Recall, mAP, and per-class errors.
- Test on real phone photos without using the training images.
