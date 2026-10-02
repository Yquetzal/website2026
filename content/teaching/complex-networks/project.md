# Complex Networks — Project

**Pierre Borgnat, Rémy Cazabet & Alexandre Nicolas**

## In short

1. **Identify a question for which a network perspective could be insightful.**
   Ideally, favour open or unsettled questions, possibly inspired by current events. Some ideas are given below, but the list is not exhaustive.

2. **Create a network related to this question and analyse it** using concepts and methods introduced in the lectures.

3. **Produce a concise report presenting your investigation and findings**, and prepare an oral presentation.

> There is no need to fully settle the question. We only ask that you honestly present your progress towards an answer and explain what the network perspective contributes to the problem.

---

## Guidelines

### Creating your own network

Once you have identified the question you want to address, collect relevant data and use them to create a network related to this question.

For this project, you need to create your own network(s). There are several possible approaches:

- **Collect data from external sources**, either:

  - online, for instance using an API or web scraping, or
  - by contacting someone who can provide data that are not openly available.

  > Using an LLM to help collect or structure data is acceptable, provided that you clearly explain what you did and verify the consistency of the output.

- **Start from an existing dataset that is not already in graph format.**
  For example:

  - taxi trips with source and destination locations → transport network;
  - users and music preferences → music similarity network;
  - [MovieLens](https://grouplens.org/datasets/movielens/latest/) → movie or user similarity network;
  - adjacent amino acids in proteins → biological network.

  Extract a list of edges from the original data and create the network, for example using `networkx`.

- **Simplify or enrich an existing network.**
  For geographic data, GIS tools such as [QGIS](https://qgis.org/) may be useful.

Feel free to ask for help and advice during the project.

Your report should clearly introduce the network you created:

- What do the nodes represent?
- What do the edges represent?
- What choices or assumptions did you make when constructing the network?
- How might these choices affect your results?

### Final report

The report should contain **at most 2,000 words** and **at most 12 pages**, including figures.

It may be provided either as:

- a **PDF document**, or
- an **interactive HTML page**, provided that its printed version would fit approximately within 12 pages.

The objective is to produce a **clear, concise, professional-looking and data-driven investigation that is pleasant to read**.

In particular, **quality is more important than quantity**. Long methodological digressions, generic definitions of standard concepts, or extensive background material should be avoided unless they are directly useful for understanding your analysis.

This is especially important when using generative AI: producing additional text is easy, but unnecessary material makes the report harder and more time-consuming to read. Focus on the research question, the data, the analysis, the results, and their interpretation.

A useful rule is:

> **Every paragraph, figure and table should contribute directly to the investigation.**

### Code and technical documentation

In addition to the final report, you must provide:

1. **all the code used to produce the analyses, results and figures included in the report**;
2. a **short technical report** describing aspects that do not need to appear in the main report, such as:
   - data collection and preparation;
   - implementation details;
   - parameter choices;
   - algorithms tested;
   - technical difficulties or limitations;
   - other relevant methodological decisions.

The code should be reasonably organised and reproducible.

The purpose of separating the main report from the technical material is to keep the report focused on the scientific question and the results, rather than filling it with implementation details.

### Visualization

Remember that **a good figure can replace a long explanation**.

Network visualizations should be used when they help answer the research question, rather than simply to show that a network has been constructed.

If you create visualizations using Gephi, remember to also submit the original image files.

### What question should I address?

There is no strong constraint on the question that you will address. We simply request that:

- it might be worth addressing from a network perspective. If it turns out that network analysis does not help, this is perfectly acceptable, as long as you explain your approach and how you arrived at this conclusion;
- the constructed network and/or its analysis are not already widely available.

### Final presentation

Additionnally to the report, you will also make a presentation of your project. Details to come.

---

## Indicative and non-exhaustive list of possible questions

The following examples are intended as inspiration. You are encouraged to propose your own question.

### Pipeline networks

In September **2022**, gas leaks appeared on the Nord Stream 1 and 2 pipelines, raising suspicions of possible sabotage.

Possible questions include:

- Which countries were directly or indirectly affected?
- How central were the affected pipeline segments in the European gas pipeline network?
- How does their importance change when considering past, present, or hypothetical future configurations of the network?

Possible resources:

- [Gas Pipelines in Europe — Memgraph](https://memgraph.com/blog/gas-pipelines-in-europe)
- [Gas Pipelines — Le Monde diplomatique](https://mondediplo.com/maps/gas-pipelines)

### Submarine communication cables

[Submarine cables](https://www.submarinecablemap.com/) form the backbone of the intercontinental telecommunications network, but they are regularly damaged by human activity, either accidentally or deliberately.

Possible questions include:

- How vulnerable is the network to the failure of individual cables?
- Which cables are structurally the most critical?
- Can the location and pattern of cable faults help assess whether malicious activity is statistically plausible?

### The Great Fear

Zapperi et al. ([*Nature*, 2025](https://www.nature.com/articles/s41586-025-09392-2)) studied the propagation of the **Great Fear of 1789 in France** using an epidemiological model. The Python scripts used in the study are available as supplementary material.

Possible questions include:

- How can we characterise the network of locations through which the Great Fear spread?
- Were some locations particularly central to its propagation?
- Conversely, which locations appear to have played only a minor role?

### Sea lanes / marine traffic routes

In the aftermath of the Israeli-American strikes on Iran in 2026, the Strait of Hormuz was partly closed to merchant ships and tankers, affecting the global economy to varying degrees depending on the country.

Construct a network of countries or world regions in which edges represent major sea lanes, possibly focusing on one particular commodity.

Possible questions include:

- Can this network help explain the economic impact of the partial closure of the Strait of Hormuz?
- Which countries or regions are structurally most exposed to disruption in the Strait?
- Are there alternative routes, and how do they change the structure of the network?

Possible resources:

- [MarineTraffic](https://www.marinetraffic.com/)
- [Global Shipping Lanes — Resource Watch](https://resourcewatch.org/data/explore/com012-Global-Shipping-Lanes)

### Forest fires

The French territory was severely affected by megafires during the summer of 2026.

[Land-cover data](https://www.data.gouv.fr/datasets/corine-land-cover-occupation-des-sols-en-france) can be used to construct a graph in which land patches are connected through flammable areas, such as pine forests.

Possible questions include:

- Assuming weather conditions are unknown, which structural properties of this network affect the risk that a fire reaches a given patch?
- Which regions appear particularly vulnerable from a purely structural perspective?
- To what extent does this highly simplified approach reproduce the observed propagation of forest fires in France during summer 2026?

Possible resources:

- [CORINE Land Cover — data.gouv.fr](https://www.data.gouv.fr/datasets/corine-land-cover-occupation-des-sols-en-france)
- [Historical forest-fire maps — feuxdeforet.fr](https://feuxdeforet.fr/cartes/historique/)

### Power grid

On April 28, 2025, a major blackout affected the Spanish and Portuguese power grids.

Possible questions include:

- Can the electricity transmission network help explain the spatial extent of the blackout?
- How can we quantify the degree of interconnection between the Spanish and Portuguese power grids?
- How does this compare with the interconnection between the Spanish and French grids?

Possible resource:

- [ENTSO-E transmission system map](https://www.entsoe.eu/data/map/)

### Adjacent street names

Most streets have names.

Possible questions include:

- What are the most common street names in France?
- Construct a network of street names in which two names are connected when the corresponding streets are adjacent.
- Build such networks for several large French cities.
- Compare their structures and discuss their similarities and differences.

