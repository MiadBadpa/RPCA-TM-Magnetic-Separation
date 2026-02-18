RPCA-TM Magnetic Anomaly Separation
Overview

This repository provides a MATLAB implementation of a multiscale magnetic anomaly separation framework based on Trajectory Matrix (TM) embedding and Robust Principal Component Analysis (RPCA).

The method enables accurate separation of:

Regional (deep) magnetic components

Residual (shallow/local) magnetic anomalies

and supports interpretation of subsurface structures and mineral exploration targets.

The workflow decomposes spatial magnetic data into low-rank and sparse components, allowing improved geological interpretation and depth-related analysis.

Scientific Background

This study presents a novel framework for precise separation of shallow (residual) and deep (regional) magnetic components and their depth interpretation.

The approach:

constructs a trajectory matrix (TM) to capture spatial correlations,

applies Robust PCA (RPCA) to decompose the data into:

low-rank component → regional field

sparse component → residual anomalies,

determines optimal RPCA regularization using the Elbow Point method,

reconstructs separated fields through inverse trajectory transformation.

The method was validated using synthetic multi-source magnetic models and real field data.

Input Data
Synthetic Model Data

Before running this workflow, synthetic models were generated using a separate script (Grav_Mag_UT) developed by the author.

The synthetic model outputs consist of MATLAB files:

magnetic response stored in variable dt

gravity response stored in variable g

⚠️ Any synthetic modeling software can be used as long as the output is stored as a MATLAB matrix with the same variable naming convention.

Real Data

The workflow also supports real field measurements.

In this study, real magnetic data from the Kuh Zireh mineralized region (Iran) were used.

Any real magnetic dataset can be used provided it is formatted as a 2-D matrix.

Workflow
1️⃣ Build Trajectory Matrix

trajectory_matrix.m
Constructs the trajectory matrix from a 2-D input grid.

Test script:

test_trajectory_matrix.m

2️⃣ Select Optimal RPCA Parameter (λ)

elbow_lambda_selection.m
Determines optimal lambda using the elbow point method.

Output:

energy curve plot

optimal lambda value

3️⃣ Robust PCA Decomposition

rpca_ialm.m
Implements Robust PCA using the Inexact Augmented Lagrange Multiplier method.

Test script:

test_rpca.m


Outputs:

Low-rank matrix (regional field)

Sparse matrix (residual anomalies)

4️⃣ Inverse Trajectory Reconstruction

inverse_trajectory_matrix.m
Reconstructs spatial fields from the decomposed matrices.

Test script:

test_inverse_trajectory.m

Required Input Format

Input must be a 2-D matrix stored in a MATLAB file.

Example:

load('magnetic_data.mat')


Where the variable may be:

dt → magnetic anomaly

g → gravity data

any matrix representing potential-field data

Outputs

The workflow produces:

low-rank regional magnetic field

sparse residual anomaly field

reconstructed spatial grids

figures for visualization

optimal λ selection curve

Applications

mineral exploration

mapping intrusive bodies

fault zone detection

geological structure interpretation

multiscale potential-field analysis

Requirements

MATLAB (tested with standard numerical toolboxes)

No proprietary toolboxes are required.

Reproducibility

All scripts required to reproduce the separation workflow are provided.

Users may run the pipeline using either:

synthetic model responses

real magnetic field data

Citation

If you use RPCA-TM-Magnetic-Separation in your research, please cite it as:

BibTeX:

@software{Badpa2026RPCA,
  author       = {Miad Badpa},
  title        = {RPCA-TM-Magnetic-Separation: MATLAB code for separating shallow and deep magnetic/gravity components},
  version      = {v1.0.0},
  date         = {2026-02-18},
  url          = {https://github.com/MiadBadpa/RPCA-TM-Magnetic-Separation},
  doi          = {10.5281/zenodo.18680570},
  license      = {MIT}
}


Plain citation:

Miad Badpa (2026). RPCA-TM-Magnetic-Separation: MATLAB code for separating shallow and deep magnetic/gravity components, Version v1.0.0, DOI: 10.5281/zenodo.18680570
, MIT License.
