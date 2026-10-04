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
4. **Phase folding** - The light curve was folded at the determined period so that all transit events could be combined into a single averaged profile.
5. **Depth Measurement** - Transit depth was measured in two ways: (a) directly from the BLS fit, and (b) by manual comparison of the mean in-transit and out-of-transit flux.
6. **Physical interpretation** - derived an estimate for the planet radius from the measured transit depth and known stellar radius, using the relation: sqrt(depth) = R_planet / R_star.
7. Verification - 'Astroquery' library was used to query the TESS Input Catalog and the NASA Exoplanet Archive to compare obtained results against peer-reviewed, published values.

## Results
| Parameter | Obtained result | Published Data (NASA Exoplanet Archive) | Agreement of obtained result with published data|
|---|---|---|--|
| Orbital Period | 6.2643 days | 6.2678 days | 0.006 % lower|
| Transit Depth (Direct) | 247.5 ppm | 321 ppm |  22.9 % lower |
| Transit Depth (Manual) | 202.6 ppm | 321 ppm | 36.9 % lower |
| Estimated Planet Radius | 1.974 R🜨 | 1.998 R🜨 | 1.2% lower |

## Discussion
The measured orbital period was within 0.006 % of the published value, strongly confirming that the detected transit signal of TOI-144.01 was valid and accurate, ruling out the possibility of it being a noise signal.  

Transit depth was measured using two independent methods: Directly from the BLS Fit (247.5 ppm), and manual comparison between in-transit and out-of-transit flux (202.6 ppm). The results from both methods gave a consistent qualitative picture, as they both agreed in order of magnitude. However, the transit depth directly derived from the BLS fit was much closer to the published value (22.9% lower) compared to the manual estimate (36.9% lower), which led me to use the former as the primary reported depth for radius calculation.
