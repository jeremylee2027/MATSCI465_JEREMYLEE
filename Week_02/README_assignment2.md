# Week 02 Assignment: Virtual Detectors & Automated Diffraction Analysis

## What this notebook does
- Loads the Si/SiGe 4D-STEM dataset
- Applies CoM-based beam centering
- Builds virtual BF and ADF images by integrating user-defined regions of reciprocal space
- Saves publication-quality figures and a line profile across the interface

## What re-playing the experiment means
Because 4D-STEM stores a full diffraction pattern at every probe position, we can apply different virtual detectors after acquisition by changing the reciprocal-space mask. This lets us recreate imaging modes, test detector geometries, and extract additional quantitative metrics (intensity, CoM, radial profiles) without recollecting the experiment.