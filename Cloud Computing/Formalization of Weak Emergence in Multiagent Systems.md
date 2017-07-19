# Paper
* link: http://www.comp.nus.edu.sg/~teoym/pub/15/2015-Sep-TOMACS-Formalization-of-Weak-Emergence-in-Multiagent-Systems.pdf
* author: Claudia Szabo, Yong Meng Teo
* year: 2015

# Summary
A grammar-based approach to formalize and identify the existence and extent of emergence without the need for prior knowledge of emergent properties. Moreover, reduction of state-space explosion through the use of our proposed degree of interaction metrics.

## Current Ways Problems (Related Works) 
1. A prior observation of an emergent property is required
2. Limited assumptions and constraints when applied to larger systems.  

## Proposed Approach
* identification of emergent properties:  
![emergent-properties](https://github.com/VickyPapa/paper/blob/master/pic/emergent-properties.png)  
implict assumption:  
the size of Lwhole is dependent on the number of interactions and state transition rules and represents a subset of interest from all the rules in a given system.   
* steps:  
modeling the system using our proposed formalism.  
the application of our method for emergence identification as the system is running.  
* future works:  
having other agent formalisms translated into proposed formalism to increase the usability of proposed formalism.  

## FLOCK-OF-BIRDS MODEL
* Model  
macro-level:  
V-like formation  
micro-level: (each obeys three simple rules)  
(1) separation: steer to avoid crowding neighbors  
(2) alignment: steer toward average heading of neighbors  
(3) cohesion: steer toward average position of neighbors  
details corresponding to "Proposed Approach" part  
* Experimental Analysis  
State-Space Explosion:  
more interactions between birds lead to more emergent property states that cannot be derived by summing the independent agents’ behaviors  
State-Space Reduction:  
1. Lw I hole grows as expected, but soon drops -> a larger number of birds encourages more interactions  
2. the system states due to weak interaction are small and tend to decrease with the number of birds -> the close relationship between the size of the bird population and the degree of interaction  \
3.  Lo is small compared to Lξ -> needs to be further investigated with two possible reasons  
Result: good efficiency  

## Future work
1. to ensure that this approach is universally applicable, further experimentation is required
2. predator–prey and social networks  

