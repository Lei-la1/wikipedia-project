# Attempting to approximate wikipedia page visits activity using a low-rank RNN

## Context
In previous work, that was shown that low rank RNN (lrRNN) can be used
to predict the output of four cognitive tasks. The trajectories of lrRNN can also
be fitted to those of a full rank.
In this project, we try to test this on a similar yet different setting, we want to
use number of visits of Wikipedia pages to reconstruct the links between pages.
Finding the Wikipedia graph would permit to study in what way Wikipedia
acts as human brain and how memory and real world events trigger activation
of specific part of the graph.

## Goal
The initial goal was to use Wikipedia data to train the lrRNN model then
analyse the connectivity matrix describing the neural network.

## Summary/General remarks
Even with large rank, the the full rank RNN (frRNN)outperforms the lrRNN in all the experiments we had. However, results from the frRNN are not
necessary considered good. Further details will be given (see report).
