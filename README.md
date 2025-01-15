# Brusselator Chemical Reaction Simulator

## Overview
This project implements a sophisticated simulation of the Brusselator chemical reaction system using both stochastic (Monte Carlo) and deterministic (ODE) approaches. The Brusselator is a theoretical model for a type of autocatalytic reaction, demonstrating oscillatory behavior and serving as a classic example of chemical pattern formation.

## Last Modified 
Last Modified: [28/11/2023]

## Mathematical Background

### The Brusselator Model
The Brusselator model consists of four elementary reactions:
```
A → X        (rate constant k₁)
B + X → Y + D  (rate constant k₂)
2X + Y → 3X    (rate constant k₃)
X → E          (rate constant k₄)
```

### Deterministic Approach (ODEs)
The system is described by the following coupled ordinary differential equations:

```
dX/dt = k₁A - k₂BX + k₃X²Y - k₄X
dY/dt = k₂BX - k₃X²Y
```

Where:
- X and Y are the concentrations of the intermediate species
- A and B are constant concentrations of the input species
- k₁, k₂, k₃, k₄ are rate constants

### Stochastic Approach (Monte Carlo)
The Monte Carlo simulation implements the Gillespie algorithm, which:
1. Calculates propensity functions for each reaction
2. Determines the time until the next reaction
3. Probabilistically selects which reaction occurs
4. Updates the system state accordingly

## Features
- Monte Carlo simulation using the Gillespie algorithm
- Numerical ODE solver using SciPy's `solve_ivp`
- Parameter fitting capabilities
- Comparative visualization of both approaches
- Multiple simulation runs with statistical analysis

## Dependencies
- NumPy: For numerical computations
- Matplotlib: For visualization
- SciPy: For ODE solving and optimization

## Installation
```python
pip install numpy matplotlib scipy
```

## Usage

### Basic Simulation
```python
# Import the required modules
import numpy as np
import matplotlib.pyplot as plt
from scipy.integrate import solve_ivp

# Run Monte Carlo simulation
t, X = brusselator_MC([1000, 2000], 14, 1)

# Run ODE simulation
T_ODE, X_ODE = brusselator_ODE([1, 2], 19, 9.5, 38, 13, 21)
```

## Key Parameters
- Initial concentrations (X0)
- Simulation time (Tfinal)
- Rate constants (k₁, k₂, k₃, k₄)
- Number of simulation runs

## Output
The simulation provides:
1. Time series data for species X and Y
2. Phase space trajectories
3. Comparative plots between Monte Carlo and ODE approaches
4. Statistical measures of system behavior

## Limitations
1. Current implementation assumes well-mixed conditions
2. Computational intensity increases with molecule numbers
3. Fixed rate constants throughout simulation
4. No spatial considerations

## Future Improvements

### Functionality
1. Add support for:
   - Temperature dependence of rate constants
   - Spatial heterogeneity
   - Additional reaction mechanisms
2. Implement adaptive time stepping for ODE solver
3. Add parallel processing for multiple runs
4. Include sensitivity analysis tools
5. Add statistical analysis package

### Visualization
1. Create interactive plots using Plotly
2. Add real-time simulation visualization
3. Implement 3D phase space plots
4. Add concentration distribution histograms
5. Create animation capabilities

## Author
Rafael Hajjar

## References
1. Prigogine, I., & Lefever, R. (1968). Symmetry Breaking Instabilities in Dissipative Systems II
2. Gillespie, D. T. (1977). Exact Stochastic Simulation of Coupled Chemical Reactions



---
*Note: This README is a living document and will be updated as the project evolves.* 