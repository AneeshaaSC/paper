# Paper
* author: Min Bai, Raquel Urtasun
* year: 2017

# Summary  
classical watershed transform + modern deep learning -> an energy map -> a cut at a single energy level -> solve over-segmentation  

## Model  
![ArchitecturePic](https://github.com/VickyPapa/paper/blob/master/pic/DeepWatershedTransformforInstanceSegmentation.png)  
* The first half of the overall network: Direction Network (DN)   
input: the original RGB image gated by a binarized semantic segmentation + semantic segmentation   
output: The resulting feature volumes from the three paths are concatenated  
* The second half of the overall network: Watershed Transform Network (WTN)   
The WTN is a fairly generic CNN  
input: 2-channel unit vector map  
output: a discretized modified watershed transform map with K = 16 possible energy values  
(bin 0 corresponds to background or regions within 2 pixels of an instance boundary and is referred to as having an energy level of 0. Higher numbered bins with higher energy levels correspond to regions in the interior of object instances.)  
The bins are chosen to maximize the binning resolution of energy levels near zero (to facilitate accurate cutting), while achieving an approximate balance between the total numbers of pixels within each class.  
* Network Training  
pre-train DN and WTN networks -> end-to-end training of the whole network
* Energy Cut and Instance Extraction  
example: cut watershed transform output at energy  
level 1 for classes with many smaller objects (person, rider, bicycle, motorcycle)  
level 2 for classes with larger objects (car, bus, truck, train)  

### Advantages 
1. can be easily trained end-to-end
2. produces very fast and accurate estimates
(about fast: does not rely on iterative strategies such as RNNs, thus has a constant runtime regardless of the number of object instances.)    

## Experiments  
evaluate this approach on the challenging Cityscapes Instance-Level Semantic Labelling Task  
* Results: a large improvement (more than double)
* Problems:  
rely upon correct semantic segmentation, errors from this (such as identifying a train as a bus) cannot be fixed by our method  
possible solution: use semantic segmentation as soft gating, or to reason about semantic and instance segmentation jointly  

