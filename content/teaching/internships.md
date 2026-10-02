## Introduction

This page maintains a list of possible internships.
For context, I'm associate professor at Lyon 1 University, LIRIS lab, in the [DM2L](https://projet.liris.cnrs.fr/dm2l/) team, Data Mining and Machine Learning.   
I'm interested in the analysis of complex networks, and more generally in the analysis of complex systems. I'm also interested in the application of those methods to real world problems, in particular in the field of epidemiology, virology, cryptocurrencies, volcanic plumbing systems, science of science.   

  

## INTERNSHIPS WITH FUNDING

In 2024/2025, I have targeted fundings with co-supervision for 2 topics:

- [Graph Neural Networks with Attention to Understand the Colonization of Mosquito Larval Habitats According to their Biotic and Abiotic Characteristics](https://liris.cnrs.fr/sites/default/files/emploi/anr_serious_internship2023_cvm.pdf)
- [Self-supervised learning for link prediction](https://liris.cnrs.fr/sites/default/files/emploi/ssl4lp.pdf)

## Ph.D. OFFER WITH FUNDING (+POSSIBLE INTERNSHIP)

I also have one funding for a Ph.D., and it is possible to start by an internship on this topic: [**A complex system model of volcanic plumbing systems: Integration of physical models and network structures**](https://cazabetremy.fr/Teaching/Internships/PhD_volcan-4.pdf)    
Below, I propose a list of other internships, for which I can provide funding for highly motivated students.   

## Structure analysis in static networks/complex systems (communities, etc...)

### A measure to evaluate the quality of community partitions based on link prediction

Knowing which community detection methods gives the most useful result is a common problem in community detection. I propose to adopt a without apriori/model free approach by considering that the best model is the one which is the most useful to predict hidden/future links. This raises a lot of questions, such as how to do this link prediction based on the partition, how many edges we should hide, etc.

### Inference of Gravity Model for graphs without apriori on the deterrence function

In previous works < href="https://hal.science/hal-01500354/document">[1], we have shown that the gravity model, a classic model in spatial economics, can be used to infer the structure of a graph. However, the deterrence function, which models the cost of interaction between nodes, is usually assumed to be a power law. We propose to relax this assumption and to infer the deterrence function from the data, using machine learning methods. This will allow to infer the structure of a graph without apriori on the deterrence function.

### Discovering spatial position of nodes using graph-embedding or bayesian inference

Imagine a spatial graph in which the probability to observe an edge depends on the distance between nodes. Now let's say that we remove the position information from the nodes. Would it be possible to re-infer the relative position of nodes from the graph? And/Or to know if the graph had a spatial structure to begin with? In theory, this is more or less what graph-embedding methods should do. But naive experiments show that it does not seem to work. I have some intuitions of why, and you will tackle this problem: can you show when it is possible and when it isn't, and/or propose a method to solve this problem?

### Study the influence of random graph structure on network properties and/or diffusion on networks

In a recent work, we introduced Structify-Net, a method and library to generate random graph with a customizable structure define by a function provided as parameters. This allows to generate networks with non-standard organization, beyond blocks and spatial structure. You will use this library to study the influence of the structure of random graphs on network properties and/or diffusion on networks. For instance, how does the robustness of a network to random failures depends on its structure? How does the convergence of an opinion dynamic model depends on the structure of the network? etc.

## Graph Neural Networks

### Variational Graph AutoEncoder adapted for Stochastic Block Models

Variational Graph AutoEncoder (VGAE) are a classic approach to learn a low dimensional representation of a graph, making the assumtion that node position in the latent space follows a gaussian distribution. Stochastic Block Models (SBM) are a classic generative model for graphs, in which nodes are grouped into communities, and the probability of an edge depends on the community of the nodes. You will adapt VGAE to learn a latent representation of a graph that follows a SBM generative model, and compare it with existing methods.

### Deep Learning for Community Detection

Several methods have been proposed recently to do community detection based on deep neural networks. You will do a state of the art of those methods, compare them empirically, and if you are motivated, propose your own method using such an approach

## Network science and LLM

Large language models are certainly one of the most important breakthrough in AI in the last decade. They are based on the idea that a model can be trained to predict the next word in a sentence, and that this model can then be used for a wide range of tasks. As for any deep neural network, the model is composed of *parameters*, or weights, which control the "neurons" of the neural network. The objective of this internship would be to start from a pretrained model such as llama or mistral, to download the weights of the model, and then to propose a modeling of this data in term of a network. The objective will therefore to use network science tools, such as community detection or centralities, to better understand the organization of such models, both "post mortems", i.e., the weights themselves, or in a "IRM" fashion, i.e., observing the evolution of the activity inside the "brain" when answering some specific requests. This is an exploratory subject, and the objective is to explore the potential of this approach, and to propose new methods to analyze those models.  

## Dynamic Networks / Communities

### Dynamic community detection in Links streams by cutting nodes/edges

There are barely any method able to detect dynamic communities in link streams without transforming them first in snapshot sequences. I have developed some prototypes of methods for such graphs, based on the principle of cutting dynamic nodes and dynamic edges, for instance based on their dynamic betweeness, in a way similar to the classic Girvan Newman approch. The results are promissing, but several difficulties remain and the code is obsolete. You will continue the research in this direction.

### Better community matching in dynamic networks

A classic method to detect communities in dynamic networks composed of sequences of snapshots is to 1)detect communities in each snapshot and 2)Match the communities between adjacent snapshots. This second step has been very little studied, with only 3 or 4 methods proposed, and no serious comparison of their strenghts/weaknesses. You will start by comparing existing approach and then propose your own.

### Transform a link stream into a stable dynamic network.

A link stream is highly unstable. When transforming a link stream into a sequence of snapshots, the classic approach consists in chosing a time window, a threshold of number of edge observations during that window, and to create 1 snapshot for each window (possibly sliding windows).
In a recent paper proposed after a similar internship, we have shown that this approach always seem to yield highly unstable snapshot sequences, that could not be visualized "as a movie". Your objective will be to develop such a method, which, with appropriate constraints and pruning, will extract the "backbone" of the dynamic graph, i.e. a representation stable enough so that it can be visualized "as a movie".  

## Other graph problems

### Decision Graph

This subject is more a machine learning than a graph topic. Decision trees are classic methods for supervised machine learning. But trees are just very limited graphs, right? Could we design a method similar to a decision tree, but having a graph structure, allowing to factorize branches? We could imagine using an agglomerative approach instead of a divisive one for instance, and take inspiration from higher-order sequential approach to select an appropriate number of nodes...
