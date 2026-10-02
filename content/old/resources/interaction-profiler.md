## Short presentation

Interaction Profiler is a small program that can be used to evaluate the nature of interactions between a set of actors.

In summary, if you have a set of actors (individuals or something else) that interact repeatedly with each other (any kind of interaction: phone calls, emails, scientific citation, colocation... anything you like), you might wonder how these interaction are organized.

  
What we propose is to compute three metrics to characterize these interactions. The value is significative in itself, but comparing with other datasets that you already know is the best way to interprete the obtained values.
The computed values are all between 0 and 1. 0 means that the observations can be explained by random interactions, while 1 means that none of the observations can be due to randomness
These values are:

- Social Structure Impact(SSI): how strong is the influence of the social structure on the interactions between authors, compared with random interactions
- Concentration Impact(CI): how much concentration there is in the interactions, excluding interpersonal friendships (strong if a few actors receive most of interactions)
- Reciprocity Impact(RI): how strong is the reciprocity in interactions between users. All these values can take values between 0 and 1, 0 meaning that obesrvations can be explained by random interactions, 1 meaning that none of the observations can be expplained by random interactions.

## Example values on some networks

| NETWORK | #Nodes | #Edges | I/A | SSI | RI | CI |
| --- | --- | --- | --- | --- | --- | --- |
| NicoNico Douga | 27,514 | 371,450 | 13.5 | 0.36 | 0.023 | 0.37 |
| DBLP | 194,079 | 7,940,131 | 40.9 | 0.45 | 0.11 | 0.16 |
| TwitterRT | 271,402 | 16,917,969 | 62.33 | 0.28 | 0.018 | 0.40 |
| TwitterNOTRT | 262,545 | 17,719,946 | 67.5 | 0.88 | 0.66 | 0.021 |
| ENRON emails | 155 | 9,646 | 62.2 | 0.51 | 0.31 | 0.0001 |

Where I/A is the number of interaction per actor in our dataset.

- NicoNico is the network of references among creators in the NicoNico social network platform
- DBLP is a network of citation in the DBLP database
- TwitterRT is a network of retweets between Twitter users
- TwitterNOTRT is a network of direct communications (mentions) between Twitter users
- ENRON is the network of emails sent between individuals in the ENRON dataset

We can observe, for instance, a clear difference between interpersonal communication activities (ENRON, TwitterNotRT), having a high RI and low CI, compared with interactions corresponding to
the diffusion of information (NND,TwitterRT), which have a low RI and high CI. DBLP is a little different, as discussed in our article on the subject.

## More information

[Code on GitHub](https://github.com/Yquetzal/InteractionProfiler/blob/master/README.md)
[Read related article](https://cazabetremy.fr/?page=publications)
