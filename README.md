## Solution description :

Yolov2 based shelf Image recognition (single class only for product count). 
I trained a YoloV2 model from scratch (without any pretrained weights) on Kaggle for faster training.

Input Image size : 416, 416

## Dataset preparation :

- Used basic techniques to prepare the data. Scaling images and bboxes. Creating a Data Generator for
  training/validation. 

Dataset downloaded from : (https://github.com/gulvarol/grocerydataset, https://storage.googleapis.com/open_source_datasets/ShelfImages.tar.gz)

## Detection Network :

I used YOLOv2 (You only look once) architecture and trained it from scratch using Tensorflow on 
Kaggle's kernel. 

Yolov2 had a much better accuracy improvement from the initial YOLO and less localization errors as
it removed the Fully Connected Layers and instead made a Fully Convoultional Network with anchor boxes
(priors according to their paper) which helped detect bounding boxes better.

You can download the weights from the model I already trained from : https://drive.google.com/file/d/1dDKkXNNSAQHYc-1ZNF3RvTPAXbFiWXqO/view?usp=sharing

## Evaluation :

Calculated mAP over 8 iou thresholds [0.4, 0.45, 0.5, 0.55, 0.6, 0.65, 0.7, 0.75].

Got a mAP score of 0.83 on Test set over all the thresholds and a precision of 0.824 on 0.5 iou 
threshold after training for 100 epochs. 

## Anchor Box Tuning :

Ideal approach is to use K-means for generating k anchor boxes and using IoU as a distance metric
between two boxes and getting the centroids of k clusters. But in this case I had to use only one 
anchor box so it was basically finding the mean of the all the bboxes.



## References :

I used the implementation of Yolov2 from https://github.com/JongsooKeum/yolov2-tensorflow
and tuned according to the current dataset.



## Footnote :
My failed attempts :
- SSD with mobilenet (300*300) couldn't get a good accuracy without pretrained weights.
- RPN with ROI pooling from Mask RCNN 






