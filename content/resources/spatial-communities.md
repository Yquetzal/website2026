## Short presentation

You probably know about community detection, also known as graph clustering or graph partitioning.

A typical way to do it is to optimise a Quality function known as Modularity. Modularity is defined, for a given graph and a given partition, as the difference between the fraction of edges inside communities in the graph and in a null model, usually the configuration model.

A variant of this problem has been proposed for spatial (or geographic) networks, networks in which nodes are located in a space.
On these networks, clusters found by modularity optimisation put in the same clusters nodes that are located close to each other.
But on some networks, this information is not very useful, as we already know this information (we known which nodes are close to other nodes.)
In order to learn something about the organisation of the network, we must first "correct" for the spatial structure.

  
A solution to do this, proposed in previous works, is to use a modified version of the modularity, in which the null model is determined by a "gravity model", a classic model in geography for trip distribution

In two articles published in 2017, we shown that the previous algorithms using this approach have a systematic bias: the gravity based null model underestimate the weight (or the probability of observing an edge) of edges between nodes located at the "periphery" of the space.
We proposed a doubly constrained procedure that solves this problem.

## Communities using the configuration Model as Null model

![comsLyonConfig](https://cazabetremy.fr/assets/images/comsLyonConfig.jpg)

  
Communities found by a "normal" community detection on the network of bicycle trips using the bicycle Sharing System in Lyon city, France

## Communities using a Degree Conserving gravity Null model

![comsLyonUs](https://cazabetremy.fr/assets/images/comsLyonUs.jpg)

  
Communities found by the space corrected version of community detection on the same network. We can observe that some found communities are not only spatial. In particular, a community of station (brown) is discovered between the two main parks of the city, and including the banks of the Rhone river.
This probably corresponds to typical leisure trips in the city.

## More information

The code is provided in Python. One function must be called to compute the gravity null model. Another function must be called to run the community detection using the input null model.

Both the original version of the gravity null model and our doubly constrained method are implemented.

I plan to upload a runnable version that only takes as input a graph and a list of nodes positions. If you think it is useful, let me know !

[Code on GitHub](https://github.com/Yquetzal/spaceCorrectedLouvainDC)
[Article in Complex Networks conference](https://www.researchgate.net/publication/313900762_Using_Degree_Constrained_Gravity_Null-Models_to_understand_the_structure_of_journeys%27_networks_in_Bicycle_Sharing_Systems)
[Article in ESANN conference](https://www.researchgate.net/publication/313371093_Enhancing_Space-Aware_Community_Detection_Using_Degree_Constrained_Spatial_Null_Model)
