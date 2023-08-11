# Synthetic HST photometry for Starburst99 models with *synphot*

The aim is to generate "expected" flux from a system (defined as a starburst model redshifted to the target redshift) by simulating an HST observation. This is done by convolving the chosen model with the relevant HST filter's transmission curve. The redshift-corrected bandpass-convolved model SED can then be used to compute the (predicted) integrated flux in the given filter bandpass (i.e., [effective stimulus](https://synphot.readthedocs.io/en/latest/synphot/formulae.html#synphot-formula-effstim)). 

Ingredients:
- Evolutionary [models](https://www.stsci.edu/science/starburst99/docs/table-index.html) from the stellar population synthesis code [Starburst99](https://www.stsci.edu/science/starburst99/docs/default.htm) 
- Astropy [synphot](https://synphot.readthedocs.io/en/latest) package

These artificial fluxes synthesized from starburst models can then be directly compared with the extinction-corrected observed photometry, to estimate star formation parameters- rates of star formation (SFRs) in case of continuous starbursts or initial starburst masses (M<sub>burst</sub>) in the instantaneous burst scenario.


The code and results in this repository were produced from the analysis of HST/UV imaging of 6 radio galaxies, a part of a study recently submitted for publication in ApJ. 

### Data


Each Starburst99 model (see sample_model.txt) is a set of 36 spectral energy distributions between the stellar ages of 1 Myr to 1 Gyr, with a wavelength range of 10 to 1000 nm. 


### Codes

- `10Myr_simulated_photometry.ipynb`  A basic script that computes the (simulated) UV photomtery, in units of flux and AB mags, at a chosen stellar age of 10 Myr. This is done iteratively for all target galaxies, condidering each of the 12 starburst models. 
- `SFR_Mburst_AllEpochs.ipynb` 
- `SFR+IonizingPhotons_3Models_3Epochs.ipynb`
- 'plotting'
