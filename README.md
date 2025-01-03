# image-recognition-project-based-on-YOLOv10
This is a very simple image recognition tool with python and yolov10 that is according to [YOLOv10: Real-Time End-to-End Object Detection](https://arxiv.org/abs/2405.14458).

In readme, it will present the process and results of this image recognition tool, the most important part of code(model train and predict) is from [yolov10](https://github.com/THU-MIG/yolov10/tree/main). 
<img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXflw-lQoXZlwEoMaubvogwEXWpUsK4gkglPfnlUpa_ASr2-g9gEEf5imPpeuMttkkBFNxqMAjINgIb6AVcFF2hXSZnQ_YCCg6Jokaz-4BxnJlhyL2AKw4Ty6lW-JT7H6uO7B80TMx0ytXBl4Xr0ZB5WCzE?key=zkoZqw4rJh7cg9cG7yYpEA"> 

## How to begin
for yolov10, please check on the [yolov10](https://github.com/THU-MIG/yolov10/tree/main). 

### photo dataset
Please go to [coco](https://cocodataset.org/#download) datset and then download Train/Val/Test images and Train/Val annotations(by click right button and choose open thelink at new page).

You can find coco.yaml at ...\yolov10\ultralytics\cfg\datasets\coco.yaml, it is important because your model learn and predict photos by coco.yaml.

### Pretrained-weight
You can find pretrained-weight files on yolov10 website, please download pretrained-weight files on yolov10 website.

### Computer hardware
My CPU is intel-i7-11th, GPU is NVIDIA GeForce RTX 3060, Size of memory is 40GB, P.S this project needs 40GB at least or it will crush, I tried it.

## dataset
The content of dataset is from coco dataset, but I added some photos which was taken by myself.

The ratio of train and test datas is from added photos is 7:3.

You have to put your train datas(including label files) and test datas in a same direction.

## Process
### Preprocessing
Make new label files of photos by annotations->Ensure all images have corresponding labels->Ensure data in labels where the class_id is in the number of classes
-> change photos size and data about size in labels(if your size of memory is enough, skip it)->make formation of new labels is the same as old->correct wrong class_id of data in labels

If you had your own added photos, you could create your labels of your new photos by [labelimg](https://github.com/HumanSignal/labelImg/blob/master/README.rst).
Other steps is the same as above.

### Train and predict process
you can find the code of training and prediction on yolov10 website

## Results
### The results of training
<img src="https://github.com/aegon1994/image-recognition-project-based-on-YOLOv10/blob/main/readphotosimages/readme%20photos/process%20of%20training.png?raw=true">

The confusion matrix(normalized):
Left of this graph is predicted result, Button of the graph is true result, if a color of square was more deeper, the pair would happen frequently. 
<img src="https://github.com/aegon1994/image-recognition-project-based-on-YOLOv10/blob/main/readphotosimages/readme%20photos/confusion_matrix_normalized.png?raw=true">
you could the color of square of diagonal is deeper than most of area. It means the correct rate of this model is not so bad, but color of button is deeper.
It means there are so many object couldn't detected by this model.

The F1-confidence curve:
In this graph,F1-score is on y-dimension, confidence is on x-dimension, the blue line is the F1 curve line of this model.
<img src="https://github.com/aegon1994/image-recognition-project-based-on-YOLOv10/blob/main/readphotosimages/readme%20photos/F1_curve.png?raw=true">
You could see this blue line, when F1 score is high, confidence is low. When F1 is low, confidence is high. It means when model recognized a object is definitely one class, the performance is not good.
It is an unusual result. It will be the future work. 

The Precision-confidence curve:
In this graph,Precision is on y-dimension, confidence is on x-dimension, the blue line is the P curve line of this model.
<img src="https://github.com/aegon1994/image-recognition-project-based-on-YOLOv10/blob/main/readphotosimages/readme%20photos/P_curve.png?raw=true">
In this graph, when confidence is low, precision raise very quickly. When confidence is high, precision is stable.
It is a ideal state, it means when model think results is right, it would be right.

The Recall-confidence curve:
In this graph,Recall is on y-dimension, confidence is on x-dimension, the blue line is the R curve line of this model.
