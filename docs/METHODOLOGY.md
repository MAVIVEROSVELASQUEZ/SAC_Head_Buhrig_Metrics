# Methodology

## 1. Project Overview

The **SAC_Head_Buhrig_Metrics** project implements a fully reproducible geometric and computational (Python 3.12.5) pipeline for the morphometric quantification of submarine canyon heads using Bührig-type metrics.

The workflow is structured to ensure:

- Deterministic reproducibility
- Clear separation between raw and processed data
- Explicit geometric definitions
- Full traceability from input DEM to final metrics

The project focuses on five tributary channels within the head of the San Antonio Submarine Canyon system:

- MCh_Main_Channel
- SACh_SanAntonio_Channel
- SDCh_SantoDomingo_Channel
- ECh_Emily_Channel
- CCh_Cartagena_Channel

In this public repository version, **only the MCh_Main_Channel is fully documented and reproducible**.  
The remaining channels are structurally preserved for architectural transparency but do not contain full datasets.

---

## 2. General Architecture

The repository follows a modular structure:

SAC_HEAD_BUHRIG_METRICS/
│
├── channels/
│ ├── MCh_Main_Channel/
│ ├── SACh_SanAntonio_Channel/
│ ├── SDCh_SantoDomingo_Channel/
│ ├── ECh_Emily_Channel/
│ ├── CCh_Cartagena_Channel/
│
├── common_data/
├── docs/
├── requirements.txt
├── LICENSE
├── CITATION.cff
└── README.md


The workflow is organized according to a deterministic processing logic:

raw → processed → outputs


This structure guarantees complete separation between:

- Input data
- Intermediate geometric products
- Final morphometric metrics

---

## 3. Common Data

The directory `common_data/` contains shared regional inputs:

- Bathymetric DEM (GeoTIFF, 32-bit float)
- Canyon edge shapefiles (Left / Right classification)

The DEM was generated from SHOA bathymetric point data (CSV format, WGS84 coordinates) and interpolated using ordinary kriging before reprojection to:

**WGS 1984 UTM Zone 18S (EPSG:32718)**

All geometric computations are performed in projected metric coordinates.

---

## 4. Channel-Level Structure (Example: MCh_Main_Channel)

The Main Channel (MCh) is provided as the fully reproducible example.

Structure:

MCh_Main_Channel/
│
├── data/
│ ├── raw/
│ │ ├── MCh_thalweg.shp
│ │ ├── MP_transects_CLEAN.shp
│ │
│ ├── processed/
│ │ ├── MCh_profile_keypoints_P1_P2_P3.shp
│ │ ├── MCh_profile_P4.shp
│ │ ├── MCh_profile_keypoints_P1_P2_P3_P4.shp
│
├── outputs/
│ ├── tables/
│ ├── figures/
│ ├── validation_profiles/
│ ├── all_profiles_MP/
│
└── src/
├── 01_MCh_extract_profile_keypoints_P1_P2_P3.py
├── 02_MCh_calculate_P4_Wmax_Dmax_intersection.py
├── 03_MCh_integrate_keypoints_P1_P2_P3_P4.py
├── 04_MCh_calculate_buhrig_metrics.py
├── 05_MCh_test_single_profile_geometry.py
├── 06_MCh_all_profiles.py
├── 07_MCh_Thalweg_Metrics.py


---

## 5. Transverse Metrics Workflow

For each transverse profile:

1. Extract P1 (thalweg), P2 (left edge), P3 (right edge)
2. Compute P4 via vector projection
3. Calculate:
   - W1, W2, Wmax
   - Dmax
   - H1, H2
   - B1, B2
   - SWmax = max(B1, B2)
   - Wmax/Dmax

No symmetry or orthogonality assumptions are imposed.

---

## 6. Longitudinal Metrics

From the thalweg geometry:

- L (real length)
- L_straight
- SIav = L / L_straight
- Δz
- thGav = Δz / L
- Gradient_max (numerical differentiation)

500 normalized sampling points are used to extract the depth profile.

---

## 7. Reproducibility Principles

The pipeline follows:

- Explicit geometric definitions
- Script numbering reflecting logical execution order
- Separation between geometry construction and metric derivation
- Batch visual validation of all profiles

This design ensures scientific traceability and compatibility with Q1 reproducibility standards.

---

## 8. Public vs Full Version

The present repository provides:

- Full reproducibility for MCh_Main_Channel
- Structural architecture for additional channels

The complete dataset for all channels is documented in the associated Zenodo publication.
