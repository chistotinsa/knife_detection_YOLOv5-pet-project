![](lpo.bmp)
# Knife detection with YOLOv5m

This is a YOLOv5 fork repo finetuned with a custom dataset that includes 23285 images of knives.
**It can detect a knife in person's hands or just a separate knife anywhere on an image/video/CCTV.**
However it shows only ~0.751 mAP50 score, it was trained on one T4 for only 30 epochs, and it is just a pet-project. I hope you'll enjoy it!

## Usage
#### 1. Clone the repo and install all dependencies
```python
!git clone https://github.com/chistotinsa/knife_detection_YOLOv5
!pip install -U -r knife_detection_YOLOv5/requirements.txt
%cd /content/knife_detection_YOLOv5
```

#### 2. Download model`s weights
```python
import gdown

gdown.download(id='10-mm4GPbpP0CS2F0f9BGd6SUGXAGjAxO', output="weights.pt")
```

#### 3. Run detect.py with changing --source flag to your own content repo
```python
!python detect.py --img 416 --conf-thres 0.2 --source /your/content/source
```

***You can see the result in runs/detect

#### What was done in fork version
- the dataset with 8966 images of knives was collected from a couple of open datasets on roboflow.com
- the collected dataset had been supplemented with my own collected and labeled data
- with an augmentation the dataset was brought to the current size
- then classic YOLOv5m was finetuned with freezing first 10 layers
#### :dolphin: you can see the change logic, train logs and additional code in train_notebook.ipynb
