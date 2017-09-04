# Paper
* author: Serena Yeung, Olga Russakovsky, Greg Mori, Li Fei-Fei
* year: 2017

# Abstract
a recurrent neural network-based agent that interacts with a video over time  

## Improvement  
* Exist works:  
building frame-level classifiers, running them exhaustively over a video at multiple temporal scales, and applying postprocessing such as duration priors and non-maximum suppression.  
* Their work:   
reasons directly on the temporal bounds of actions  
sequentially decide where to look and how to refine our hypotheses to obtain precise localization of the action withfar less exhaustive search  
using a combination of backpropagation and REINFORCE  

# Method  
## Architecture
![ArchitecturePic](https://github.com/VickyPapa/paper/blob/master/pic/EndtoendLearningofActionDetectionfromFrameGlimpsesinVideos.png)  
 The observation network encodes visual representations of video frames. The recurrent network sequentially processes these observations and decides both which
frame to observe next and when to emit a prediction. We
now describe each of these in more detail
* Observation Network  
The observation network encodes visual representations of video frames.  
inputs: the normalized temporal location of the observation + and the corresponding video frame  
* Recurrent Network  
The recurrent network sequentially processes these observations and decides both which frame to observe next and when to emit a prediction.  
input: observation feature vector  
outputs: candidate detection dn, binary indicator pn signaling whether to emit dn as a prediction, and temporal location ln+1 indicating the frame to observe next.  
## Training
Challenges: designing suitable loss and reward functions, and handling non-differentiable model components  
Methods: use standard backpropagation to train dn, and REINFORCE to train pn and ln+1.
* Segment-Level Saliency Inference  
Steps to eliminate discontinuities along object boundaries
1. raw input image -> a set of superpixels (segment)
2. generate a binary mask for each segment
3. averaged -> thresholded -> binary segment mask on Conv5_3
* Deep Contrast Network Training  
Steps to fine-tune the two streams  
1. fix the parameters in the second stream and train the first stream for one epoch  
2. fix the parameters in the first stream and fine-tune the neural network in the second stream for one epoch using groundtruth saliency maps (exchange with step 1)  

# Future Work  
extend their framework to learn joint spatio-temporal observation policies  
