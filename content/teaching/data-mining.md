
Ceci est la page du cours de Data Mining pour les M2 IA et Data Science, université Lyon 1, pour l'année académique **2025/2026**

-----

### Programme et contenus

**Salles** 

Vous pouvez retrouver le détail des horaires et des salles là : https://adelb.univ-lyon1.fr/
Les cours ont lieu les Lundi et Mardi matin. Se reporter au calendrier détaillé ci-dessous pour les détails. Les chargées de TP seront Maeva Somny & Chloé Conrad

----

Ci-dessous, une vue générale des cours du semestre. Il s'agit d'un programme provisoire qui sera amené à évoluer.
Les contenus seront mis à jour au fur et à mesure.

| Date | Time       | Type        | Teachers | Content |
|-----------|-------------|-------------|------------|------------|
| Lundi 8 Sep   | 11h30-13h00     | CM          | Rémy       | Rappels,Stat/Data ([Slides](https://cazabetremy.fr/Teaching/DSIA/2025/DM-DataIntro.pdf), [Notes](https://cazabetremy.fr/Teaching/DSIA/2025/SupportDataIntro.pdf)) |
| Mardi 9 Sep   | 11h30-13h00     | CM          | Rémy       | Clustering avancé ([Slides](https://cazabetremy.fr/Teaching/data_class/2025/slides/Clustering.pdf),Notes) |
| Lundi 15 Sep  | 8h00-13h00     | TP+CM          | Rémy, Chloe, Maeva       | [TP1](https://cazabetremy.fr/Teaching/data_class/2025/TP/TP_DataDescription.pdf) - [TP2](https://cazabetremy.fr/Teaching/data_class/2025/TP/TP_CLustering.pdf) - Dimensionality Reduction([Slides](https://cazabetremy.fr/Teaching/data_class/2025/slides/Dimensionality%20Reduction.pdf), Notes)|
| Mardi 16 Sep   | 8h00-13h00     | TP+CM+TP          | Rémy, Chloe, Maeva        | Networks 1([Slides](https://cazabetremy.fr/Teaching/data_class/Graphs_centrality.pdf), Notes) - [TP3](https://cazabetremy.fr/Teaching/data_class/2025/TP/TP_dimensionality.pdf), [TP4](https://cazabetremy.fr/Teaching/data_class/TPs/graphsGephi.pdf)) |
| Lundi 6 Octobre   | 8h00-13h00     | Projet+TP+CM          | Rémy, Chloe, Maeva        | Networks 2 ([Slides](https://cazabetremy.fr/Teaching/data_class/Graphs_ML.pdf),[TP](https://cazabetremy.fr/Teaching/data_class/TPs/graphsPython.pdf)) |
| Mardi 7 Octobre   | 8h00-13h00      | Projet+CM+TP          | Rémy, Chloe, Maeva        | Frequent Patterns ([Slides](https://cazabetremy.fr/Teaching/DSIA/frequentPatterns.pdf),[TP](https://cazabetremy.fr/Teaching/data_class/2025/TP/TP_frequent.pdf)) |
| Lundi 13 Octobre   | 8h00-13h00     | Projet+CM+TP          | Rémy, Chloe, Maeva        | Spatial and Temporal ([Slides](https://cazabetremy.fr/Teaching/data_class/2025/slides/Spatiotemporal.pdf),[TP](https://cazabetremy.fr/Teaching/data_class/2025/TP/TP_spatialTemporal.pdf))  |
| Mardi 14 Octobre   | 8h00-13h00      | Projet+CM+TP          | Rémy, Chloe, Maeva        | Explainable AI ([Slides](https://cazabetremy.fr/Teaching/DSIA/2025/XAI.pdf),[TP](https://cazabetremy.fr/Teaching/DSIA/2025/TP_XAI.pdf)) |
| Mardi 4 Novembre   | 9h45-11h45     | EXAMEN          | Rémy, Chloe, Maeva        | Voir détails ci-dessous |

-----
## DATA

### Data Description

* [Caffeine Dataset](https://cazabetremy.fr/Teaching/data_class/Datasets/coffee_effects.csv) (Synthetic)
* [Car Dataset](https://cazabetremy.fr/Teaching/data_class/Datasets/cars_synthetic.csv) (Synthetic)

### Clustering

* [Fruits](https://cazabetremy.fr/Teaching/data_class/Datasets/fruits_all.zip)
* [Car Dataset, CLEAN](https://cazabetremy.fr/Teaching/data_class/Datasets/cars_synth_clean.csv) (Synthetic)

### Dimensionality Reduction, Frequent Patterns
* [Movie User Ratings](https://cazabetremy.fr/Teaching/data_class/Datasets/ratings_clean_names.csv)
  
### Network 1
* <a href="https://cazabetremy.fr/Teaching/data_class/2025/data/GOT.graphml.zip">small network GOT</a>
* <a href="https://cazabetremy.fr/Teaching/data_class/2025/data/airportsAndCoord.graphml.zip">Airport Network</a>

### Spatiotemporal
* <a href="https://cazabetremy.fr/Teaching/data_class/Datasets/US_City_T.csv">US cities T</a>
* <a href="https://cazabetremy.fr/Teaching/data_class/Datasets/US_City_Locations.csv">US cities location</a>
-------
## Évaluation

### Projet
* Pour faire le projet, vous pouvez vous mettre par groupe de 2 ou 3. **Vous devez clairement indiquer qui a travaillé sur quelle partie**. Les notes pourront être individualisées.
* L'objectif du projet est de prendre un jeu de données réel, et de l'analyser en utilisant principalement une de ces parties du cours:
  * Clustering,
  * Dimensionality reduction,
  * Networks
  
  L'objectif est de ne pas simplement appliquer la méthode, mais de creuser comment l'appliquer au mieux: transformations des données, variantes des méthodes, paramètres...
* Vous pouvez compléter l'analyse avec d'autres aspects du cours.
* Il est important de fournir une **analyse** a partir des résultats que vous avez obtenus. Quels paramètres ont le mieux fonctionné, et, à votre avis, pourquoi ? Qu'avez-vous appris sur votre jeu de données? Qu'est-ce que vous n'avez pas réussi à faire marcher, et pourquoi ?
* Le rendu est composé de deux éléments:
  * Le code. Peut être sous forme de notebook, de fichiers .py, ou une combinaison des deux.
  * Un document PDF qui doit viser à être de qualité professionnelle (Étude en entreprise ou article scientifique). 4000 mots maximum. Le rapport doit être très soigné. Il doit **décrire les données**, et **présenter une analyse claire et pertinente**. 
* La note évaluera 1)Le bon usage des méthodes vues en cours, 2) La pertinence des analyses effectuées, 3)La qualité du document (lisibilité, clarté des explications, usage de terminologie précise et adéquate). Le code en lui-même ne sera pas évalué, mais il sera regardé pour s'assurer que le travail a bien été effectué par les étudiants.
* Je donne quelques [conseils](https://cazabetremy.fr/?page=teaching/datasets) pour trouver un dataset</a>.
* Le projet est à rendre pour le <b>Dimanche 2 Novembre, 23:59</b>, en le déposant dans Tomuss, sois sous la forme d'un fichier, sois sous la forme d'une URL vers un dépôt de type GitHub/GitLab.

### Examen final 
Pour l'examen final: Je n'attends pas de vous de savoir par cœur les équations des différentes méthodes, ou de savoir appliquer des méthodes que nous n'avons pas appliqué en TP. J'attends de vous de savoir quelles sont les différentes méthodes que j'ai présenté, et, dans les grandes lignes, leur fonctionnement et leurs différences. Vous aurez le droit aux documents papier durant l'examen. 
* Annale de 2022 avec éléments de correction (https://cazabetremy.fr/Teaching/DSIA/2022/Exam_corr.pdf)
* Annale de 2023 avec éléments de correction (https://cazabetremy.fr/Teaching/DSIA/Exams2023.pdf)

