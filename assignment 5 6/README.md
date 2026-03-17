# MAT_SCI 465 -- Week 5 & 6 Assignment

## Electron Microscopy Simulation with abTEM

This repository contains the completed notebook and figures for the
**Week 5--6 combined assignment** in **MAT_SCI 465: 4D‑STEM &
Data‑Driven Microscopy**. The goal of this assignment is to simulate
transmission electron microscopy (TEM) imaging using the **abTEM**
multislice framework.

------------------------------------------------------------------------

## Overview

The notebook demonstrates the core workflow of TEM image simulation:

### 1. Atomic Structure Construction

-   The Si₃N₄ unit cell is defined using **ASE (Atomic Simulation
    Environment)**.
-   The structure is orthogonalized to satisfy multislice simulation
    requirements.
-   The atomic structure is visualized to confirm correct geometry.

### 2. Multislice Simulation

-   An electron wave is propagated through the crystal using the
    **multislice method**.
-   The exit wave leaving the sample is calculated.

### 3. Contrast Transfer Function (CTF)

Two microscope configurations are compared:

**Uncorrected microscope** - C10 = -600 Å - C30 = 1.3 × 10⁷ Å

**Aberration‑corrected microscope** - C10 = 30 Å - C30 = -8 × 10⁴ Å

The CTF profiles illustrate how aberration correction improves transfer
of high spatial frequencies.

### 4. Image Formation

The exit wave is passed through each CTF to simulate the image recorded
by the microscope.

### 5. Noise Simulation

Poisson noise is added to simulate realistic electron counting
statistics at a finite electron dose.

------------------------------------------------------------------------

## Repository Structure

    465-week5-6-assignment/
    │
    ├── assignment_combined_5_6.ipynb
    ├── README.md
    │
    └── figures/
        ├── figure_1.png
        ├── figure_2.png
        ├── figure_3.png
        ├── figure_4.png
        ├── figure_5.png
        └── figure_6.png

------------------------------------------------------------------------

## Requirements

The notebook requires the following Python packages:

-   abTEM
-   ASE
-   NumPy
-   Matplotlib

Install dependencies with:

``` bash
pip install abtem ase numpy matplotlib
```

------------------------------------------------------------------------

## How to Run

1.  Open the notebook:

```{=html}
<!-- -->
```
    assignment_combined_5_6.ipynb

2.  Restart the kernel and run all cells:

```{=html}
<!-- -->
```
    Kernel → Restart & Run All

3.  The figures will be generated automatically within the notebook.

------------------------------------------------------------------------

## Purpose

This assignment demonstrates how electron microscopy images are formed
through the interaction of the electron wave with the specimen and the
microscope transfer function. It highlights the impact of aberrations
and noise on image quality and illustrates the advantages of aberration
correction in modern TEM instruments.
