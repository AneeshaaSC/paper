# Paper
* link: https://arxiv.org/abs/1706.02216
* author: William L. Hamilton, Rex Ying, Jure Leskovec
* year: 2017
* codes and models: https://github.com/stephenyan1231/dl-image-enhance

# Summary  
embedding nodes in graph  
improve:  
unseen nodes  
transductive -> inductive  

# Idea
train individual embedding for each nodes ->  
generate embeddings by sampling and aggregating features from a node's local neighborhood  
fixed graph ->  
unseen nodes / new (sub)grapghs  

# Framework: GraphSAGE  
* Algorithm: Aggregate every level and cancat  
outer loop: K (level)  
inner loop: v (neighbors)  
* Unsupervised: Graph-based loss function    
encourage nearby nodes -- similiar representaions  
disparate nodes -- distinct representations  
* Aggregator  
Symmetry function -> arbitrarily ordered nodes  
1. mean  
2. LSTM (not symmestry, need to use random permuation of inputs)  
3. max pooling  
4. GCN (CNN on graph)  

# Experiment    
* GraphSAGE performs good  
* pooling version performs good and fast  

# Analysis  
can approx artitrary percision (theorem based on pooling)    

# Future  
neighbors sampling function can be various  
