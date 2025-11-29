🌌 CMB Power Spectrum Analysis (Planck 2018 SMICA)

Author: Toghrul Hasanli
Course / Project: Cosmology & Data Analysis · Python / Jupyter
Tools: Healpy · CAMB · Astropy · NumPy · Matplotlib
Data Source: ESA Planck 2018 (Public Release)

📘 Overview

This project reproduces the Cosmic Microwave Background (CMB) angular power spectrum using real Planck 2018 SMICA data.
The goal is to:

Load and clean CMB sky maps

Apply Planck temperature masks

Compute the observed spectrum 
𝐶
ℓ
C
ℓ
	​

 and 
𝐷
ℓ
D
ℓ
	​


Detect acoustic peaks

Generate the theoretical ΛCDM spectrum from CAMB

Compare observations with cosmological predictions

This workflow follows the methodology used in real CMB research and demonstrates how Planck data encodes the physics of the early Universe.

🛰️ Dataset

All data files are stored in the data/ directory:

File	Description
COM_CMB_IQU-smica_2048_R3.00_full.fits	SMICA CMB map (I, Q, U Stokes components + masks)
COM_CMB_IQU-commander_2048_R3.00_full.fits	Commander map (optional alternative)
Planck_Parchment_RGB.txt	Official Planck colormap

The SMICA map (field 0) and its temperature mask (field 3) are used for all core computations.

🧠 Scientific Objectives
✔ 1. Visualize the CMB Sky

Load the SMICA intensity map

Apply the official Planck temperature mask

Plot a full-sky Mollweide projection using the Planck colormap

✔ 2. Extract the Power Spectrum

Compute:

𝐶
ℓ
,
𝐷
ℓ
=
ℓ
(
ℓ
+
1
)
2
𝜋
𝐶
ℓ
C
ℓ
	​

,D
ℓ
	​

=
2π
ℓ(ℓ+1)
	​

C
ℓ
	​


using healpy.anafast() on the cleaned map.

✔ 3. Detect Acoustic Peaks

Identify the characteristic peaks at:

ℓ ≈ 220 (first acoustic peak)

ℓ ≈ 540

ℓ ≈ 800

These correspond to sound waves in the early Universe plasma.

✔ 4. Generate the Theoretical ΛCDM Spectrum

Using CAMB with Planck-like cosmological parameters:

H₀ = 67.36

Ω_b h² = 0.02237

Ω_c h² = 0.1200

τ = 0.0544

Σ mν = 0.06 eV

✔ 5. Compare Observation vs Theory

Plot SMICA vs ΛCDM on logarithmic axes.
The spectra should align closely—confirming the ΛCDM model and the quality of Planck data.

📊 Example Outputs
1. Cleaned CMB Map

Mollweide projection

Official Planck parchment colormap

Masked Galactic region removed

2. Power Spectrum

Raw 
𝐷
ℓ
D
ℓ
	​

 (gray)

Smoothed spectrum (red)

3. Acoustic Peak Detection

Peaks marked using scipy.signal.find_peaks

4. SMICA vs CAMB Comparison

ΛCDM theoretical curve (black dashed)

SMICA spectrum (red, rescaled)

🧰 Tools & Libraries
Library	Purpose
NumPy	Numerical operations
Matplotlib	Plotting maps & spectra
Astropy (FITS)	Reading Planck FITS files
Healpy (HEALPix)	CMB maps, masking, spectra
CAMB	Cosmological predictions & theory
SciPy	Smoothing, peak detection
📁 Project Structure
cmb-power-spectrum-planck/
│
├── data/
│   ├── COM_CMB_IQU-smica_2048_R3.00_full.fits
│   ├── COM_CMB_IQU-commander_2048_R3.00_full.fits
│   ├── Planck_Parchment_RGB.txt
│
├── notebook/
│   └── cmb_power_spectrum.ipynb
│
├── plots/
│   ├── smica_clean_map.png
│   ├── Dl_raw_vs_smooth.png
│   ├── peak_detection.png
│   └── smica_vs_camb.png
│
└── README.md

▶️ How to Run the Project

Create a virtual environment:

python3 -m venv venv
source venv/bin/activate


Install required packages:

pip install numpy matplotlib healpy astropy camb scipy


Open the Jupyter Notebook:

jupyter notebook


Run all cells in cmb_power_spectrum.ipynb.

🏁 Conclusion

This project demonstrates a complete mini–CMB analysis pipeline:

Data cleaning

Power spectrum extraction

Physical peak detection

Comparison with ΛCDM cosmology

The results reproduce the key scientific insight of the Planck mission:
the observed Universe is consistent with the ΛCDM model.

📚 References

Planck Collaboration (2018), Planck 2018 Results

HEALPix: Górski et al. (2005)

CAMB: Lewis et al. (2000)

Tutorials from ESA/Planck Legacy Archive
