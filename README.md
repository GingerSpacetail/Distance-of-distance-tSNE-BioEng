# Distance-of-distance transformation to improve t-SNE embedding in face of scattering noise in data

Jinke Liu , Martin Vinck 
## Introduction 
In this project, we introduce a simple transformation on the distance matrix based on the neighboring relationship, so that the scattering noise in the data, if any, can be attracted to each other. Thus, the transformation helps separate the the clusters in the dataset from the scattering noise and improve the low-dimensional t-SNE embedding.  

## Installation 
The following examples were run in the Python virtual environment with dependencies listed below:
1. ```conda install python=3.6.5```
2. ```conda install matplotlib```
3. ```conda install torch```
4. ```conda install spotDist```
5. ```conda install allensdk```


## Method 
For each pair of data points, we consider the joint set of K neighbours of these two data points, and then compute the distance of distance w.r.t. this set of neighbour points. Using this transformation, we should be able to obtain a high similarity between scattering noise points, while relatively retaining the distances from noise points to the clusters, and the distances between the clusters.

``` dis_of_dis_transform ``` performs the distance-of-distance transformation.


## Results

### Example: GMM simulation  
Gaussian Mixture Model to generate cluster data and scattering noise points. We showed that distance-of-distance transformation can alleviate the overlapping of noise points onto clusters in the low-dimensional t-SNE embeddings. 

notebook ``` simulate.npy``` samples data points from Gaussian Mixture models and tests distance-of-distance transformation. 

### Example: CNN representation of image patches 
We took natural images of 20 different object classes from PASCAL VOC2007 dataset. Patches were cropped out of the images that either contain the object or contain only the random pixels without the object. We used the activaty pattern in the activation layer of a pretrained AlexNet as their representations. We showed that with distance-of-distance transformation, the object patches were more successfully separated from the random patches.  

notebook ``` alex.npy``` extracts the CNN representations of object/random patches and tests distance-of-distance transformation.  

### Example: Neural represenation of drifting grating stimulus
We took Allen Institute Brain Observatory dataset [[1]](#1). Mice were shown drifting grating visual stimulus moving in 8 different directions on the screen while being electrophysiologically recorded. Between the stimulus presentations, the neural activities were considered as the spontaneous activities. We compare the evoked neural response in V1 with the spontaneous activities. Using SpotDist metric [[2]](#2), we measured the dissimilarity between the spiking patterns. We showed that distance of SpotDist can separate the spontaneous activities from evoked response while maintaining the clustering properties.    

notebook ``` spotdist.npy``` computes the neural representations of drifting grating stimuli and grey screen and tests distance-of-distance transformation.  


## References
<a id="1">[1]</a> 
Siegle, Joshua H., et al. "Survey of spiking in the mouse visual system reveals functional hierarchy." Nature 592.7852 (2021): 86-92.

<a id="2">[2]</a> 
Grossberger, Lukas, Francesco P. Battaglia, and Martin Vinck. "Unsupervised clustering of temporal patterns in high-dimensional neuronal ensembles using a novel dissimilarity measure." PLoS computational biology 14.7 (2018): e1006283.
