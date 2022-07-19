# Face_Recognition

## Code Structure

```
.
├── README.md
├── face_detect.py
├── face_rec
│   ├── face_capture.py
│   ├── face_rec.pb
│   ├── face_rec_train.py
│   ├── face_rec_train.sh
│   └── train_images
├── face_rec.py
├── face_rec_test.py
├── opencv_face_detector
│   ├── deploy.prototxt
│   ├── opencv_face_detector.pbtxt
│   ├── opencv_face_detector_uint8.pb
│   ├── res10_300x300_ssd_iter_140000_fp16.caffemodel
│   └── weights.meta4
├── requirements_m1mac.txt
└── requirements_ubuntu.txt
```

## Capture Sample Images for Training

- Run the script `face_capture.py` to capture images from the video camera.
```
$ python face_rec/face_capture.py
```

- Save the cropped images.
1. This script saves the cropped face images in `face_rec/outputs` directory. 
2. Make folder(name it `{Person_Name}` like "js_kim") and move images which in `face_rec/outputs` into the folder(like "js_kim").


```
train_images/
  ├── Person_1
  │   ├── face_0001.png
  │   ├── face_0002.png
  │   ├── ...
  │   └── face_0300.png
  ├── Person_2
  └── etc.
```


## Train the network with new data

Run `face_rec_train.py` and update `face_rec.pb` file.


- Sample Usage (CPU)
```
$ python face_rec_train.py --num_epochs 200 --minimum_cost 5e-06
```


## Test with the camera.

- Run the script `face_rec.py` and check the name of recognized face.
```
$ python face_rec.py
```
