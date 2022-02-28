# Unsupervised-Domain-Adaptation-For-Star-Formation-History

This study has been conducted with the help of the [ADAPT](https://github.com/adapt-python/adapt) library.

## Abstract

The prevalent paradigm of machine learning today is to use past observations to predict future ones What if, however, we are interested in knowing the past given the present? This situation is indeed one that astronomers must contend with often To understand the formation of our universe, we must derive the time evolution of the visible mass content of galaxies based on the Spectral Energy Distribution (SED) observed on earth.

## What’s the problem?

As galaxies evolve over billions of years, it is impossible to completely capture any single galaxy’s mass evolution as a function of time Astrophysicists then generate cosmological simulation, which allow building artificial star formation histories with the corresponding radiation However, a significant challenge arises due to the domain shift between simulated and real galaxies (see Figure 1).


<p align="center">
  <figure>
    <img src="images/image_sed_uda_2_lowrez.png" alt="uda_4_seds">
    <figcaption> <b>Figure 1</b>: <i>Radiation spectrums with corresponding star formation histories can be recorded from cosmological simulation to form a dataset (X, y). This dataset is used to learn a machine learning model. Because of the domain shift between real radiation spectrums and simulated ones, domain adaptation is used to adapt the learned machine learning model to the real observations</i></figcaption>
  </figure>
</p>

## Methodology

Our training and test data sets consist of SEDs from three state of the art cosmological galaxy formation simulations SIMBA, EAGLE and IllustrisTNG. Input consists of flux densities in 20 filters, and output consists of SFH (time series) in 29 bins from t= 0 to t= 13 8 billion years ago We train on any two simulations and test on the third one This is a necessary first step in developing a technique that can ultimately be applied to observational data.
1. We apply KLIEP 4 an instance based method that reweights the sources in order to minimize the KL divergence between any two domains
2. We normalize each SFH time series vector by its sum, and apply kernelPCA to reduce the dimensionality of the normalized SFH time series vectors from 29 to 3
3. We fit two NNs on the source data using the KLIEP derived importance weights one network to predict the 3 kPCA components, the other to predict SFH_sum.


<p align="center">
  <figure>
    <img src="images/kliep_lowrez.png" alt="kliep">
    <figcaption> <b>Figure 2</b>: <i>KLIEP brings different domains closer by reweighing source samples. <b>Top</b>: Scatter plot of the first two kPCA components. <b>Bottom</b>: KDE plots of log of the first two features.</i></figcaption>
  </figure>
</p>


