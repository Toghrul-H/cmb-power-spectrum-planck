.

🌌 CMB Power Spectrum Analysis with Planck 2018 Data

Author: Toghrul Hasanli
Environment: Linux, Python (venv), Jupyter Notebook
Tools: Healpy, CAMB, Astropy, NumPy, Matplotlib

📌 Overview

This project reproduces key results of modern cosmology by analyzing real Planck 2018 CMB temperature data.
The goal is to extract the CMB angular power spectrum from the SMICA map and compare it with the ΛCDM theoretical prediction generated using CAMB.

The workflow follows the same methodology used in contemporary CMB research pipelines.

🎯 Project Objectives

Load and inspect Planck SMICA CMB maps in HEALPix format.

Apply the official Planck temperature mask to remove galactic contamination.

Plot the cleaned full-sky CMB map using a Planck-style colormap.

Compute the observed angular power spectrum 
𝐶
ℓ
C
ℓ
	​

.

Convert to

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
D
ℓ
	​

=
2π
ℓ(ℓ+1)
	​

C
ℓ
	​


Smooth the spectrum and detect acoustic peaks.

Generate the theoretical ΛCDM spectrum using CAMB.

Compare the observed and theoretical curves on log–log axes.

📂 Dataset

All datasets are stored under the data/ directory:

SMICA map
COM_CMB_IQU-smica_2048_R3.00_full.fits

Temperature map (I), Q/U polarization maps, masks

Commander map (optional)
COM_CMB_IQU-commander_2048_R3.00_full.fits

Planck Parchment Colormap
Planck_Parchment_RGB.txt

🧪 Analysis Steps
1. Load and mask the CMB map

Extract SMICA I_STOKES (temperature)

Load TMASK to remove invalid or contaminated pixels

Apply mask → produce a cleaned CMB map

2. Visualize the CMB sky

Render Mollweide projection

Use official Planck-themed colormap

Adjust map contrast with percentiles

3. Compute the CMB angular power spectrum

Use healpy.anafast

Compute both 
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


Apply smoothing (moving average or Gaussian)

4. Detect acoustic peaks

Use scipy.signal.find_peaks

Identify:

1st peak ~ ℓ ≈ 220

2nd peak ~ ℓ ≈ 540

3rd peak ~ ℓ ≈ 800

Mark them visually

5. Generate theoretical ΛCDM spectrum

Use CAMB with Planck-like parameters:

H₀ = 67.36

Ω_b h² = 0.02237

Ω_c h² = 0.1200

τ = 0.0544

Σmν = 0.06 eV

6. Compare Planck vs CAMB

Overlay curves

Normalize SMICA spectrum for visual comparison

Observe strong alignment of peaks

📊 Key Results
✔ Full-sky CMB map

Cleaned and masked SMICA map shows expected hot/cold anisotropies.

✔ Observed CMB power spectrum

Acoustic peak structure clearly visible after smoothing.

✔ Peak detection

Automated detection matches theoretical expectations.

✔ SMICA vs ΛCDM comparison

Both spectra overlap closely → reproducing Planck’s primary cosmological results.

📦 Python Libraries Used
Library	Purpose
NumPy	Numerical operations
Matplotlib	Plotting (maps & spectra)
Healpy	HEALPix map handling, spherical harmonics, anafast
Astropy	FITS file reading
CAMB	Theoretical ΛCDM CMB spectrum
SciPy	Smoothing + peak detection
▶️ How to Run

Create virtual environment:

python3 -m venv venv
source venv/bin/activate


Install requirements:

pip install numpy matplotlib healpy astropy camb scipy


Start Jupyter Notebook:

jupyter notebook


Run the notebook file:

cmb_power_spectrum.ipynb

🧭 Project Structure
cmb_project/
│
├── data/
│   ├── COM_CMB_IQU-smica_2048_R3.00_full.fits
│   ├── COM_CMB_IQU-commander_2048_R3.00_full.fits
│   └── Planck_Parchment_RGB.txt
│
├── cmb_power_spectrum.ipynb
├── plots/              
└── README.md

📘 References

Planck Collaboration (2018) — Planck Legacy Papers

HEALPix / Healpy documentation

CAMB documentation

“The Cosmic Microwave Background” — Wayne Hu

“A Student’s Guide to the CMB” — Klauber

📌 Summary

This project successfully reproduces the essential cosmological result:

➡️ The observed Planck CMB power spectrum closely matches the ΛCDM theoretical prediction.

It demonstrates proper use of:

CMB data processing

HEALPix formats

Power spectrum estimation

Theoretical cosmology tools (CAMB)
