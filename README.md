# Quantum_Materials_Hackathon


# Quantum-Assisted Simulation of Copper–Carbon Materials

## Background

Understanding the electronic properties of novel materials is essential for developing efficient and sustainable technologies. However, simulating these properties—especially those that depend on quantum interactions like electrical conductivity—is computationally expensive. Classical methods such as Density Functional Theory (DFT) are accurate but scale poorly with system size, making them difficult to apply to large or complex materials systems.

## Project Overview

This project focuses on simulating and analyzing copper–carbon alloys using a quantum-assisted workflow. The goal is to estimate material properties such as conductivity by modeling how electrons behave in different atomic configurations. We target systems like graphene-doped copper and nanotube-like structures, where geometry and bonding can significantly affect electron flow. Our tool allows users to input atomic configurations and compute predicted properties with improved efficiency, using quantum subroutines to accelerate the most computationally intensive steps.

## Technical Implementation

We use a hybrid quantum–classical approach based on a simplified version of DFT:

1. **Hamiltonian Construction**: We build a single-particle Hamiltonian from the atomic positions of copper and carbon atoms. This includes kinetic energy and potential energy terms.
2. **Quantum Encoding**: Using Quantum Singular Value Transformation (QSVT), we apply a polynomial approximation of the Fermi–Dirac distribution to encode the occupied states of the system into a quantum state.
3. **Density Measurement**: We extract local electron densities via amplitude amplification. These measurements are used to update the electron density.
4. **Self-Consistent Field Iteration**: The algorithm updates the Hamiltonian based on the measured density and repeats until convergence.
5. **Property Estimation**: Once the electron density stabilizes, we estimate conductivity by analyzing the density of states near the Fermi level.

This method avoids full matrix diagonalization and achieves better scaling than classical DFT implementations.

## Future Work

We plan to expand this framework by incorporating quantum algorithms for spectral density estimation and by integrating classical or quantum optimization loops to search the alloy composition and structure space. Further development will include simulations of more complex nanostructures, such as carbon-doped copper nanotubes, and comparison of results with classical simulations or experimental data to validate accuracy and reliability.
