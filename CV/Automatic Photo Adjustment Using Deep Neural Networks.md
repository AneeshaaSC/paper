# Paper
* link: http://i.cs.hku.hk/~yzyu/publication/DNNphoto-tog2016.pdf
* author: Zhicheng Yan, Hao Zhangy, Baoyuan Wang, Sylvain Paris, Yizhou Yu
* year: 2016
* codes and models: https://github.com/stephenyan1231/dl-image-enhance

# Summary  
This paper provides a deep netural network model to do automatic photo enhancement.  

## Model  
* Difficulty: need a mapping function which is sensitive to high-frequency details  
* Solution: F(Θ; x<sub>i</sub>) ->  F = Φ(Θ; x<sub>i</sub>)V(c<sub>i</sub>)  
(color basis vector V(c<sub>i</sub>), major difference with previous work and significant improvement)  

### Neural Network Architecture and Training  
* Architecture  
Choose the rectified linear unit (ReLU), for inducing sparsity in the hidden units and accelerating the convergence of the training process  
* Training  
Choose Dropout training strategy, for improving the generalization capability  

### Feature descriptor  
Three components  
* Pixelwise Features —— reflect high-resolution pixel-level image variations & indispensable for learning spatially varying photo enhancement models  
* Global Features —— benefit decision on how to enhance an image  
* Contextual Features —— characterize the distribution of semantic categories  

## Experiments  
* Measurement: Compare automatic ones to manual ones in user studies  
* Steps: Neural Network Setup -> Data Sampling -> Image Enhancement with Learned Color Mappings  
* Results: positive  
### Learning local adjustments  
* Three Stylistic Local Effects: Foreground Pop-Out, Local Xpro, Watercolor  
* Spatially Varying Color Mappings  
* Generalization Capability  
* Effectiveness of Contextual Features  
* Effectiveness of Learning Color Transforms  
* DNN Architecture  
### Learning global adjustments  
* MIT-Adobe FiveK Dataset
* Instagram Dataset


## Benifits  
1. Model local adjustments that depend on image semantics  
2. Qualitatively and quantitatively improvement 

## Limitations  
1. Relies on scene parsing and object detection to build contextual features, which have challenging problems themselves. For example, it will be greatly affected by mislabeling  
2. Individual adjustments significantly deviating from the average adjustment for a semantic object type are likely to be treated as outliers and cannot be correctly learnt.  
3. There may exist better design choices in the DNN architecture.

## Me  
Detailed application is the new kind of innovation!  
Constraints of application relies on what it combine.  
