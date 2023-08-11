# Synthetic HST photometry for Starburst99 models

The aim is to generate "expected" flux from a system (defined as a starburst model redshifted to the target redshift) by simulating an HST observation. This is done by convolving the chosen model with the relevant HST filter's transmission curve. The redshift-corrected bandpass-convolved model SED can then be used to compute the (predicted) integrated flux in the given filter bandpass (i.e., [effective stimulus](https://synphot.readthedocs.io/en/latest/synphot/formulae.html#synphot-formula-effstim)). 

Ingredients:
- Evolutionary [models](https://www.stsci.edu/science/starburst99/docs/table-index.html) from the stellar population synthesis code [Starburst99](https://www.stsci.edu/science/starburst99/docs/default.htm) 
- [synphot](https://synphot.readthedocs.io/en/latest) and [stsynphot](https://github.com/spacetelescope/stsynphot_refactor) packages

These artificial fluxes synthesized from starburst models can then be directly compared with the extinction-corrected observed photometry, to estimate star formation parameters- rates of star formation (SFRs) in case of continuous starbursts or initial starburst masses (M<sub>burst</sub>) in the instantaneous burst scenario.


The code and results in this repository were produced from the analysis of HST/UV imaging of 6 radio galaxies, a part of a study recently submitted for publication in ApJ. 

----------------------------

### Data

The target sample consists of 6 radio galaxies, with their redshifts, luminosity distances and HST imaging filters required as input. HST imaging for this sample was obtained with WFC3/UVIS in Cycle 25 GO program 15245 (PI: C. O’Dea).  

There are 6 models each for continuous and instantantaneous star formation in the original 1999 dataset (hosted [here](https://www.stsci.edu/science/starburst99/docs/table-index.html)). See starburst_models_info.txt for details. Each Starburst99 model (example_model.txt) is a set of spectral energy distributions, associated with 36 epochs between the stellar ages of 1 Myr to 1 Gyr, on a wavelength range of 10 to 1000 nm. 

Also used in this analysis is the Starburst99 "far-UV properties" model, i.e. the number of (ionizing) photons produced with wavelength below 912 Å vs. time, for continuous and single-burst star formation.

### Codes

- `10myr_Epoch.ipynb` |  A basic script that computes the (simulated) UV photomtery, in units of flux and AB mags, at a chosen stellar age of 10 Myr. This is done iteratively for all target galaxies, considering each of the 12 starburst models.
- `SFR_Mburst_AllEpochs.ipynb` | Automated computation of "expected" SFRs and M<sub>burst</sub> values for all targets in each model scenario. Observed flux from HST observations is used to scale the model-produced fluxes. This can be used to check for "best fit" models by comparing with observed SFRs.
- `SFR+IonizingPhotons_3Models_3Epochs.ipynb` | This script includes the calculation of ionizing photons from the hot, massive stars, along with SFRs and starburst masses (continuous and instantaneous burst cases) at the young ages of 1 Myr, 10 Myr and 100 Myr. This is done with only those models that include nebular continuum with stellar UV emission. 
-  `Obs_vs_Syn_plots` | Plotting the comparison of "expected" SFRs and initial burst masses in the 6 radio galaxies, with the values deduced from observations. The best-fit model/epoch is highlighted.

