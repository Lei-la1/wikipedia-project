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

Manipulations of the data were used:
- Normalization : both global normalization and normalization signal by
signal. We even tried with not normalized data which did not affect the
performance.
- Fourier transformation of the signals was also tried but was not a good
idea.
- Transformation of the data: to lessen the irregularity of the signals
we have, we tried multiple ways of smoothing like Gaussian smoothing,
taking the log of the signals, moving average... The moving average yields
good results and even very good ones for large smoothing window.

Besides, we also tried to make our signals look like the cognitive tasks
signals used in the paper mentioned earlier, we used transformation into
binary signals. With those rectangular signals, we only keep information
on activation (if the number of visits suddenly increases) or deactivation
(if the number of visits suddenly decreases) of a page. It makes sense
that the model can predict future behaviors of the signals as Wikipedia
pages are correlated. Usually a whole bunch of pages that are related
somehow (related content for example) get activated together. Indeed,
the experiment shows that the pages that had at least 1 activation on the
n days of the input get accurate predictions.
We also tried to smooth the data (moving average) then transforming
the signals into binary ones. We had interpolation but no Extrapolation
(basically the output of the model is the input).

With the results of the experiments above, we deduce that we could make
the mode learn from the binary signals and predict. The idea is to merge
peaks that are too close and give more importance to the narrow ones by
extending them in time. This way, we still have data that resembles to
the input used for cognitive tasks. And most importantly, we obviously
preserve the idea of activation of a page.
This experiment yields good predictions. and will be used to get the connectivity matrix.


Overall: we managed to get good accurate predictions using full rank RNN
and simplification of the data. We did not get good results using lrRNN
even when trying to fit the trajectories of lrRNN to those of the trained
frRNN.
