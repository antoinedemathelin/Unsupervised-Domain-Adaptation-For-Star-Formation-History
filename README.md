# Unsupervised-Domain-Adaptation-For-Star-Formation-History

This study has been conducted with the help of the [ADAPT](https://github.com/adapt-python/adapt)

## Abstract

The prevalent paradigm of machine learning today is to use past observations to predict future ones What if, however, we are interested in knowing the past given the present? This situation is indeed one that astronomers must contend with often To understand the formation of our universe, we must derive the time evolution of the visible mass content of galaxies based on the Spectral Energy Distribution (SED) observed on earth.

## What’s the problem?

As galaxies evolve over billions of years, it is impossible to completely capture any single galaxy’s mass evolution as a function of time Astrophysicists then generate cosmological simulation, which allow building artificial star formation histories with the corresponding radiation However, a significant challenge arises due to the domain shift between simulated and real galaxies (see Figure 1).

![uda_4_seds](images/image_sed_uda_2.png)
*Figure 1: Radiation spectrums with corresponding star formation histories can be recorded from cosmological simulation to form a dataset (X, y). This dataset is used to learn a machine learning model. Because of the domain shift between real radiation spectrums and simulated ones, domain adaptation is used to adapt the learned machine learning model to the real observations*
