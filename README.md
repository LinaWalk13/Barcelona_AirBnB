# Airbnb and Gentrification: The Case of Barcelona
This repository contains the code and data for analyzing the relationship between Airbnb prevalence and socio-economic change in Barcelona. We are using spatial analysis and Bayesian modeling to explore potential indicators of gentrification at an early and late timestep.

## Folder Structure

* `01_preprocessing.Rmd` – Preprocessing and merging of socio-economic datasets for each year.
* `02_spillover_computation.Rmd` – Computes the kernel-weighted spillover effect from nearby Airbnb listings based on proximity to census section borders.
* `03_plotting.Rmd` – Generates visualisations of Airbnb density, socio-economic indicators, and spatial patterns.
* `04_analysis.Rmd` – Runs Bayesian regression models.

## Datasets used

All data are processed and merged at the **census-section level** using polygon shapefiles from Barcelona Open Data.

| Dataset                      | Years                            | Description                                                                                                           |
| ---------------------------- | -------------------------------- | --------------------------------------------------------------------------------------------------------------------- |
| **Disposable Income**        | 2015, 2021                       | Average disposable household income per census section.                                                               |
| **Population**               | 2015, 2024                       | Population counts used for normalizing Airbnb density (listings per 1,000 residents).                                 |
| **Education Levels**         | 2015, 2024                       | Share of residents with tertiary education (used as a gentrification indicator).                                      |
| **Census Sections Polygons** | 2017                             | Shapefile delineating census section boundaries for spatial analysis.                                                 |
| **Airbnb Listings**          | 2015 (inferred), 2025 (observed) | Downloaded from [Inside Airbnb](http://insideairbnb.com/); 2015 listings approximated using the date of first review. |

Socio-economic data was downloaded from [Open Data Barcelona](https://opendata-ajuntament.barcelona.cat/data/en/dataset). 

## Summary of methods

* **Airbnb dnsity**: Calculated as number of listings per 1,000 residents in 2015.
* **Spillover effect**: Computed using an exponential kernel function that weights the influence of nearby Airbnb listings based on their distance to census borders.
* **Modeling**: Bayesian linear regression models (via `brms`) with interaction terms between time and Airbnb density, main effects of Airbnb density and time, as well as random effects for census sections.


---
Authors: Laura Lundbye and Lina Walkowiak


Spatial Analytics Spring 2025
