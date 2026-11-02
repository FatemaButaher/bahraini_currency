# Bahraini Currency Recognition Using YOLO26

This project uses **YOLO26** to detect Bahraini currency notes in images. The model draws a bounding box around each detected note and shows the predicted currency class with a confidence score.

## Project Overview

I trained the model using **Google Colab** and tested webcam detection using **Jupyter Notebook**. I also created a **Streamlit** app where users can upload an image or take a photo to detect Bahraini currency.

## Dataset

- **Source:** Roboflow (Bahraini currency dataset, Version 1)
- **Total images:** 392
- **Classes:** 10

| Split | Images |
| --- | ---: |
| Training | 371 |
| Validation | 11 |
| Testing | 10 |
| **Total** | **392** |

During training, YOLO skipped **9 training images** because their labels mixed segmentation and detection formats. This left **362 usable training images**.

## Preprocessing and Data Augmentation

Images were resized to **224 × 224** for training. YOLO handles pixel normalization automatically.

| Augmentation | Setting |
| --- | --- |
| Rotation | `degrees=10` |
| Zoom / scale | `scale=0.2` |
| Horizontal flip | `fliplr=0.5` |
| Brightness | `hsv_v=0.2` |

## Model

- **Model:** YOLO26 Nano (`yolo26n.pt`)
- **Platform:** Google Colab (T4 GPU)
- **Training configuration:** 50 epochs, image size 224
- **Trained weights:** `best.pt`

## Streamlit App

The app includes:

- Uploading a currency image or taking a photo
- Detecting notes with bounding boxes
- Showing currency labels and confidence scores
- Adjusting the confidence threshold
- Downloading the image with predictions

The Streamlit camera option takes a **photo**. Live webcam detection was tested separately in Jupyter Notebook.

## Project Files

```text
Bahraini_Currency_Streamlit/
├── app.py
├── best.pt                 # Add your downloaded model here
├── requirements.txt
├── packages.txt
├── .gitignore
├── .streamlit/
│   └── config.toml
└── README.md
```

## Run the App

Put `best.pt` in the same folder as `app.py`, then run:

```bash
pip install -r requirements.txt
streamlit run app.py
```

## Notes

The validation and test sets contain only **11 and 10 images**, so they are too small for a reliable evaluation of performance on new photos. Some training labels also need correction. The project can be improved by fixing those labels and using a larger, better-balanced validation and test set.
