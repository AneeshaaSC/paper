# Paper
* link: http://i.cs.hku.hk/~yzyu/publication/SelectiveJoint-cvpr17.pdf
* author: Weifeng Ge, Yizhou Yu
* year: 2017
* codes and models: https://github.com/ZYYSzj/Selective-Joint-Fine-tuning

# Summary
This paper proposes a way to identify a  sufficient training data, named selective joint fine-tuning.

## What 
Selecting image from D<sub>s</sub> (large-scale source training set) according to low-level characteristics similar to D<sub>t</sub> (small-scale target training set)  
### How  
use existing linear or nonlinear filter (lower layers of a pretrained CNN)  
### Why  
1. low-level characteristics related to lower layers of a deep network  
2. diversity and quantity in high-level semantic contents  

## Model
* Filter Bank  
* Image Descriptor  
* Nearest Neighbor Ranking  
* Hard Samples in the Target Domain  

## Experiments
the initial number of retrieved nearest neighbors can't be too small (overfit) or too large (surprising, doesn't explain why?)  
result: performance improved for all selected target images  

## Benefits
1. X overfitting  
2. √ robustness of kernels in shared convolutional layers 

## Me
pre DL for DL?   
Maybe will develop to a nested way instead of parallel one?  -> Make filtesr reuseable for some more detailed but similiar DL!
Cool!
