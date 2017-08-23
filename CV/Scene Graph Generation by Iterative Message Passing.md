# Paper
* author: Danfei Xu, Yuke Zhu, Christopher B. Choy, Li Fei-Fei
* year: 2017

# Summary  
propose a end-to-end model that generates a visually-grounded scene graph from an image  

## Related Work & Improvement  
* Scene understanding and relationship prediction  
problem: these works focus on image-level predictions without detailed visual grounding  
improvement: with joint inference  
* Visual scene representation  
problem: either using ground-truth annotations, or extracting the graphs from other modalities  
improvement: generating scene graphs directly from images  
* Graph inference  
problem: they focus on node inference while treating edges as pairwise constraints  
improvement: we enable edge predictions using a novel primal-dual graph inference scheme  
problem: Structural RNN only makes one-time predictions along the temporal dimension  
improvement: iteratively refines its predictions through message passing  

## Model
![ArchitecturePic](https://github.com/VickyPapa/paper/blob/master/pic/SceneGraphGenerationbyIterativeMessagePassing.jpg)  
