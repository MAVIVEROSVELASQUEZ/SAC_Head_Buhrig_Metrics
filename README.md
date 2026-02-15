# SAC_Head_Buhrig_Metrics

## Reproducible Geometric and Computational Implementation of Bührig-Type Metrics Applied to the Head of the San Antonio Submarine Canyon System

Author: Marco Antonio Viveros Velásquez  
ORCID: https://orcid.org/0009-0001-3653-5758  
Year: 2026  

---

## Overview

This repository implements a reproducible geometric and computational pipeline (Python 3.12.5) for the calculation of Bührig-type morphometric metrics in the head sector of the San Antonio Submarine Canyon System (central Chile).

The workflow provides explicit, traceable, and fully reproducible computation of:

### Transverse Metrics
- Wmax (maximum canyon width)
- Dmax (maximum canyon depth)
- SWmax (maximum flank slope angle)
- Wmax/Dmax (aspect ratio)
- B1 and B2 (lateral angles)
- H1 and H2 (oblique flank lengths)

### Longitudinal Metrics
- L (real thalweg length)
- L_straight (straight-line length)
- SIav (average sinuosity index)
- Δz (total vertical difference)
- thGav (mean longitudinal gradient)
- Gradient_max (maximum absolute gradient)

---

## Repository Scope

This public repository includes:

- Full reproducible implementation for the main channel:
  **MCh_Main_Channel**
- Modular project architecture prepared for additional tributary channels:
  - SACh_SanAntonio_Channel
  - SDCh_SantoDomingo_Channel
  - ECh_Emily_Channel
  - CCh_Cartagena_Channel

The remaining channels are preserved as structural modules for scalability demonstration.

The complete multi-channel implementation and formal methodological documentation are available via Zenodo.

---

## Data

The Digital Elevation Model (DEM) was generated from bathymetric point data provided by the Chilean Hydrographic and Oceanographic Service (SHOA), originally distributed in CSV format (latitude, longitude WGS84, and depth values).

The bathymetric points were interpolated using ordinary kriging to generate a continuous surface and subsequently reprojected to:

WGS 1984 UTM Zone 18 South (EPSG:32718)

The final DEM is stored as a 32-bit floating-point GeoTIFF raster.

---

## Project Architecture

The workflow follows a deterministic structure:

raw → processed → outputs


Main directories:

channels/
common_data/
docs/


Each channel replicates the exact same numbered computational sequence (01–07), ensuring methodological consistency and scalability to other submarine canyon systems.

---

## Methodological Principles

- Explicit geometric definition of key points P1–P4  
- Vector projection for rigorous P4 computation  
- Angular calculation using the Law of Cosines  
- No assumption of symmetry or orthogonality  
- Individual and batch graphical validation  
- Strict separation between raw data and derived metrics  

The pipeline is designed to meet reproducibility standards expected in Q1 geomorphology journals.

---

## Requirements

Python 3.x  

Main libraries:

- numpy  
- pandas  
- geopandas  
- rasterio  
- matplotlib  
- shapely  

Installation:

pip install -r requirements.txt


---

## Citation

Full methodological framework available at:

Viveros Velásquez, M. A. (2026). SAC_Buhrig_Metrics_V1 (v1.0.6). Zenodo.  
https://doi.org/10.5281/zenodo.18618759  

Viveros Velásquez, M. A. (2026). Manual for the reproducible geometric and computational implementation of Bührig-type metrics in submarine canyons (1.0.0). Zenodo.  
https://doi.org/10.5281/zenodo.18446821  

---

## License

© 2026 Marco Antonio Viveros Velásquez  
All rights reserved.

This repository is published for academic transparency and methodological documentation purposes only.

No reproduction, redistribution, modification, commercial use, or derivative work is permitted without prior written authorization from the author.

---

## Academic Contact

For scientific inquiries or formal usage requests:

Marco Antonio Viveros Velásquez  
ORCID: https://orcid.org/0009-0001-3653-5758  