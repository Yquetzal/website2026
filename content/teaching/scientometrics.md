### IMST - EISO 2025/2026 - Gephi et l'analyse en réseau

![labs](https://cazabetremy.fr/assets/images/labs.png)**Introduction**  
Cette page concerne l'UE 3 - Scientométrie, Bibliométrie : Mesures et représentations de la production scientifique du Master 2 IMST (Information et médiation scientifique et technique), parcours EISO (Epistémologie et Ingénierie de la Science Ouverte).  
Plus particulièrement, elle sert de support à la partie dont je (Rémy Cazabet) suis responsable, portant sur l'analyse en réseau des données scientifiques, ainsi qu'à l'outil d'analyse de réseaux Gephi.

  
**Objectifs**  
L'objectif de ce cours est d'acquérir les compétences suivantes:

1. Savoir comment une base de données bibliographique en accès libre, telle HAL, peut être interrogée en utilisant un language de programmation
2. Savoir passer de données brutes à des données modélisées sous la forme d'un graphe, et les bonnes questions à se poser
3. Connaître les bases du domaine de la science des réseaux (Network Science), permettant de décrire et d'analyser des données représentées sous forme de graphes
4. Savoir utiliser le logiciel libre Gephi pour 1)Calculer des indicateurs d'analyse de réseaux et 2)Produire des visualisations sous forme de réseaux de données de co-citations ou de collaborations.

**Présentations Générale du cours**  
Le cours sera composé de 4 séances, soit 12h d'enseignement. La dernière séance sera dévolue au projet.  
Le cours sera évalué par un projet à effectuer en groupe (voir section correspondante).  

### Programme

Ci-dessous le programme prévisionnel des cours.

**Ce programme est encore provisoire!**.

  

| Créneau | Sujet | Ressources |
| --- | --- | --- |
| Vendredi 19/09 | Introduction, Description de réseaux, centralité, Gephi 1 | [PDF-Description-Centralités](https://cazabetremy.fr/Teaching/IMST/2025/DescriptionsCentralite.pdf)    [Exercices Gephi: Introduction](https://cazabetremy.fr/Teaching/IMST/2023/XPgephi.pdf)  [Formulaire science des réseaux](https://cazabetremy.fr/Teaching/URFIST/CN_BABA.pdf) |
| Vendredi 24/10 | Collection de données depuis HAL - debut projet | [Présentation de HAL](https://cazabetremy.fr/Teaching/IMST/HAL.pdf)  [Requetes API HAL](https://colab.research.google.com/drive/1EQyB2xGay1hojuKbjYetccJWYaZr7v2j)  [Exemple pour démarrer](https://colab.research.google.com/drive/1Ao_0Z5H2a2wzaYnHuKAwZrMsNzGAxqmU)  Pour aller plus loin:  [Introduction à Pandas](https://colab.research.google.com/github/Yquetzal/Teaching_notebooks/blob/main/Pandas_hands_on.ipynb)  [Introduction aux structures de données python](https://colab.research.google.com/github/Yquetzal/Teaching_notebooks/blob/main/pythonDataStructureIntro.ipynb) |
| Vendredi 14/11 | Réseaux: centralité, Communautés, Gephi 2 | [PDF communautés](https://cazabetremy.fr/Teaching/IMST/2025/Modularite.pdf)  [Exercices: créer un réseau Gephi avec Excel](https://cazabetremy.fr/Teaching/IMST/Gephi_fr_3.pdf)  [TP: Figures Interactives en python](https://colab.research.google.com/drive/1TwPTHO3s37WZsk3fNQikyWur6K5D8YrV?usp=sharing) |
| Vendredi 28/11 | Travail sur le projet |  |

  

### Jeux de données de test

Quelques données de réseaux pour pratiquer avec Gephi.  
[Petit réseau Game Of Thrones(.graphml)](https://cazabetremy.fr/Teaching/IMST/GOT.graphml)   
[Aeroports avec pays et position(.graphml)](https://cazabetremy.fr/Teaching/CN2020/airportsAndCoord.graphml)  

Les données de pays GapMinder:
[GapMinder](https://cazabetremy.fr/Teaching/IMST/gapminder_tidy.csv)  

### Outils

Pour ce cours, vous allez avoir besoin de deux choses: Le logiciel Gephi et un notebook pour coder en python (mais vous pouvez travailler en ligne sans rien installer, comme indiqué ci-dessous)

  

## Gephi

Gephi est l'outil le plus pratique pour visualiser des réseaux, et faire des analyses simples sans programmation.

Il peut être téléchargé ici : [Gephi](https://gephi.org).

La dernière version doit normalement s'installer sur tous les ordinateurs (mac, windows, linux) sans souci particulier. Au cours où vous seriez vraiment bloqué, vous pouvez essayer de travailler en ligne avec [Gephi Lite](https://gephi.org/gephi-lite/), une version allégée en ligne.

## Python

Pour la partie requête de bases de données bibliométriques, nous utiliserons python. Il est possible de travailler en ligne avec un outil tel que [Google colab](http://colab.research.google.com). Sinon vous pouvez bien sûr installer python sur votre machine de manière classique, je recommende dans ce cas d'utiliser la distribution appelée Anaconda.
Vous pouvez aussi utiliser l'éditeur de code VScode.  

### Projet

L'évaluation de ma partie de l'UE sera faite sous la forme d'un rendu de projet.

Vous travaillerez par groupes de 2 à 3 étudiants.

L'objectif du projet est de faire votre propre analyse d'un réseau de données issues d'une base de données de citations telle que HAL.  
Le projet sera à rendre sous la forme d'un court document PDF. Ce document devra contenir:

- Les détails des requêtes que vous avez utilisé
- Une interprétation de votre analyse (qu'est-ce que vous avez appris, quelles sont les limites de votre analyse, etc.)
- Au moins une visualisation de qualité de votre réseau
- Au moins un graphique (histogramme, nuage de pts, etc.). Vous pouvez intégrer l'image au rapport ou joindre un fichier intéractif en annexe.

Le document devra être court (3000 mots maximum). Vous pouvez utiliser autant d'images que nécessaire, mais ne mettre que celles qui sont pertinentes, et prendre soin de les rendre lisibles. Un code python devra être fourni en annexe, mais ne sera pas évalué.

L'objectif est de faire un document de qualité professionnelle, qui pourrait être utilisé pour une présentation à un client, ou pour un article scientifique.

 Il est tout à fait autorisé de réutiliser le code python fourni durant le cours, de copier-coller du code depuis internet, de demander de l'aide à chatGPT/copilot et de vous partager du code python. Vous ne serez pas évalué sur la qualité de votre code python.

Vous devez définir un sujet d'analyse unique à votre groupe: cela peut être limité à une zone géographique, un sujet thématique, une période donnée, etc. L'analyse de ces données, leur visualisation, et l'interpréation que vous en ferez sera unique à votre groupe.

  
Date de rendu: **21 Décembre, 23:59**.

Exemples des années précédentes (les consignes peuvent varier d'une année sur l'autre):
[Exemple 1](https://cazabetremy.fr/Teaching/IMST/projetExample/projet2023-1.pdf)
[Exemple 2](https://cazabetremy.fr/Teaching/IMST/projetExample/projet2023-2.pdf)
