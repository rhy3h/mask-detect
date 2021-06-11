# YOLOv4-tiny NCNN with Android 

This repo provides C++ implementation of [YOLOv4-tiny model](https://github.com/AlexeyAB/darknet) using
[Tencent's Ncnn framework](https://github.com/tencent/ncnn). 

Tips: If your class is not too much, use YOLOv4-tiny rather than YOLOv4 you will get more efficiency, and run faster. 

## Step 1 Darknet Train Model
[Use YOLOv4-tiny train your model](https://github.com/rhy3h/mask-detect/blob/main/YOLOv4/yolov4-tiny-train.ipynb) 

## Step 2 [Darknet To NCNN Conversion Tools](https://github.com/Tencent/ncnn/tree/master/tools/darknet)

### 1. Convert yolov4-tiny cfg and weights 

Download pre-trained [yolov4-tiny-custom.cfg](https://github.com/rhy3h/mask-detect/blob/main/YOLOv4/cfg/yolov4-tiny-custom.cfg) and [yolov4-tiny-custom.weights](https://github.com/rhy3h/mask-detect/blob/main/YOLOv4/weights/yolov4-tiny-custom_final.weights) or with your own trained weight.

### 2. [Convert to Ncnn](https://github.com/rhy3h/mask-detect/blob/main/YOLOv4/darknet2ncnn/darknet2ncnn.exe) 
Convert cfg and weights:
```
darknet2ncnn yolov4-tiny-custom.cfg yolov4-tiny-custom.weights yolov4-tiny.param yolov4-tiny.bin 1
```

If succeeded, the output would like this:
```
Loading cfg...
WARNING: The ignore_thresh=0.700000 of yolo0 is too high. An alternative value 0.25 is written instead.
WARNING: The ignore_thresh=0.700000 of yolo1 is too high. An alternative value 0.25 is written instead.
Loading weights...
Converting model...
83 layers, 91 blobs generated.
NOTE: The input of darknet uses: mean_vals=0 and norm_vals=1/255.f.
NOTE: Remeber to use ncnnoptimize for better performance.
```

### 3. [Optimize graphic](https://github.com/rhy3h/mask-detect/blob/main/YOLOv4/darknet2ncnn/ncnnoptimize.exe) 

```
ncnnoptimize yolov4-tiny.param yolov4-tiny.bin yolov4-tiny-opt.param yolov4-tiny-opt.bin 0
```

## Step 3 [Android Project](https://github.com/dog-qiuqiu/Android_NCNN_yolov4-tiny) 

## [APK](https://github.com/rhy3h/mask-detect/blob/main/maskapp/app/release/app-release.apk) 

### If the program crashes, please open the camera and read/write storage permission 

## Credits 
- [Darknet](https://github.com/AlexeyAB/darknet)
- [Ncnn](https://github.com/tencent/ncnn)
- [YOLOv5_NCNN](https://github.com/WZTENG/YOLOv5_NCNN)