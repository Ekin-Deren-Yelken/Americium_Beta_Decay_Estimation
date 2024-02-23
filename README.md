# Americium_Beta_Decay_Estimation
This code cleans and analyzes data obtained using the experimental set up in Figure 1 and LABVIEW software to measure the halflife and lifetime of an exicted state of Neptunium which has undergone beta decay from Americium.

![image](https://github.com/Ekin-Deren-Yelken/Americium_Beta_Decay_Estimation/assets/128660105/4aa90410-460c-4c9d-9b83-b6c13b11948c)
Figure 1: Experimental Set Up

## Description
Radioactivity, since its discovery by Henri Becquerel, Pierre Curie, and Marie Curie in 1896 has shone light on several natural phenomena and found its way into much of modern technology today. Radioactive decay is a part of this phenomenon in which energetic particles are emitted by unstable nuclei [1] . The radioactive decay law states that the amount of an unstable nucleus (N(t)) changes proportional to a ‘lifetime’ constant () as a function of time:

$\frac{\mathrm{d} }{\mathrm{d} x}N(t) = -\frac{1}{\tau }N(t)$

Equation 1 : Radioactive Decay Law [2]

Equation 1 describes a process that is exponential in nature indicating that it is also strictly probabilistic. Thus, the ‘lifetime’ can be thought of as a measure of the probability. This can manifest statistically as a histogram with bins defined by amount of time a nucleus is excited for and counts as number of times this amount of time occurs [2] . The range of possible lifetimes is vast, with direct measurement of values ranging from 10^-15 seconds to greater than 10 13 years [2], [3], [4]. A better understanding of radioactive decay lifetimes is critical to furthering technology that takjes advantage of these phenomena 

This experiment measures the lifetime of an excited state of Neptunium ( 237 Np*, where * signifies ‘excited’) by analyzing the distribution of alpha decay in Americium ( 241 Am). This can be experimentally obtained by assuming a curve fit to the histogram produced by detected Beta decays follows the general form of 

$N(t)=N_{0}e^{-\lambda t}+C$ and $y=e^{-at}+b$

The lifetime is expected to be ~67 ns [5] and can be obtained using

$\tau =\frac{1}{a}=\frac{t_{\frac{1}{2}}}{ln(2)}$

## Procedure
1. The TPHC must be calibrated using an ORTEC time calibrator and gate and delay generator.
2. Once calibrated, output signals that were amplified and controlled with the discriminator threshold are fed into the input of the TPHC. The trigger and output signal are sent to be view on the oscilloscope and LabView via the multi-channel analyzer.
3. Delay between signals must be introduced. The easiest way to do this is by ataching a long wire between one of the signal discriminators and the TPHC. In this experiment, this was done between the gamma discriminator and TPHC.
4. LabView dashboard and software is run over a long period of time to develop a histogram where voltages incrementing in 0.05V are the bins.
5. A clearer histogram can be obtained by fine tuning the gain and threshold on the amplifiers and discriminators respectively.
6. Data can be exported in the form of a comma separated value (CSV) file. This can be imported into data analysis software such as Python and MATLAB. The histogram is expected to follow a decaying exponential in its general shape.
8. The data is cleaned and analyze in the following steps:
- Voltage can be converted into time using the time calibration results in the setup. A new histogram with time as the x-axis is made.
- A baseline noise is observed prior to the expected exponential decay. This is removed by averaging the counts in bins related to noise and subtracting them from all the data.
- All bins that are zero or negative are removed and the exponential curve is isolated.
- Using curve fiting tools, an exponential function is fit onto the data.
- It can be observed that the exponential is a convolution of a gaussian and exponential function. For more accurate results, switch the discriminator outputs to positive and obtain a gaussian. Use the software to deconvolve the gaussian and exponential curve, which will theoretically result in a smooth exponential decay curve.
10. The lifetime can be found using the general forms. The lifetime $\tau$ is calculated analytically using halflife $t_{/frac{1}{2}}$
11. To verify results, consult tabulated values for half life and lifetime found in literature

## Results
![image](https://github.com/Ekin-Deren-Yelken/Americium_Beta_Decay_Estimation/assets/128660105/ec601cca-4324-4ff1-9e86-5580c44d941f)

![image](https://github.com/Ekin-Deren-Yelken/Americium_Beta_Decay_Estimation/assets/128660105/5daf1902-39f1-450f-bee8-96c14736fd14)

A lifetime of 96ns and halflife of 67 ns is found.

## Resources and Citations
[1] “DOE Explains...Radioactivity,” Energy.gov. Accessed: Feb. 06, 2024. [Online]. Available: https://www.energy.gov/science/doe-explainsradioactivity
[2] E. Segre, Nuclei and Particles: An Introduction to Nuclear and Subnuclear Physics (2nd Edition). Redwood City, Ca: Benjamin-Cummings Publishing Company, Subs Of Addison Wesley Longman, Inc, 1977. Accessed: Feb. 06, 2024. [Online]. Available: https://www.biblio.com/book/nuclei-particles- introduction-nuclear-subnuclear-physics/d/1538238155
[3] J. B. Cumming and D. E. Alburger, “Search for the decay of 180Tam,” Phys. Rev. C Nucl. Phys., vol. 31, no. 4, pp. 1494–1498, Apr. 1985, doi: 10.1103/physrevc.31.1494.
[4] “Energy traps in atomic nuclei | Nature.” Accessed: Feb. 06, 2024. [Online]. Available: https://www.nature.com/articles/19911
[5] “Table of Isotopes: 1999 Update, 8th Edition | Wiley.” Accessed: Feb. 06, 2024. [Online]. Available: https://www.wiley.com/en-us/Table+of+Isotopes%3A+1999+Update%2C+8th+Edition-p- 9780471356332
