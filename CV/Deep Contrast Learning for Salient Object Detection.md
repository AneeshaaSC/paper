# Paper
* link: http://i.cs.hku.hk/~yzyu/publication/DCLsaliency-cvpr16.pdf
* author: Guanbin Li, Yizhou Yu
* year: 2016

# Summary
This paper introduces an end-to-end (only once run) deep contrast network for salient object detection, consist of a fully convolutional stream and a segment-wise spatial pooling
stream. 

## Model
Architecture:  
![ArchitecturePic](https://github.com/VickyPapa/paper/blob/master/pic/ArchitectureOfDeepContrastNetwork.jpg)  
* Multi-Scale Fully Convolutional Network  
Consideration for end-to-end feature
1. depth -> muti-level features at diff scales
2. able to tell subtle visual contrast (I think it is similiar to point 1)
3. fine-tuning an existing deep model (in accordence with the later paper, "Deep Contrast Learning for Salient Object Detection")  
VGG16 and detailed layers design
* Segment-Level Saliency Inference  
Steps to eliminate discontinuities along object boundaries
1. raw input image -> a set of superpixels (segment)
2. generate a binary mask for each segment
3. averaged -> thresholded -> binary segment mask on Conv5_3
* Deep Contrast Network Training  
Steps to fine-tune the two streams  
1. fix the parameters in the second stream and train the first stream for one epoch  
2. fix the parameters in the first stream and fine-tune the neural network in the second stream for one epoch using groundtruth saliency maps (exchange with step 1)  

## Algorithm  
* Superpixel Segmentation  
Use slightly modified version of the SLIC algorithm (maybe not a good choice considered the performance)
* Spatial Coherence  
Use CRF, energy minimization and well performance

## Experiments  
Point: five public datasets & divide the MSRA-B dataset for fair comparison  
Performance measurement: using precision-recall (PR) curves, F-measure and mean absolute error (MAE)  
Implementation framework: Caffe  
Result: good efficiency  

## Benefits
1. More clear at pixel level instead of patch level  
2. Save time & space since avoiding redundancy 
