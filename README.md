
Advance Maths

## Overview
This project is an implementation of a Roll-Number-Parameterized Non-Linear Model to learn Probability Density Functions (PDF). The assignment involves transforming air quality data (`NO2` levels) using a unique student identifier (Roll Number) and estimating the parameters of a specific Gaussian-based density function.

## Table of Contents
- [Dataset](#dataset)
- [Mathematical Model](#mathematical-model)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Usage](#usage)
- [Results](#results)

## Dataset
- **Source:** [India Air Quality Data (Kaggle)](https://www.kaggle.com/datasets/shrutibhargava94/india-air-quality-data)
- **File Required:** `data.csv`
- **Feature Used:** `no2` (Nitrogen Dioxide)

## Mathematical Model

### 1. Data Transformation
The feature $x$ (NO2) is transformed into $z$ using the following non-linear equation:

$$z = x + a_r \sin(b_r x)$$

Where $a_r$ and $b_r$ are derived from the University Roll Number ($r$):
- $a_r = 0.05 \times (r \mod 7)$
- $b_r = 0.3 \times ((r \mod 5) + 1)$

### 2. Probability Density Function (PDF)
We fit the transformed data to the target function:

$$\hat{p}(z) = c \cdot e^{-\lambda(z-\mu)^2}$$

The parameters are estimated using statistical moments (Mean and Variance):
- $\mu$: Mean of the transformed data $z$.
- $\lambda$: Derived from variance ($\lambda = \frac{1}{2\sigma^2}$).
- $c$: Normalization constant ($c = \frac{1}{\sqrt{2\pi\sigma^2}}$).

## Prerequisites
The project requires **Python 3.x** and the following scientific computing libraries:
* `pandas`
* `numpy`
* `matplotlib`

## Installation

1.  Clone this repository or download the project files.
2.  Install the required dependencies:
    ```bash
    pip install pandas numpy matplotlib 
    ```
3.  Ensure the dataset `data.csv` is placed in the root directory.

## Usage

1.  **Update Roll Number:**
    Open the main script (or notebook) and locate the variable `r`. Replace the placeholder with your actual University Roll Number:
    ```python
    r = 102317250
    ```

2.  **Run the Script:**
    Execute the Python script to perform the transformation and parameter learning.

    ```bash
    DS_Statistics_A2.ipynb
    ```

## Results
The script outputs the learned parameters required for submission:
1.  **$\lambda$ (Lambda)**
2.  **$\mu$ (Mu)**
3.  **$c$ (Constant)**

It also generates a histogram visualization overlayed with the predicted probability density curve to validate the fit.
