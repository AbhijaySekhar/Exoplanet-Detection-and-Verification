# Exoplanet Transit Detection and Verification - TOI 144.01

## Overview

In this project, I analysed NASA TESS photometric data to detect and characterise an exoplanet transit signal from the star 'TIC 261136679'. The light curve data was processed using python, and the transit depth obtained was used to compute an estimate for planetary radius. Furthermore, the orbital period of the planet was determined by analysing the frequency of dips in the transit signal. Finally, the derived parameters were critically cross-checked against officially published values in the NASA Exoplanet Archive to test the accuracy of my obtained data.

**Target/Host Star:** TIC 261136679 (R = 1.15 R☉, Teff = 5992 K, M= 1.1 M☉)   
**Exoplanet Name:** TOI-144.01  
**Data source:** NASA TESS (Transiting Exoplanet Survey Satellite), accessed via the 'lightkurve' library in python.

## Method

1. **Data Retrieval** - Searched and downloaded TESS light curve data for the target from the MAST (Mikulski Archive for Space Telescopes) catalog. The 'lightkurve' library was used to read the downloaded file into python.
2. **Detrending** - lc.flatten() command was used to flatten the light curve to remove long-term trends in stellar and instrumental signals.
3. **Determining Orbital period**- A BLS (Box Least Squares) periodogram was applied to the flattened light curve to detect the periodic signal that was statistically the most convincing, hence determining the orbital period of the planet.
4. 
