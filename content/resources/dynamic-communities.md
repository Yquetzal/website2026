### Dynamic Community Discovery: a (Live) Survey

This page is a live version of the article: [Community Discovery in Dynamic Networks: a Survey](https://arxiv.org/abs/1707.03186), written by [Giulio Rossetti](http://www.giuliorossetti.net) and myself. Please note that some of the contents of this page are not in the original survey, so, if you use it, please add a reference to this page.

##### About this page

The weakness of all survey article is that they are obsolete as soon as they are published, as new methods are proposed all the time. At first, we wanted to maintain actively a **live survey**, adding new methods as soon as they were published, but this task is actually too time consuming.   
As an inbetween solution, we propose this page which contains references and description of all methods included in the published survey, and we offer the possibility to all researcher to include their own method, if it was not already present.   

This first attempt is managed *manually*: you need to send us an email with all useful information (summary of your method in a few lines, reference to the article, reference to an implementation if available, etc.)  

The mechanism could be upgraded to a wiki-like behaviour. If you want to propose an improved version of it, feel free to contact us, we are very open to a take over by someone else with motivation/time/fresh ideas.

### Categories

Organisation of Dynamic Community Discovery methods in categories and sub-categories.   
Descriptions of the sub-categories follow below.  

#### **(A)** Instant Optimal

Clusters at *t* depends **only on the current state** of the network  
Clusters are **non-temporally smoothed**  
(Communities **labels**, however, can be smoothed)

#### **(B)** Temporal Trade-Off

Clusters at *t* depends  **on current and past states** of the network  
Clusters are **incrementally temporally smoothed**

#### **(C)** Cross-Time

Clusters at *t* depends on **both past and future** states of the network   
Clusters are **Completely temporally smoothed**  

### Methods

This table lists all methods included in the original survey, plus methods contributed by authors, marked with the symbol .  
If you want to add your own method, complete something or spot a mistake, feel free to [tell us](mailto:remy.cazabet@gmail.com?Subject=Dynamic%20Community%20Discovery%20Live).

  

  

##### A1 - Iterative Similarity-based approaches

×In similarity-based approaches, a quality function is used to quantify the similarity between communities in different snapshots (e.g., Jaccard among node sets).   
Communities in adjacent time-steps having the highest similarity are considered part of the same dynamic community. Particular cases can be handled, such as a lower threshold of similarity, or the handling of \(1\) to \(n\) or \(n\) to \(n\) matchings, thus defining complex operations such as split and merge.

##### A2 - Iterative Core-nodes based approaches

×Methods in this subcategory identify one or several special node(s) for each community -- for instance those with the highest value of a centrality measure -- called **core-nodes**. Two communities in adjacent time-steps containing the same core-node can subsequently be identified as part of the same dynamic community. It is thus possible to identify splits or merge operations by using several core-nodes for a single community.

##### A3 - Multi-step matching

×Methods in this subcategory do not match communities only between adjacent time-steps. Conversely, they try to match them even in snapshots potentially far apart in the network evolution. The matching itself can be done, as in other sub-categories, using a similarity measure or core-nodes. The removal of the adjacency constraint allows to identify *resurgence* operations, i.e. a community existing at \(t\) and \(t+n\) but not between \(t+1\) and \(t+(n-1)\). It can, however, increase the complexity of the matching algorithm, and *on-the-fly* detection becomes inconsistent, as past affiliations can change.  

These methods allows a smoothing of the communities of labels

##### B1 - Update by Global Optimization

×A popular method for static CD is to optimize a Global Quality Function, such as Modularity or Conductance.   

This process is typically done using a heuristic (gradient descent, simulated annealing, etc) that iteratively merges and/or splits communities, and/or moves nodes from a community to another until a local or global maximum is reached.   

Methods in this subcategory use the partition existing at \(t\) as a seed to initialize a Global optimization process at \(t+1\).
The heuristic used can be the same as in the static case or a different one.
A typical example of a method in this category Aynaud-2010 consists in using the Louvain algorithm: in its original definition, at initialization, each node is in its community.   
The *partition update* version of it consists in initializing Louvain with communities found in the previous step.

##### B2 - Update by Set of Rules

×Methods in this subcategory consider the list of network changes (edge/node apparitions, vanishing) that occurred between the previous step and the current one, and define a list of rules that determine how networks changes lead to communities update.   
Methods that follow such rationale can vary significantly from one to the other.

##### B3 - Informed CD by Multi-objective optimization

×When addressing community detection on Snapshot Graphs, two different aspects need to be evaluated for each snapshot: partition quality and temporal partition coherence.   
The multi-objective optimization subclass groups together algorithms that try to balance both of them at the same time so that a partition identified at time $t$ represents the natural evolution of the one identified at time \(t-1\).   
This approach optimizes a quality function of the form:
\[
c = \alpha CS + (1-\alpha) CT
\]
with \(CS\) the cost associated with current snapshot (i.e. how well the community structure fits the graph at time \(t\), and \(CT\) the smoothness w.r.t. the past history (i.e., how different is the actual community structure w.r.t. the one at time \(t-1\) and \(\alpha \in [0,1]\) is a correction factor.   

An instantiation of such optimization schema could be defined using **modularity** as \(CS\) and **Normalized Mutual Information** as \(CT\) as done in Folino-2010.

##### B4 - Informed CD by network smoothing

×Methods in this subcategory search for communities at \(t\) by running a CD algorithm, not on the graph as it is at \(t\), but on a version of it that is *smoothed* according to the past evolution of the network, for instance by adding weights to keep track of edges' age. In a later step, communities are usually matched between snapshots, as in typical *Two-Stage* approaches.  
Contrary to previous subcategories, it is not the previous communities that are used to take the past into account, but the previous state of the network.

##### C1 - Fixed Memberships, fixed properties

×Methods in this subcategory do not allow nodes to switch communities, nor communities to appear or disappear.
They also assume that communities stay the same throughout the studied period.   
As a consequence, they search for the best partition, *on average*, over a time period.   
In most cases, they improve the solution by slicing the evolution in several time periods, each of them considered homogeneous, and separated by dramatic changes in the structure of the network, a problem related to change point detection.

##### C2 - Fixed memberships, evolving properties

×Methods in this subcategory are aware that communities are not homogeneous along time.   
For instance, nodes in a community can interact more actively during some recurrent time-periods (hours, days, weeks, etc.), or their activity might increase or decrease along time.   
To each community -- whose membership cannot change -- they assign a temporal profile corresponding to the evolution of its activity.

##### C3 - Evolving memberships, fixed properties

×Methods in this subcategory allow node memberships to change along time, i.e., nodes can switch between communities.   
However, because they use Stochastic Block Models approaches, for which the co-evolution of memberships and properties of communities is not possible (see Matias-2015), the number of communities and their density is fixed for the whole period of analysis.

##### C4 - Evolving memberships, evolving properties

×Methods in this category do not impose constraints on how dynamic communities can evolve: nodes can switch between them, communities can appear or disappear, and their density can change.   
Two main approaches are currently present in this category:

- Edges are added between nodes in different snapshots. Static community detection algorithms are consequently run on this trans-temporal network
- Searching for persistent cliques of a minimal size in link streams.

##### Column Dynamicity

×Dynamic networks can be represented by several means:  

- Snapshots: The network evolution is represented by an ordered series of static graphs
- TN-Interval Graph: The network is a temporal network (no snapshots), edges exist during intervals. It is assumed that the network is relatively *stable*, i.e communities found by dynamic algorithms at \(t\) should be close to what a static algorithm would find on the static network defined by existing edges at that time
- TN-Instantaneous: The network is a temporal network (no snapshots), edges are transient, they have no duration, therefore the network is never fully defined at a given time \(t\)

##### Community Definition

×There is no universally accepted definition of what are good communities, or good graph clusters. This column states for each method the definition it adopts.   

It can be one of commonly used definitions (Stochastic Block Model, Modularity, etc.) or one of the following ones:   

- Independent (PP): The method is not dependent on a particular definition, because it is a Post Process (PP), i.e any static method can be used in the first place to find non-dynamic communities, and the method "makes the link" between them.
- Ad hoc: This method does not rely on a well-known definition of communities, but define an Ad hoc process, usely ensuring that communities are dense and well separated from the rest of the network.
- Ad hoc static: the method uses as a first step a particular static community detection algorithm that cannot be obviously related to a well known community definition.

## Referenced methods

### Agarwal-2018

[Article](https://arxiv.org/abs/1802.04593) · 2018 · Category: B5 (Update Local Optimization)

Community definition: Independant. Dynamicity: TN-Interval Graph.

*Contributed after publication of the survey.*

Code: [By authors](https://tinyurl.com/dyperm-code)

DyPerm is the first dynamic community detection method that adopts an effective community goodness metric, called “permanence” and optimizes it to incrementally detect the community structure. The benefits of adopting permanence as an optimization function are two-fold:

* Permanence, being a local vertex-centric metric (as opposed to the global network-centric metrics such as modularity, conductance), allows us to reassign communities to only those nodes whose associated topological structure has changed, and guarantees that the remaining nodes do not affect the optimization. This leads to very low computing complexity in updating the community structure when the network changes dynamically.
* Incremental changes in the local portion of the community structure guarantee that the resultant communities are highly correlated with that in the previous time-stamp. We present theoretical justifications why/how mere changes in the community structure lead to maximize permanence.

### Lorenz-2017

[Article](https://doi.org/10.1007/978-3-319-72150-7_33) · 2017 · Category: A3

Community definition: Independant (PP). Dynamicity: Snapshots.

*Contributed after publication of the survey.*

Code: [By authors](https://github.com/philipplorenz/memory_community_matching)

This method provides a similarity measure for solving the matching problem, that arises from detecting communities on discrete snapshots.   
The memory-Jaccard similarity of \(n\)-th order is introduced, which sums up all non-zero overlaps of two communities \(A\) and \(B\) within a given time window \(n\) trailing the current timestep \(t\):\[ M(A,B\_t) = \sum\_{i=1}^{n} \frac{1}{i} \frac{\vert A\_{t-i} \cap B\_t \vert}{\vert A\_{t-i} \cup B\_t \vert}. \] This happens recursively, starting from the first available snapshot at \(t=1\), with the history of each community then building up and contributing to future overlaps, while the memory kernel \(1/i\) mitigates the influence of communities further in the past. The matching problem can be solved by maximizing the overall sum \(\sum\_{\substack{B\_t \\ B\_t = A}} M(A, B\_t)\) in each timestep \(t\) by renaming \(B\) optimally. This method stabilizes long-term developments that evolve on larger timescales than \(n\), by canceling out temporally uncorrelated fluctuations. It avoids loosing track of communities that are small in size or undergo periodic occurrence with intervals smaller than \(n\). 

### Hopcroft-2004

[Article](http://dx.doi.org/10.1073/pnas.0307750100) · 2004 · Category: A1

Community definition: Ad hoc. Dynamicity: Snapshots.

The algorithm in (Hopcroft et al., 2004) can be seen as the ancestor of all approaches within this category. It first finds natural communities in each snapshot by running the same algorithm for community detection several times and maintaining only those communities that appear in most runs. In a second phase, similar communities of successive snapshots are matched together using a match function defined as:   
 \[ match(C,C') = Min\left(\frac{|C \cap C'|}{|C|},\frac{|C\cap C'}{|C'|}\right) \]   
 with \(C\) and \(C′\) the clusters to compare treated as sets.

### Palla-2007

[Article](https://doi.org/10.1038/nature05670) · 2007 · Category: A1

Community definition: Cliques based. Dynamicity: Snapshots.

The algorithm proposed in (Palla et al., 2007) is based on clique percolation (CPM [Palla et al., 2005](https://doi.org/10.1038%2Fnature03607)). CPM is applied on each snapshot to find communities. The matching between these communities is done by running CPM on the joint graph of snapshots at t and t + 1. Due to the formal definition of communities pro- vided by CPM (communities are composed of cliques), communities of the joint graph can only grow compared to those of both snapshots. The authors also discuss how the knowledge of the temporal commitment of members to a given community can be used for estimating the community’s lifetime. They observed that while the stability of small communities is ensured by the high homogeneity of the nodes involved, for large ones the key of a long life is continuous change.

### Bourqui-2009

[Article](https://doi.org/10.1109/ASONAM.2009.55) · 2009 · Category: A1

Community definition: Ad hoc static. Dynamicity: Snapshots.

Code: ?

In this article, an approach based on dynamic graph discretization and graph clustering is proposed.   
The framework allows detection of major structural changes over time, identifies events by analyzing temporal dimensions and reveals hierarchies in social networks.   
It consists of four major steps:

1. The social network is decomposed into a set of snapshot graphs;
2. Clusters are extracted from each static graph separately using an overlapping CD algorithm, to produce overlapping structures. This step allows to identify communities in the network but also its pivots (vertices shared by several clusters) while being insensitive to minor changes in the network;- Major structural changes in the network are detected by comparing the clustering obtained on every pair of successive static graphs using a similarity measure (cluster representativeness, e.g., the geometrical mean of the normalized ratio of common elements between two clusters).   
     Thus, the temporal changes in the input network are decomposed into periods of high activity and **consensus** communities during stable periods
   - An influence hierarchy in the **consensus** communities is identified using an MST (Minimum Spanning Tree).

### Asur-2007

[Article](https://doi.org/10.1145/1631162.1631164) · 2007 · Category: A1

Community definition: Ad hoc static. Dynamicity: Snapshots.

Code: ?

In this article, the authors approach the problem of identifying events in communities: MCL (a modularity based algorithm) is applied to extract communities in each time step.   
A set of events (Continue, kMerge, kSplit, Form, Dissolve, Join, Leave) are defined. For instance, kMerge is defined as: \(kMerge(C^k\_i,C^l\_i,k)=1\) iff \(\exists C^j\_{i+1}\) such that \[ \frac{|(V^k\_i \cup V^l\_i) \cap V^j\_{i+1}|}{Max(|V\_i^k \cup V^l\_i|,|V^j\_{i+1}|)}>k\% \] and \(|V^k\_i \cap V^j\_{i+1}|>\frac{|C^k\_i|}{2}\) and \(|V^l\_i \cap V^j\_{i+1}|>\frac{|C^l\_i|}{2}\), with \(i\) representing time steps.

### Rosvall-2010

[Article](https://doi.org/10.1371/journal.pone.0008694) · 2010 · Category: A1

Community definition: Information Compression. Dynamicity: Snapshots.

Code: [By authors](http://www.tp.umu.se/~rosvall/code.html)

In this article, the authors propose a method to map changes in large networks. To do so, they focus on finding stable communities for each snapshot, by using a bootstrap resampling procedure accompanied by significance clustering.   
More precisely, for each snapshot, 1000 variations of the original network are generated, in which the weight of each edge is taken randomly from a Poisson distribution having as mean the original weight of the edge.   
All of these alternative networks are clustered using a static algorithm.   
To find significant communities, the authors propose to search for modules, largest sets of nodes that are clustered together in more than 95\% of networks.   
These small node sets are grouped into larger clusters if their nodes appear together in more than 5\% of network instances. Clusters corresponding to different time steps are linked if the number of common nodes is higher than a user-defined threshold. 

### Bota-2011

[Article](https://doi.org/10.14232/actacyb.20.1.2011.4) · 2011 · Category: A1

Community definition: Ad hoc static. Dynamicity: Snapshots.

Code: ?

In this article, the authors propose an extension of the basic community events described in Palla-2007 and an approach capable of handling communities identified by a non-monotonic community detection algorithm (\(N^{++}\) ). The proposed method works on snapshots and uses for each pair of adjacent network observation **union** (and **intersection**) graphs to perform community matching. The final goal of this approach is to build an extended community life-cycle.   
In addition to the classical events defined in Palla-2007, 5 meta-events are introduced to capture the combinations of standard events: Grow-merge, Contraction-merge, Grow-split, Contraction-split and Obscure case (which envelop more complex, non-binary, transformations).

### Takaffoli-2011

[Article](https://www.aaai.org/ocs/index.php/ICWSM/ICWSM11/paper/viewPaper/2853) · 2011 · Category: A1

Community definition: Independant (PP). Dynamicity: Snapshots.

Code: ?

This method is designed to track the evolution of communities. First, a static community detection is run on each snapshot, using an existing algorithm. In a second step, communities matching and operations are done according to a set of rules, that can be summarized as:

* Two communities are matched if they have at least a fraction \(k\) of the nodes of the largest one in common;* A new community is born if it has no match in the previous snapshot;* A community dies if it has no match in the following snapshot;* A community split if several other communities have more than a fraction \(k\) of its nodes;* A merge occurs if a community contains at least a fraction \(k\) of several other communities.

### Greene-2010

[Article](https://doi.org/10.1109/ASONAM.2010.17) · 2010 · Category: A1

Community definition: Independant (PP). Dynamicity: Snapshots.

Code: ?

This method is designed to track the evolution of communities in time evolving graphs following a two-step approach: (i) community detection is executed on each snapshot with a chosen static algorithm and then (ii) the Jaccard coefficient is used to match communities across adjacent snapshots. Communities are matched if their similarity is above a user-defined threshold, allowing many-to-many mappings.

### Brodka-2013

[Article](http://dx.doi.org/10.1007%2Fs13278-012-0058-8) · 2013 · Category: A1

Community definition: Independant (PP). Dynamicity: Snapshots.

Code: ?

The GED method is designed to identify what happened to each node-group in successive time frames: it uses not only the size and equivalence of groups' members but also takes into account their position (e.g., via node ranking within communities, social position...) and importance within the group.   
This approach is sustained by a new measure called **inclusion**, which respects both the **quantity** (the number of members) and **quality** (the importance of members) of the group. The proposed framework is parametric in the static CD algorithm to be applied on each network snapshot to extract node-groups (communities).

### Dhouioui-2014

[Article](https://doi.org/10.1109/ASONAM.2014.6921672) · 2014 · Category: A1

Community definition: Ad hoc static. Dynamicity: Snapshots.

Code: ?

This method uses the OCDA algorithm (Dhouioui-2013) to find overlapping communities in each snapshot.   
 Then, relations are found between similar communities in different snapshots. A Data Warehouse layer memorizes the evolution of the network and its communities.

### Ilhan-2015

[Article](https://doi.org/10.1145/2808797.2808913) · 2015 · Category: A1

Community definition: Independant (PP). Dynamicity: Snapshots.

Code: ?

In this method, an evolving network is represented by a series of static snapshots. Communities are determined using the Louvain algorithm (Blondel-2008), then matched using a custom similarity metric.   
 The evolution of communities is labeled with the events they experienced (survive, grow, shrink, merge, split and dissolve).   
Moreover, the authors propose to forecast future evolution of communities.   
To do so, a broad range of structural and temporal features are extracted covering many properties of both the internal link structure and the external interaction of each community with the rest of the network.   
 A temporal window length is defined to generate time series for each feature, thus for each community, a set of time-series is built.   
Then, ARIMA (Auto Regressive Integrated Moving Average) model is applied to estimate the next values of the features.   
 The communities with the forecasted feature values were then used as test set for several classification algorithms trained using the rest of the window length snapshots as the training set.

### Wang-2008

[Article](https://doi.org/10.1007/978-3-540-88192-6_22) · 2008 · Category: A2

Community definition: Independant (PP). Dynamicity: Snapshots.

Code: ?

This method proposes to use the concept of core nodes to track the evolution of communities.   
 It is agnostic w.r.t. the CD algorithm used to detect communities on each snapshot.   
For each snapshot, a voting strategy is used to select a few core nodes.   
 Finally, the tracking of communities can be done by tracking the core nodes.

### Chen-2010

[Article](https://doi.org/10.1109/ICDMW.2010.32) · 2010 · Category: A2

Community definition: Cliques based. Dynamicity: Snapshots.

Code: ?

In this article, the authors adopt a conservative definition of communities, i.e., they define them as the maximal cliques of the graph.   
 They consequently introduce **Graph representatives** and **Community representatives** to limit the search space and avoid redundant communities.   
 They are defined as follows:

* **Graph representatives**: Representatives of graph \(G\_t\) are the nodes that also appear in \(G\_{t-1}\), \(G\_{t+1}\),or both. Nodes that only appear in one graph are called graph dependent nodes.   
   If a community only contains graph-dependent vertices, then it can be considered as a *graph-dependent* community, not dynamic one
* **Community representatives**: A community representative of community \(C\_i^t\) is a node in \(C\_i^t\) that has the minimum number of appearances in other communities of the same graph \(G\_t\).

The proposed approach first finds **graph representatives** and enumerates the communities that are seeded by the graph representatives to avoid considering redundant communities.   
 Then, in every generated community, it selects only one node as a community representative and uses community representatives to establish the predecessor/successor relationship between communities of different time-steps.   
 Once all predecessors and successors have been found, it finally applies decision rules to determine community dynamics. 

### Falkowski-2006

[Article](https://doi.org/10.1109/WI.2006.118) · 2010 · Category: A3

Community definition: Independant (PP). Dynamicity: Snapshots.

Code: ?

In this article (also in Falkowski-2007), a three-step approach is applied to detect subgroups in social networks:

* In the first step, communities are found in each snapshot using a static CD algorithm.
* In the second step, communities in different snapshots are linked based on their similarity, using the overlap measure: \(overlap(x,y)=\frac{|x\bigcap y|}{min(|x|,|y|)}\). This creates a *Community survival graph*.
* In the third step, a community detection algorithm is run on the *Community survival graph*, thus finding communities relevant across several snapshots.

### Goldberg-2011

[Article](https://doi.org/10.1109/PASSAT/SocialCom.2011.102) · 2011 · Category: A3

Community definition: Independant (PP). Dynamicity: Snapshots.

Code: ?

The approach proposed in this article identifies evolutive chains of communities.   
 Given a time-evolving graph, community detection on each snapshot is executed using a chosen static algorithm (including overlapping ones).   
 Any set intersection based measure can be used to match communities between snapshots, creating a link between them.   
 The authors propose a strategy to find the best chains of evolution for each community: they define chain strength as the strength of its weakest link.   
 As a result, all the maximal valid chains are constructed for the identified communities.   
 A valid chain is considered maximal if it is not a proper subchain of some other valid chain.

### Morini-2017

[Article](https://hal.inria.fr/hal-01558219) · 2017 · Category: A3

Community definition: Independant (PP). Dynamicity: Snapshots.

Code: ?

In this article, the authors start by computing aggregated network snapshots from timestamped observations (SN or TN) using sliding windows.   
Communities are detected using a static CD algorithm on each of these windows independently. Then, the similarity between pair of communities is computed between communities at \(t\) and communities at \(t-2\), \(t-1\), \(t+1\), \(t+2\).   
This information is used to *smooth out* the evolution of communities: if a community \(c\_{t-n}\) in a previous snapshot has a high similarity with \(c\_{t+n}\) in a later one, but is matched with lower similarity to two communities \(c1\_{t}\) and \(c2\_{t}\) at \(t\), then these two communities are merged and the resulting community is identified to \(c\_{t-n}\) and \(c\_{t+n}\). The same mechanism is used to smooth out artificial merges.

### Miller-2009

[Article](https://e-reports-ext.llnl.gov/pdf/457510.pdf) · 2009 · Category: B1

Community definition: Latend Dirichlet Allocation. Dynamicity: Snapshots.

Code: ?

The authors adapt a dynamic extension of Latent Dirichlet Allocation to the extraction of dynamic communities. They design cDTM-G the Continuous time Dynamic Topic Model for Graphs.  
 In this work, observations of the time evolving graph (snapshots) correspond to *corpora* at different points in time: each source-node at each time step corresponds to a document at the same time step, and the links among the nodes connect document's words.   
Exploiting such modeling strategy, dynamic groups/communities capture time evolving topics.   
The authors sequentially run LDA-G (henderson 2009) on each time step initializing the topics for the current time step with the ones learned in the previous time step.

### Aynaud-2010

[Article](https://hal.archives-ouvertes.fr/inria-00492058) · 2010 · Category: B1

Community definition: Modularity. Dynamicity: Snapshots.

Code: ?

This method is based on the Louvain algorithm.   
In the original, static version, the Louvain algorithm is initialized with each node in its community.   
 A greedy, multi-step heuristic is used to move nodes to optimize the partition's modularity.   
 To limit instability, the authors propose to initialize the Louvain algorithm at \(t\) by communities found at \(t-1\).   
A parameter \(x \in [0-1]\) can be tuned to specify a random fraction of nodes that will start in a singleton community, to avoid staying in a local minimum (community drift).

### Gorke-2010

[Article](https://doi.org/10.1007/978-3-642-13193-6_37) · 2010 · Category: B1

Community definition: Modularity. Dynamicity: TN-Interval Graph.

Code: ?

This method efficiently maintains a modularity-based clustering of a graph for which dynamic changes arrive as a stream. The authors design dynamic generalizations of two modularity maximization algorithms, Clauset-2004 and the Louvain algorithm (Blondel-2008).   
The problem is cast as an ILP (Integer Linear Programming).   
 Intuitively, the process at \(t\) is initialized by communities found at \(t-1\), adding a backtracking strategy to extend the search space.

### Bansal-2011

[Article](https://doi.org/10.1007/978-3-642-25501-4_20) · 2011 · Category: B1

Community definition: Modularity. Dynamicity: TN-Interval Graph.

Code: ?

The authors introduce a dynamic community detection algorithm for real-time online changes, which involves the addition or deletion of edges in the network.   
 The algorithm, based on the greedy agglomerative technique of the CNM algorithm (clauset-2004), follows a hierarchical clustering approach, where two communities are merged at each step to optimize the increase in the modularity of the network.   
The proposed improvement for the dynamic case consists in starting from the dendrogram of the previous step cutted just before the first merge of a node involved in the network modifications.   
 It assumes that the small change in network size and density between snapshots does not dramatically impact modularity for non-impacted nodes, and therefore that the beginning of the dendrogram is not impacted.

### Shang-2012

[Article](https://arxiv.org/abs/1407.2683) · 2012 · Category: B1

Community definition: Modularity. Dynamicity: TN-Interval Graph.

Code: ?

This method searches for evolving communities of maximal modularity.   
The Louvain algorithm (Blondel-2008) is used to find communities in the first snapshot.   
 Custom rules are then applied to each modification of the network to update the communities while keeping the modularity as high as possible.   
 The procedure designed to update the communities depends on the type of modification of the network, which can concern an inner community edge, across community edge, a half-new edge (if one of the involved nodes is new) or a new edge (if both extremities are new nodes).

### Alvari-2014

[Article](https://doi.org/10.1109/ASONAM.2014.6921567) · 2014 · Category: B1

Community definition: Ad hoc. Dynamicity: Snapshots.

Code: ?

The authors introduce a game-theoretic approach for community detection in dynamic social networks called D-GT: in this context, each node is treated as a rational agent who periodically chooses from a set of predefined actions to maximize its utility function. The community structure of a snapshot emerges after the game reaches Nash equilibrium: the partitions and agent information are then transferred to the next snapshot.   
 D-GT attempts to simulate the decision-making process of the individuals creating communities, rather than focusing on statistical correlations between labels of neighboring nodes.

### Zhou-2007

[Article](https://doi.org/10.1109/ICDM.2007.56) · 2007 · Category: B2

Community definition: Normalized cut. Dynamicity: Snapshots.

Code: ?

The authors seek communities in bipartite graphs.   
Temporal communities are discovered by threading the partitioning of graphs in different periods, using a constrained partitioning algorithm.   
 Communities for a given snapshot are discovered by optimizing the *Normalized cut*.   
The discovery of community structure at time \(t\) seeks to minimize the (potentially weighted) sum of distances between the current and \(n\) previous community membership, \(n\) being a parameter of the algorithm.

### Tang-2008

[Article](https://doi.org/10.1145/1401890.1401972) · 2008 · Category: B2

Community definition: Stochastic Block Model. Dynamicity: Snapshots.

Code: ?

This approach allows finding the evolution of communities in multi-mode networks.   
To find communities at time \(t\), the authors propose to use a spectral-based algorithm that minimize a cost function defined as the sum of two parts, \(F\_1\) and \(\Omega\).   
 \(F\_1\) corresponds to the reconstruction error of a model similar to block modeling but adapted to multi-mode networks. \(\Omega\) is a regulation term that states the difference between the current clustering and the previous one.   
 Weights allow balancing the relative importance of these two factors.

### Yang-2009

[Article](https://doi.org/10.1137/1.9781611972795.85) · 2009 · Category: B2,C3

Community definition: Stochastic Block Model. Dynamicity: Snapshots.

Code: [By authors](https://homepage.cs.uiowa.edu/~tyng/publications.html)

In this article (and Yang-2010}, the authors propose to use a Dynamic Stochastic Block Model.   
 As in a typical static SBM, nodes belong to clusters, and an interaction probability $eta\_{ql}$ is assigned to each pair of clusters \((q,l)\).  
 The dynamic aspect is handled by a transition matrix, that determines the probability for nodes belonging to a cluster to move to each other cluster at each step.   
The optimal parameters of this model are searched for using a custom Expectation-Maximization (EM) algorithm.   
 The \(\beta\_{ql}\) are constant for the same community for all time steps.  

 Two versions of the framework are discussed:

* **online learning** which updates the probabilistic model iteratively (in this case, the method is a Temporal Trade-Off CD, similar to FacetNet (Lin-2009);
* **offline learning** which learns the probabilistic model with network data obtained at all time steps (in this case, the method is a Cross-Time CD).

Several variations with a similar approach have been proposed by different authors, most notably in Ishiguro-2010, Herlau-2013, Xu-2014d.

### Folino-2010

[Article](https://doi.org/10.1145/1830483.1830580) · 2010 · Category: B2

Community definition: Modularity, Independant. Dynamicity: Snapshots.

Code: ?

This method, also discussed in Folino-2014 adopt a genetic algorithm to optimize a multi-objective quality function.   
 One objective is to maximize the quality of communities in the current snapshot (the modularity is used in the article, but other metrics such as conductance are proposed).   
 The other objective regards the maximization of the NMI between the communities of the previous step and of the current one to ensure a smooth evolution.

### Lin-2009

[Article](https://doi.org/10.1145/1367497.1367590) · 2009 · Category: B2

Community definition: Stochastic Block Model. Dynamicity: Snapshots.

Code: ?

In this method (see also Lin-2008), called FacetNet, the authors propose to find communities at \(t\). To minimize the reconstruction error, a cost error defined as \(cost = \alpha C\_1 + (1-\alpha) C\_2\) is defined -- with \(C\_1\) corresponding to the reconstruction error of a mixture model at $t$, and $C\_2$ corresponding to the KL-divergence between clustering at \(t\) and clustering at \(t-1\).  
 The authors then propose a custom algorithm to optimize both parts of the cost function.   
 This method is similar to Yang-2009.

### Sun-2010

[Article](https://doi.org/10.1145/1830252.1830270) · 2010 · Category: B2

Community definition: Latent Dirichlet Allocation. Dynamicity: Snapshots.

Code: ?

This method (and its variant (Sun-2014co) proposes to find multi-typed communities in dynamic heterogeneous networks.   
 A Dirichlet Process Mixture Model-based generative model is used to model the community generations.   
 A Gibbs sampling-based inference algorithm is provided to infer the model.   
 At each time step, the communities found are a trade-off between the best solution at \(t\) and a smooth evolution compared to the solution at \(t-1\).

### Gong-2012

[Article](https://doi.org/10.1007/s11390-012-1235-y) · 2012 · Category: B2

Community definition: Modularity. Dynamicity: Snapshots.

Code: ?

In this article, the detection of community structure with temporal smoothness is formulated as a multi-objective optimization problem.   
 As in (Folino-2010) the maximization is performed on modularity and NMI.

### Kawadia-2012

[Article](http://doi.org/doi:10.1038/srep00794) · 2012 · Category: B2

Community definition: Modularity. Dynamicity: Snapshots.

Code: ?

In this article a new measure of partition distance is introduced.  
 **Estrangement** captures the inertia of inter-node relationships which, when incorporated into the measurement of partition quality, facilitates the detection of temporal communities.  
 Upon such measure is built the **estrangement confinement method**, which postulates that neighboring nodes in a community prefer to continue to share community affiliation as the network evolves.  
 The authors show that temporal communities can be found by estrangement constrained modularity maximization, a problem they solve using Lagrange duality.  
 Estrangement can be decomposed into local single node terms, thus enabling an efficient solution of the Lagrange dual problem through agglomerative greedy search methods.

### Crane-2015

[Article](https://arxiv.org/abs/1509.09254) · 2015 · Category: B2

Community definition: Stochastic Block Model. Dynamicity: Snapshots.

Code: ?

In this article is introduced a hidden Markov model for inferring community structures that vary over time according to the cut-and-paste dynamics from Crane-2014.   
The model takes advantage of temporal smoothness to reduce short-term irregularities in community extraction.   
 The partition obtained is without overlap, and the network population is fixed in advance (no node appearance/vanishing).

### Gorke-2013

[Article](https://doi.org/10.1145/2444016.2444021) · 2013 · Category: B2

Community definition: Modularity. Dynamicity: TN-Interval Graph.

Code: ?

In this article is proposed an algorithm to efficiently maintain a modularity-based clustering of a graph for which dynamic changes arrive as a stream, similar to Gorke-2012.   
 Differently from such work, here the authors introduce an explicit trade-off between modularity maximization and similarity to the previous solution, measured by the Rand index.   
 As in other methods, a parameter \(\alpha\) allows to tune the importance of both components of this quality function.

### Falkowski-2008

[Article](http://aisel.aisnet.org/amcis2008/29) · 2008 · Category: B3

Community definition: Ad hoc. Dynamicity: TN-Interval Graph.

Code: ?

DENGRAPH is an adaptation of the data clustering technique DBSCAN Ester-1996 for graphs.   
 A function of proximity ranging in [0,1] is defined to represent the distance between each pair of vertices.   
 A vertex \(v\) is said to be density-reachable from a core vertex \{c\) if and only if the proximity between \(v\) and \(c\) is above a parameter \(\omega\).  
 A core vertex is defined as a vertex that has more than \(\eta\) density-reachable vertices.  
 Communities are defined by the union of core vertices that are density-reachable from each other.   
 A simple procedure is defined to update the communities following each addition or removal of an edge.

### Nguyen-2011

[Article](https://doi.org/10.1145/2030613.2030624) · 2011 · Category: B3

Community definition: Ad hoc static. Dynamicity: TN-Interval Graph.

Code: ?

AFOCS (Adaptative FOCS) uses the FOCS algorithm to find initial communities.   
 Communities found by FOCS are dense subgraphs, that can have strong overlaps.   
 Starting from such topologies, a local procedure is applied to update the communities at each modification of the network (e.g., addition or removal of a node or an edge).  
 The strategy, proposed to cope with local network modifications, respects the properties of communities as they are defined by the FOCS algorithm.

### Cazabet-2010

[Article](https://doi.org/10.1109/SocialCom.2010.51) · 2010 · Category: B3

Community definition: Ad hoc. Dynamicity: TN-Interval Graph.

Code: ?

In this article is introduced iLCD, an incremental approach able to identify and track dynamic communities of high cohesion.   
Two measures are defined to qualify the cohesion of communities:

* EMSN: the Estimation of the mean number of second neighbors in the community;
* EMRSN: the Estimation of the mean number of robust second neighbors (second neighbors that can be accessed by at least 2 different paths).

Given a new edge, the affected nodes can join an existing community if an edge appeared with a node in this community.   
 The condition is that the number of its second neighbors in the community is greater than the value of EMSN of the community, and respectively for EMRSN.   
 iLCD has two parameters \(k\) and \(t\).  
 The former regulates the rising of new communities (new communities are created if a new clique of size $k$ appears outside of existing ones), while the latter the merge of existing ones (communities can be merged if their similarity becomes greater than a threshold \(t\).

### Nguyen-2011

[Article](https://doi.org/10.1109/INFCOM.2011.5935045) · 2011 · Category: B3

Community definition: Ad hoc. Dynamicity: TN-Interval Graph.

Code: ?

In this article, the Quick Community Adaptation (QCA) algorithm is introduced.   
 QCA is a modularity-based method for identifying and tracking community structure of dynamic online social networks.   
 The described approach efficiently updates network communities, through a series of changes, by only using the structures identified from previous network snapshots.   
 Moreover, it traces the evolution of community structure over time.   
 QCA first requires an initial community structure, which acts as a **basic structure**, to process network updates (node/edge addition/removal).

### Cazabet-2011

[Article](https://doi.org/10.1109/WI-IAT.2011.50) · 2011 · Category: B3

Community definition: Ad hoc. Dynamicity: TN-Interval Graph.

Code: [By authors](https://cazabetremy.fr/?page=resources/ilcd)

In this article, the authors propose to use a multi-agent system to handle the evolution of communities.   
 The network is considered as an environment, and communities are agents in this environment.   
 When what they perceive of their local environment change (edge/node addition/removal), community agents take decisions to add/lose nodes or merge with another community, based on a set of rules.   
 These rules are based on three introduced measures, *representativeness*, *seclusion* and *potential belonging*.

### Agarwal-2012

[Article](https://doi.org/10.14778/2336664.2336671) · 2012 · Category: B3

Community definition: Ad hoc. Dynamicity: TN-Interval Graph.

Code: ?

In this article the authors addressed the problem of discovering events in a microblog stream.   
 To this extent, they mapped the problem of finding events to that of finding clusters in a graph.   
 The authors describe aMQCs: bi-connected clusters, satisfying **short-cycle property** that allow them to find and maintain the clusters locally without affecting their quality.   
 Network dynamics are handled through a rule-based approach for addition/deletion of nodes/edges.

### Duan-2012

[Article](https://doi.org/10.1007/s10462-011-9250-x) · 2012 · Category: B3

Community definition: Clique based. Dynamicity: TN-Interval Graph.

Code: ?

In this article social networks' dynamics are modeled as a **change stream**.  
 Based on this model, a local DFS forest updating algorithm is proposed for incremental 2-clique clustering, and it is generalized to incremental k-clique clustering.   
 The incremental strategies are designed to guarantee the accuracy of the clustering result with respect to any kind of changes (i.e., edge addition/deletion).   
 Moreover, the authors shown how the local DFS forest updating algorithm produces not only the updated connected components of a graph but also the updated DFS forest, which can be applied to other issues, such as finding a simple loop through a node.

### Gorke-2012

[Article](https://doi.org/10.1145/2444016.2444021) · 2012 · Category: B3

Community definition: Ad hoc. Dynamicity: TN-Interval Graph.

Code: ?

In this article the authors show that the structure of **minimum-s-t-cuts** in a graph allow for an efficient dynamic update of **minimum-cut trees**.   
 The authors proposed an algorithm that efficiently updates specific parts of such a tree and dynamically maintains a graph clustering based on minimum-cut trees under arbitrary atomic changes.   
 The main feature of the graph clustering computed by this method is that it is guaranteed to yield a certain **expansion** -- a bottleneck measure -- within and between clusters, tunable by an input parameter \(\alpha\).   
 The algorithm ensures that its community updates handle temporal smoothness, i.e., changes to the clusterings are kept at a minimum, whenever possible.

### Ma-2013

[Article](https://doi.org/10.1145/2501025.2501026) · 2013 · Category: B3

Community definition: Clique based. Dynamicity: TN-Interval Graph.

Code: ?

The CUT algorithm tracks community-seeds to update community structures instead of recalculating them from scratch as time goes by.   
 The process is decomposed into two steps:

* First snapshot: identify community seeds (collection of 3-cliques);
* Successive snapshots: (i) track community seeds and update them if changes occur, (ii) expand community seeds to complete communities.

To easily track and update community seeds, CUT builds up a Clique Adjacent Bipartite graph (CAB).   
 Custom policies are then introduced to handle node/edge join/removal and seed community expansion.

### Xie-2013

[Article](https://doi.org/10.1145/2489247.2489249) · 2013 · Category: B3

Community definition: Label propagation. Dynamicity: TN-Interval Graph.

Code: ?

In this article the LabelRankT algorithm is introduced.   
 It is an extension of LabelRank Xie-2013, an online distributed algorithm for the detection of communities in large-scale dynamic networks through stabilized label propagation.   
 LabelRankT takes advantage of the partitions obtained in previous snapshots for inferring the dynamics in the current one.

### Lee-2014

[Article](https://doi.org/10.1109/ICDE.2014.6816635) · 2014 · Category: B3

Community definition: Ad hoc. Dynamicity: TN-Interval Graph.

Code: ?

This method aims at monitoring the evolution of a graph applying a fading time window.   
 The proposed approach maintains a skeletal graph that summarizes the information in the dynamic network.   
 Communities are defined as the connected components of such this skeletal graph.   
 Communities on the original graphs are built by expanding the ones found on the skeletal graph.

### Zakrzewska-2015

[Article](https://doi.org/10.1145/2808797.2809375) · 2015 · Category: B3

Community definition: Ad hoc. Dynamicity: TN-Interval Graph.

Code: ?

In this article, the authors propose an algorithm for dynamic greedy seed set expansion, which incrementally updates the traced community as the underlying graph changes.   
 The algorithm incrementally updates a local community starting from an initial static network partition (performed trough a classic set seed expansion method).   
 For each update, the algorithm modifies the sequence of community members to ensure that corresponding fitness scores are increasing. 

### Rossetti-2017

[Article](https://doi.org/10.1007/s10994-016-5582-8) · 2017 · Category: B3

Community definition: Ad hoc. Dynamicity: TN-Interval Graph.

Code: [By authors](https://goo.gl/zFRfCU)

In this article, the authors introduce TILES, an online algorithm that dynamically tracks communities in an edge stream graph following local topology perturbations.   
 Exploiting local patterns and constrained label propagation, the proposed algorithm reduces the computation overhead.   
 Communities are defined as two-level entities:

* **Core node**: a core node is defined as a node involved in at least a triangle with other core nodes of the same community;
* **Community Periphery**: the set of all nodes at one-hop from the community core.   
   Event detection is also performed at runtime (Birth, Split, Merge, Death, Expansion, Contraction).

### Kim-2009

[Article](https://doi.org/10.14778/1687627.1687698) · 2009 · Category: B4

Community definition: Ad hoc. Dynamicity: Snapshots.

Code: ?

In this article, the authors propose a particle-and-density based method, for efficiently discovering a variable number of communities in dynamic networks.   
 The method models a dynamic network as a collection of particles called **nano-communities**, and model communities as a densely connected subset of such particles.   
 Each particle, to ensure the identification of dense substructures, contains a small amount of information about the evolution of neighborhoods and/or communities and their combination, both locally and across adjacent network snapshots (which are connected as t-partite graphs).   
 To allow flexible and efficient temporal smoothing, a cost embedding technique -- independent on both the similarity measure and the clustering algorithm used -- is proposed.   
 In this work is also proposed a mapping method based on information theory.

### Guo-2014

[Article](https://doi.org/10.1016/j.physa.2014.07.004) · 2014 · Category: B4

Community definition: Modularity. Dynamicity: Snapshots.

Code: ?

This method finds communities in each dynamic weighted network snapshot using modularity optimization.   
 For each new snapshot, an input matrix -- which represents a tradeoff between the adjacency matrix of the current step and the adjacency matrix of the previous step -- is computed.   
 Then, a custom modularity optimization community detection algorithm is applied.

### Xu-2013

[Article](https://doi.org/10.1109/SocialCom.2013.30) · 2013 · Category: B4

Community definition: Ad hoc. Dynamicity: Snapshots.

Code: ?

In this method (variant in Xu-2015, the **Cumulative Stable Contact** (CSC) measure is proposed to analyze the relationship among nodes: upon such measure, the authors build an algorithm that tracks and updates stable communities in mobile social networks.   
 The key definition provided in this work regards:

* **Cumulative Stable Contact**: There is a CSC between two nodes iff their history contact duration is higher than a threshold.
* **Community Core Set**: The community core at time \(t\) is a partition of the given network built upon the useful links rather than on all interactions.

The network dynamic process is divided into snapshots. Nodes and their connections can be added or removed at each snapshot, and historical contacts are considered to detect and update **Community Core Set**.  
 Community cores are tracked incrementally allowing to recognize evolving community structures.

### Sun-2007

[Article](https://doi.org/10.1145/1281192.1281266) · 2007 · Category: C1

Community definition: Information Compression (MDL). Dynamicity: Snapshots.

Code: ?

GraphScope is an algorithm designed to find communities in dynamic bipartite graphs. Based on the Minimum Description Length (MDL) principle, it aims is to optimize graph storage while performing community analysis.   
 Starting from an SN, it reorganizes snapshots into segments.   
 Given a new incoming snapshot it is combined with the current segment if there is a storage benefit, otherwise, the current segment is closed, and a new one is started with the new snapshot.   
 The detection of communities sources and destination for each segment is done using MDL.

### Duan-2009

[Article](https://doi.org/10.1145/1651274.1651278) · 2009 · Category: C1

Community definition: Modularity. Dynamicity: Snapshots.

Code: ?

In this article the authors introduce a method called Stream-Group designed to identify communities on dynamic directed weighted graphs (DDWG).   
 Stream-Group relies on a two-step approach to discover the community structure in each time-slice:

* The first step constructs compact communities according to each node's single compactness -- a measure which indicates the degree a node belongs to a community in terms of the graph's relevance matrix.
* In the second step, compact communities are merged along the direction of maximum increase of the modularity.

A measure of the similarity between partitions is then used to determine whether a change-point appears along the time axis and an incremental algorithm is designed to update the partition of a graph segment when adding a new arriving graph into the graph segment.   
 In detail, when a new time-slice arrives,

* the community structure of the arriving graph is computed;
* the similarity between the partition of the new arriving graph and that of the previous graph segment is evaluated;
* change-point detection is applied: if the time-slice \(t\) is not a change point, then
* the partition of the graph is updated; otherwise a new one is created.

### Aynaud-2011

[Article](https://hal.archives-ouvertes.fr/hal-01286941) · 2011 · Category: C1

Community definition: Modularity. Dynamicity: Snapshots.

Code: ?

In this article, the authors propose a definition of average modularity \(Q\_{avg}\) over a set of snapshots (called time window), defined as a weighted average of modularity for each snapshot, with weights defined a priori -- for instance to reflect heterogeneous durations.   
 Optimizing average modularity yield a constant partition relevant overall considered snapshots.  
 This approach does not contemplate community operations.   

 The authors propose two methods to optimize this modularity:

* **Sum-method**: Given an evolving graph \(G = \{G\_1,G\_2, \dots,G\_n\}\) and a time window \(T \subseteq \{1, \dots,n\}\), a cumulative weighted graph is built, called the sum graph, which is the union of all the snapshots in \(T\). Each edge of the sum graph is weighted by the total time during which this edge exists in \(T\).  
   Since the sum graph is a static weighted graph, the authors apply the Louvain method on it. This method is not strictly equivalent to optimizing \(Q\_{avg}\) but allows a fast approximation.
* **Average-Method**: two elements of the Louvain method are changed to optimize the average modularity during a time window \(T\): (1) the computation of the quality gain in the first phase and (2) how to build the network between communities in the second one.
  1. average modularity gain is defined as the average of the static gains for each snapshot of \(T\);
  2. given a partition of the node set, the same transformation of Louvain is applied to every snapshot of \(T\) independently (with different weights for each snapshot) to obtain a new evolving network between the communities of the partition.

The authors finally propose a method using sliding windows to segment the evolution of the network in stable periods, potentially hierarchically organized.

### Gauvin-2014

[Article](https://doi.org/10.1371/journal.pone.0086028) · 2014 · Category: C2

Community definition: Non-negative Matrix Factorization (NMF). Dynamicity: Snapshots.

Code: ?

In this article, the authors propose to use a Non-Negative tensor factorization approach.   
 First, all adjacency matrices, each corresponding to a network snapshot, are stacked together in a 3-way tensor (a 3-dimensional matrix with a dimension corresponding to time).   
 A custom non-negative factorization method is applied, with the number of desired communities as input, that yields two matrices: one corresponds to the membership weight of nodes to components, and the other to the activity level of components for each time corresponding to a snapshot.   
 It can be noted that each node can have a non-zero membership to several (often all) communities.   
 A post-process step is introduced to discard memberships below a given threshold and, thus, simplify the results.

### Matias-2016

[Article](http://doi.org/10.1111/rssb.12200) · 2016 · Category: C2

Community definition: Stochastic Block Model. Dynamicity: TN-Instantaneous / Snapshots.

Code: ?

In thsi article, the authors propose to use a Poisson Process Stochastic Block Model (PPSBM) to find clusters in temporal networks.   
 As in a static SBM, nodes belong to groups, and each pair of groups is characterized by unique connection characteristics.   
 Unlike static SBM, such connection characteristic is not defined by a single value, but by a function of time \(f\) (intensity of conditional inhomogeneous Poisson process) representing the probability of observing interactions at each point in time.   
 The authors propose an adapted Expectation-Maximization (EM) to find both the belonging of nodes and \(f\) that better fit the observed network.   
 It is to be noted that nodes do not change their affiliation using this approach, but instead, it is the clusters' properties that evolve along time. 

### Matias-2015

[Article](https://arxiv.org/abs/1512.07075) · 2015 · Category: C3

Community definition: Stochastic Block Model. Dynamicity: Snapshots.

Code: ?

In this article, the authors propose to use a Dynamic Stochastic Block Model, similar to Yang-2009.   
 As in a typical static SBM, nodes belong to clusters, and an interaction probability \(\beta\_{ql}\) is assigned to each pair of clusters \((q,l)\).  
 The dynamic aspect is handled as an aperiodic stationary Markov chain, defined as a transition matrix \(\pi\), characterizing the probability of a node belonging to a given cluster \(a\) at time \(t\) to belong to each one of the other clusters at time \(t+1\).   
 The optimal parameters of this model are searched for using a custom Expectation-Maximization (EM) algorithm.   
 The authors note that it is not possible to allow the variation of \(\beta\) and node memberships parameters at each step simultaneously, and therefore impose a single value for each intra-group connection parameter \(\beta\_{qq}\) along the whole evolution -- thus, searching for clusters with stable intra-groups interaction probabilities.   
 Finally, authors introduce a method for automatically finding the best number of clusters using Integrated Classification Likelihood (ICL), and an initialization procedure allowing to converge to better local maximum using an adapted k-means algorithm.

### Ghasemian-2016

[Article](https://doi.org/10.1103/PhysRevX.6.031005) · 2016 · Category: C3

Community definition: Stochastic Block Model. Dynamicity: Snapshots.

Code: ?

In this article, the authors use a Dynamic Stochastic Block Model similar to Yang-2009, and propose scalable algorithms to optimize the parameters of the model based on belief propagation and spectral clustering. They also study the detectability threshold of the community structure as a function of the rate of change and the strength of communities.

### Jdidia-2007

[Article](https://doi.org/10.1109/ICDIM.2007.4444313) · 2007 · Category: C4

Community definition: Ad hoc static, Independent. Dynamicity: Snapshots.

Code: ?

In this article, the authors propose to add edges between nodes in different snapshots, i.e. edges linking nodes at \(t\) and \(t+1\).   
 Two types of these edges can be added:

* *identity edges* between the same node, if present at \(t\) and \(t+1\), and
* *transversal edges* between different nodes in different snapshots.

To do so, the following relation must hold: there is an edge between \(u \in t\) and \(v \in t+1\) if \(\exists w\) such that \((u,w) \in t\) and \((v,w) \in t+1\).  
 A static CD algorithm, Walktrap, is consequently applied to this transversal network to obtain dynamic communities.

### Mucha-2010

[Article](http://doi.org/10.1126/science.1184819) · 2010 · Category: C4

Community definition: Modularity. Dynamicity: Snapshots.

Code: [By authors](http://netwiki.amath.unc.edu/GenLouvain/GenLouvain)

The method introduced in this article has been designed for any multi-sliced network, including evolving networks.   
 The main contribution lies in a multislice generalization of modularity that exploits laplacian dynamics.   
 This method is equivalent to adding links between same nodes in different slices, and then run a community detection on the resulting graph.   
 In the article, edges are added only between same nodes in adjacent slices. The weight of these edges is a parameter of the method.   
 The authors underline that the resolution of the modularity can vary from slice to slice. In Bassett-2013, variations of the same method using different null models are explored.

### Viard-2015

[Article](https://doi.org/10.1016/j.tcs.2015.09.030) · 2015 · Category: C4

Community definition: Clique based. Dynamicity: TN-Instantaneous.

Code: 

In this article, the notion of clique is generalized to link streams.   
 A \(\Delta\)-clique is a set of nodes and a time interval such that all nodes in this set are pairwise connected at least once during any sub-interval of duration \(\Delta\) of the interval.  
 The paper presents an algorithm able to compute all maximal (in terms of nodes or time interval) \(\Delta\)-cliques in a given link stream, for a given \(\Delta\).   
 A solution able to reduce the computational complexity has been proposed in Himmel-2016.

