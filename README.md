
# Garbage Classification — Deep Learning Model

A real-time garbage classification system built with TensorFlow/Keras and OpenCV. Point your webcam at a piece of trash, press **S** to scan, and the model identifies the material type within 3 seconds.
This project was wroked on as part of Artificial Intelligence course at Antonine University.

---

## Classes

The model classifies waste into 6 categories:

| Class | Description |
|---|---|
| Cardboard | Cardboard boxes, packaging |
| Glass | Bottles, jars |
| Metal | Cans, foil |
| Paper | Newspapers, documents |
| Plastic | Bottles, bags, containers |
| Trash | General non-recyclable waste |

---

## Model Architecture

Custom CNN built with TensorFlow/Keras:

```
Conv2D(32)  → MaxPooling
Conv2D(64)  → MaxPooling
Conv2D(128) → MaxPooling
Flatten
Dense(128, relu)
Dense(6, softmax)
```

- Input size: 224 × 224 × 3
- Optimizer: Adam
- Loss: Sparse Categorical Crossentropy
- Trained for 35–50 epochs

---

## Dataset

[Garbage Classification Dataset — Kaggle](https://www.kaggle.com/datasets/asdasdasasdas/garbage-classification)

The dataset is split into `train/`, `val/`, and `test/` directories, each containing one subfolder per class.

---

## Requirements

```bash
pip install tensorflow numpy opencv-python matplotlib seaborn scikit-learn
```

Or install from the requirements file:

```bash
pip install -r requirements.txt
```

---

## Usage

### Train the model


Open `garbage_classifier_DL_model.ipynb` in Jupyter and run all cells. The notebook will:

1. Load and preprocess the dataset
2. Train the CNN
3. Plot accuracy and loss curves
4. Generate a confusion matrix and classification report
5. Save the model as `garbage_model.h5`

### Using the pretrained model

The pre-trained model is hosted on Hugging Face:

[HusseinDiab/Garbage-Classifier on Hugging Face](https://huggingface.co/HusseinDiab/Garbage-Classifier)

Download the `garbage_model.h5` file and place it in the root of this repo, then load it with:

```python
from tensorflow.keras.models import load_model

model = load_model("garbage_model.h5")
```


### Run real-time webcam classification

The last section of the notebook launches a live webcam window:

```
Press S — start a 3-second scan countdown
Press Q — quit
```

The model captures the center region of the frame, runs inference, and overlays the predicted class and confidence percentage on the video feed.

---

## Project Structure

```
garbage-classifier/
├── garbage_classifier_DL_model.ipynb   # Main notebook (training + webcam)
├── garbage_model.h5                    
└── README.md
```

---

## Built With

- TensorFlow / Keras
- OpenCV
- NumPy
- Matplotlib / Seaborn
- scikit-learn
