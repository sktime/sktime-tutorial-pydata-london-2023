![](images/team.jpg)

Welcome to the sktime tutorial at PyData London 2023
====================================================

This tutorial is about [sktime] - a unified framework for machine learning with time series. sktime features various time series algorithms and modular tools for sktime is a widely used scikit-learn compatible library for learning with time series.

`sktime` is easily extensible by anyone, and interoperable with the pydata/numfocus stack.

This tutorial explains how to use sktime for three learning tasks with independent instances of time series: time series classification, regression, clustering. It also explains their close connection to time series distances, kernels, and time series alignment, and how to flexibly combine such estimators to classifiers, regressors, clusterers with custom distances/kernels or feature extraction steps.

[sktime]: https://sktime.net

[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/sktime/sktime-tutorial-pydata-london-2023/main)

Also recommended:

:movie_camera: **[general sktime intro tutorial](https://github.com/sktime/sktime-tutorial-pydata-global-2021) from PyData Global 2021**\
:tv: [youtube video of sktime intro at PyData Global 2021](https://www.youtube.com/watch?v=ODspi8-uWgo)

## :rocket: How to get started

In the tutorial, we will move through notebooks section by section.

You have different options how to run the tutorial notebooks:

* Run the notebooks in the cloud on [Binder] - for this you don't have to install anything!
* Run the notebooks on your machine. [Clone] this repository, get [conda], install the required packages (`sktime`, `seaborn`, `jupyter`, `dtw-python`) in an environment, and open the notebooks with that environment. For detail instructions, see below. For troubleshooting, see sktime's more detailed [installation instructions].
* or, use python venv, and/or an editable install of this repo as a package. Instructions below.

[Binder]: https://mybinder.org/v2/gh/sktime/sktime-tutorial-pydata-global-2022/main?filepath=notebooks
[clone]: https://help.github.com/en/github/creating-cloning-and-archiving-repositories/cloning-a-repository
[conda]: https://docs.conda.io/en/latest/
[installation instructions]: https://www.sktime.net/en/latest/installation.html

Please let us know on the [sktime discord](https://discord.com/invite/54ACzaFsn7) if you have any issues during the conference, or join to ask for help anytime.

## :bulb: Description

In time series or sequence analysis, data often takes the form of multiple, independent observations of the same process, where one independent observation is an entire indexed series. Examples are sequential observations of a patient’s lab values, for many patients; or, spectrograms of independent samples (where the sequence is indexed by wavelength, not time).

As with tabular data, common learning tasks associated with such data are:
-	time series or sequence classification, where an algorithm is trained, on examples, to assign one of a set of labels to each time series or sequence. For instance, sick or healthy, for a patient; the type of substance, for a spectrogram
-	time series or sequence regression, where an algorithm is trained to assign a real number to each time series or sequence. For instance, length of stay for a patient; the alcohol content as a percentage, for a spectrogram
-	time series or sequence clustering, where sequences are assigned a cluster, or are arranged according to their similarity with each other

Unlike with tabular data, sequence and shape information is crucial in the time series (or sequence) setting, and algorithms tend to be heavily based on feature extraction steps, distances or kernel functions that are specific to time series and sequences, and/or registration or alignment of the series.

Of course, feature extraction followed by application of a “standard” tabular classifier etc constitutes an important kind of “simpler” baseline for above estimation tasks.

sktime provides unified interfaces, and ample state-of-art functionality to flexibly construct estimators of the above kind, specifically:
-	native implementations and direct interfaces to state-of-art references in time series classification, regression, and clustering, as “atomic” algorithms; e.g., k-means clusterer
-	sequential pipeline functionality to combine these with time series transformers, also natively available under the unified sktime transformer interfaces ; e.g., feature extractors, feature union
-	performant implementations of time series distances and time series kernels, exposed under the unified interface abstraction of “pairwise transformers”; e.g., time warping distance
-	adaptors and compositors to use classical tabular transformers, distances, kernels in a time series setting; e.g., using the sklearn Gaussian RBF kernel on a flattened time series
-	composition and combination estimators for time series distances and kernels, e.g., “n-th differenced distance” from ordinary and pairwise transformers; or, “mean sample kernels” 
-	interfaces and adaptors for sequence alignment as a separate learning task, which can be used to obtain distances, kernels, and estimators

The framework in sktime is highly customizable and composable; for instance, users can construct a custom time warping distance from an alignment algorithm, combine that with n-th differencing as pre-processing, and use this modified time warping distance in the k-nearest-neighbors algorithm for time series, all parameters and choices exposed and tunable via, say, grid search.

sktime is also highly extensible, and provides guided extension templates for any of the involved types of objects (distances, kernels, aligners) or estimators (time series classification, regression, clustering), which allow users to implement custom components, ready for use with the above-mentioned composition patterns that sktime provides.


## :movie_camera: Other Video Tutorials:

- [PyData 2021 - Intro to sktime](https://www.youtube.com/watch?v=ODspi8-uWgo)

- [Pydata 2022 - How to implement your own estimator in sktime](https://www.youtube.com/watch?v=S_3ewcvs_pg)

- [Pydata 2022 - Advanced Forecasting Tutorial](https://www.youtube.com/watch?v=4Rf9euAhjNc)

## :wave: How to contribute

If you're interested in contributing to sktime, you can find out more how to get involved [here](https://www.sktime.net/en/latest/get_involved.html).

Any contributions are welcome, not just code!

## Installation instructions for local use

To run the notebooks locally, you will need:

* a local repository clone
* a python environment with required packages installed

### Cloning the repository

To clone the repository locally:

`git clone https://github.com/sktime/sktime-tutorial-pydata-london-2023.git`

### Using conda env

1. Create a python virtual environment:
`conda create -y -n pydata_sktime python=3.9`
2. Install required packages:
`conda install -y -n pydata_sktime pip sktime seaborn jupyter dtw-python`
3. Activate your environment:
`conda activate pydata_sktime`
4. If using jupyter: make the environment available in jupyter:
`python -m ipykernel install --user --name=pydata_sktime`

### Using python venv

1. Create a python virtual environment:
`python -m venv .venv`
2. Activate your environment:
`source .venv/bin/activate`
3. Install the requirements:
`pip install sktime seaborn jupyter dtw-python`
4. If using jupyter: make the environment available in jupyter:
`python -m ipykernel install --user --name=pydata_sktime`
