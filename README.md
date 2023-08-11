# Synthetic HST photometry for Starburst99 models with *synphot*

The aim is to generate "expected" flux from a system (defined as a starburst model redshifted to the target redshift) by simulating an HST observation. This is done by convolving the chosen model with the relevant HST filter's transmission curve. The redshift-corrected bandpass-convolved model SED can then be used to compute the (predicted) integrated flux in the given filter bandpass (i.e., [effective stimulus](https://synphot.readthedocs.io/en/latest/synphot/formulae.html#synphot-formula-effstim)). 

Ingredients:
- Evolutionary [models](https://www.stsci.edu/science/starburst99/docs/table-index.html) from the stellar population synthesis code [Starburst99](https://www.stsci.edu/science/starburst99/docs/default.htm) 
- Astropy [synphot](https://synphot.readthedocs.io/en/latest) package

These “artificial” fluxes synthesized from starburst models can then be directly compared with the extinction-corrected observed photometry, to estimate star formation parameters- rates of star formation (SFRs) in case of continuous starbursts or initial starburst masses (M<sub>burst</sub>) in the instantaneous burst scenario.
