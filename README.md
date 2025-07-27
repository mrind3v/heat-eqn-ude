# Physics-Informed Machine Learning for the 1D Heat Equation Using Universal Differential Equations (UDEs)

This repository implements a physics-informed machine learning framework in Julia that models the **1D heat equation** by combining traditional numerical PDE methods with neural networks in the form of Universal Differential Equations (UDEs). It jointly learns the finite-difference stencil (spatial operator) and the diffusion coefficient (parameter) directly from simulated data, while enforcing key physical constraints like conservation of mass.

## Project Overview

The core idea is to replace the fixed finite-difference Laplacian operator by a **learnable convolutional stencil** and simultaneously discover the diffusion parameter **D** from data. This hybrid approach leverages the strengths of both scientific computing and neural network flexibility to build interpretable and physically consistent models of PDEs.

The repository includes:

- Detailed implementation of the 1D heat equation with periodic boundary conditions.
- A custom loss function encouraging physical constraints alongside data fitting.
- Visualization scripts creating heatmaps, line slice comparisons over time, and training loss curves.
- Comments and modular design for clarity and extensibility.


## Requirements

- Julia v1.6 or higher
- Recommended packages:
  - [DiffEqFlux.jl](https://github.com/SciML/DiffEqFlux.jl)
  - [DifferentialEquations.jl](https://github.com/SciML/DifferentialEquations.jl)
  - [Flux.jl](https://github.com/FluxML/Flux.jl)
  - [Plots.jl](https://github.com/JuliaPlots/Plots.jl)
  - [Optimisers.jl](https://github.com/FluxML/Optimisers.jl)

## Installation and Setup

1. Clone this repository:
   ```sh
   git clone https://github.com/your-username/heat-equation-ude.git
   
   cd heat-equation-ude
2. Activate the project environment and install dependencies from `Project.toml`:
   ```julia
    using Pkg
    Pkg.activate(".")
    Pkg.instantiate()


## Usage

- **Data Generation and Model Training**

The notebook or script files contain code to generate ground-truth data for the 1D heat equation, define and initialize the learnable model components (including kernels and diffusion coefficient), and train the Universal Differential Equation with a physics-informed loss function.

- **Prediction and Visualization**

After training, you can run the plotting script or cells to visualize:
- Heatmaps of ground truth vs model predictions over space and time.
- Line slice comparisons of solutions at selected time steps.
- Training loss curves on a logarithmic scale with physical constraint annotations.

## Code Structure

- **Cell 1:** Environment setup and package imports.
- **Cell 2:** Ground-truth data simulation using a finite-difference Laplacian.
- **Cell 3:** Neural network-like architecture for learnable finite difference stencil, with manual parameter reconstruction.
- **Cell 4:** Implementation of the Universal Differential Equation ODE function with periodic boundary conditions.
- **Cell 5:** Physics-informed loss function combining data fidelity and physical constraints.
- **Cell 6:** Training loop and results.
- **Cell 7:** Visualizations of results and training loss.

## Troubleshooting

- **DimensionMismatch Errors:**  
Ensure the manual `reconstruct_cnn` function is used instead of automatic Flux reconstruction to extract parameters correctly.

- **Missing Axis Labels in Plots:**  
Use the `bottom_margin` keyword with unit `mm` in Plots.jl (after importing `Plots: mm`) to add sufficient space for axis labels in combined layouts.

- **Diffusion Coefficient Not Learning:**  
Adjust the weights of physics constraint terms in the loss to prevent overpowering the data fitting term.

## Contribution

Contributions are welcome! Feel free to submit issues or pull requests to improve the model, add alternative PDE examples, or enhance visualization.



   

