# Bahraini Currency Recognition with YOLO26

This project uses **YOLO26 Object Detection** to recognize Bahraini currency notes in images. The model draws bounding boxes around detected notes and displays their predicted classes and confidence scores.

## Project Overview

I used **Google Colab** for model training and **Jupyter Notebook** for live webcam testing. I also created a **Streamlit** app to detect currency notes from uploaded images or camera photos.

## APP: `https://bahrainicurrency-gvtgsaor8naspnpjfmgcmp.streamlit.app/`

## Dataset

- **Source:** Roboflow , Bahraini Currency dataset, **Version 2**
- **Images shown for Version 2 on Roboflow:** **1,075**
- **Classes:** 10
- **Task:** Object Detection

## Preprocessing and Data Augmentation

Images were resized to **224 × 224** during training. YOLO automatically normalizes the input pixel values.

| Method | Setting |
| --- | --- |
| Rotation | `degrees=10` |
| Zoom / scale | `scale=0.2` |
| Horizontal flip | `fliplr=0.5` |
| Brightness adjustment | `hsv_v=0.2` |

## Model Training

- **Model architecture:** YOLO26 Nano (`yolo26n.pt`)
- **Environment:** Google Colab
- **Training configuration:** 50 epochs, `imgsz=224`
- **Saved model file:** `best.pt`

## Testing and Streamlit App

I tested camera-based detection in **Jupyter Notebook**. The Streamlit app allows users to:

- Upload an image or take a photo
- Detect notes and display bounding boxes
- View predicted currency labels and confidence scores
- Download the annotated result

**Note:** Streamlit's camera option captures a photo, not continuous live video.

## Project Files

```text
Bahraini_Currency_Streamlit_V2/
├── app (1).py
├── bestbest.pt               
├── requirements.txt
└── README.md
```

## Limitations

Performance can be affected by lighting, distance, camera angle, background, and the quality of the training labels. The project results should be assessed on unseen images before making claims about accuracy. Final evaluation metrics are not reported here.
