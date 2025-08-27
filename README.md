# LQG Volume Operator Spectral Analysis

This repository contains scripts and tools for computing and analyzing the spectrum of the Loop Quantum Gravity (LQG) volume operator and its kernel (zero-volume) states. The computations and reported counts below reflect the sampling and parameter ranges used by the included scripts; they are not exhaustive proofs of global properties.

**📖 [View the complete research documentation on GitHub Pages](https://arcticoder.github.io/lqg-volume-kernel-catalog/)**

## Repository Name

**lqg-volume-kernel-catalog**

## Description

Scripts to:
- Compute the LQG volume operator spectrum via SU(2) 12j-symbols.
- Identify trivial and non-trivial zero-volume states for 4-valent nodes.
- Analyze kernel dimensions of the volume-squared matrix.
- Generate LaTeX tables and figures summarizing results.
- Validate the Diophantine characterization of zero-volume states.

## Topics

`loop-quantum-gravity` `volume-operator` `quantum-gravity` `su2` `recoupling-theory` `12j-symbols` `latex`

## Requirements

See `requirements.txt` for dependencies:
```bash
pip install -r requirements.txt
```

## Usage

### 1. Analyze Zero-Volume States (4-valent)

```bash
python scripts/analyze_zero_volume_states.py
```
- Scans a specified spin-configuration range (default j=0.5 to 3.0). Adjust the script arguments to explore other ranges.
- Identifies trivial zero-volume states under the tested sampling and criteria (J₁₂ ∩ J₃₄ = ∅ where applicable).
- Reports that no non-trivial zero-volume states were found within the tested range and parameter sweep; this is an empirical result for the scanned configurations (not a mathematical proof of absence).
- Outputs summary statistics and generates:
  - `results/kernel_dimension_distribution.png`
  - `results/zero_volume_catalog.json`

### 2. Generate LaTeX Table of Trivial Zero-Volume States

```bash
python scripts/generate_latex_table.py
```
- Produces `results/trivial_zero_volume_table.tex` with a single-column summary of trivial zero-volume cases.

### 3. Create Spin-1/2 Correlation Placeholder Figure

```bash
python scripts/generate_spin_half_correlation.py
```
- Generates `results/figures/spin_half_correlation.png` showing the absence of non-trivial kernel states.

### 4. Generate Volume Spectrum (Optional)

```bash
python scripts/compute_volume_spectrum.py
```
- Computes eigenvalues of the volume-squared operator for specified spin configurations.
- Outputs to `data/volume_spectrum.csv`.

## Results

- **Total configurations scanned (example run)**: 1,296 (default j_i ∈ {0.5, 1.0, …, 3.0}) — changeable via script arguments.
- **Trivial zero-volume states (example run)**: 60 (≈4.6%) — fraction observed in the example sweep; varies with sampling.
- **Non-trivial zero-volume states (example run)**: 0 observed in the example sweep (empirical result in the tested parameter range).
- **Full-rank matrices (example run)**: 674 (≈52.0%) — reported for the example sweep.
- **Other kernel matrices (example run)**: 562 (≈43.4%) — reported for the example sweep.

All trivial zero-volume cases in the example sweep satisfy the Diophantine condition for the tested configurations:

```
max(|j₁−j₂|, |j₃−j₄|) > min(j₁+j₂, j₃+j₄)
```

## Scope, Validation & Limitations

- Scope: example numerical scans of the LQG volume operator kernel for 4-valent nodes within user-configurable spin ranges. Results are empirical and dependent on the sampled range and discretization.
- Validation: run `python scripts/analyze_zero_volume_states.py --help` to see runtime options. To reproduce example results, run the script with the default parameters and attach the generated `results/` artifacts.
- Limitations: the scripts perform finite, discrete scans. Absence of a configuration in the sampled set does not constitute a mathematical proof of absence. For broader claims, increase sampling density, include symbolic checks where possible, and provide reproducibility artifacts.

## Directory Structure

```
├── scripts/
│   ├── analyze_zero_volume_states.py
│   ├── generate_latex_table.py
│   ├── generate_spin_half_correlation.py
│   ├── compute_volume_spectrum.py
│   └── ...
├── results/
│   ├── trivial_zero_volume_table.tex
│   ├── zero_volume_catalog.json
│   ├── kernel_dimension_distribution.png
│   └── figures/
│       └── spin_half_correlation.png
├── data/
│   └── volume_spectrum.csv
├── README.md
└── requirements.txt
```
