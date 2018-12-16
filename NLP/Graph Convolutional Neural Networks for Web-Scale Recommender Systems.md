# Paper
* link: https://arxiv.org/pdf/1806.01973.pdf
* author: Rex Ying, Ruining He, Kaifeng Chen, Pong Eksombatchai, William L. Hamilton, Jure Leskovec
* year: 2018
* codes and models: TBD

# Summary  
PinSAGE (an extension of GraphSAGE)  
DNN on graph -> ✔️ recommend system  
✘ web-scable  
PinSAGE: efficient random walks + graph convolutions  
-> embedding nodes(items), info: graph structure + node feature  

# Backgroud
scale up GCNs difficult:  
eg: require full graph Laplacian -- infeasible assumption  

# Idea: Improve on GraphSAGE
1. ✘ whole graph stored in GPU  
low-lantency random walks to sample graph neighborhoods in a producer-customer architecture  
2. new training techniques  
MapReduce pipeline  

# Model  
* Forward propagation  
importance pooling:   
random walks from node u and compute L1 visit count -> select top T  
adv:  
1. fixed numbers -> control memory footprint   
2. take into importance when aggregating  
mean -> weighted mean       
* Stacking convolution  
* Train
supervised: max-margin ranking loss
loss function:   
maximize the inner product of positive examples  
ensure inner product of negtive examples is smaller than the positive sample by some pre-defined margin  
1. Multi-GPU training with large minibatches
2. Producer-comsumer minibatch construction
The model computations are in GPUs   
extracting features, re-indexing, and negtive sampling are computed on CPUs  
-- we design a producer-consumer pattern to run GPU computation at the current iteration and CPU computation at the next iteration in parellel  
3. Sampling negative items
Hard negative items: somewhat related to the query item q, but not as related as the positive item i  
-> doubles epoches to converge  
first epoch: no hard negative item  
subsequent epoches: add hard negative item (epoch n, add n-1)  
4. Node Embedding via MapReduce
✘ repeated computations  
latent vector for each node is computed only once  
5. Efficient nearest-neighbor lookups
Approx KNN by locality senstive hashing  
