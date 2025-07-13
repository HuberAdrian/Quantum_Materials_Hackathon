# Quantum-Accelerated SCF-DFT Simulation Using QSVT and QCBM

## 🌍 Vision and Social Impact

This project was developed as part of the [Hackathon Initiative – Team 6], aiming to explore how cutting-edge quantum computing tools can be harnessed to create **technologies for the public good**.

Our simulation platform is a **technical proof-of-concept** that connects **quantum machine learning** and **computational chemistry** to potential real-world use cases such as:
- **Designing new sustainable materials**
- **Modeling electronic behavior for next-gen electronics**
- **Accelerating scientific discovery with fewer resources**

By democratizing access to quantum-accelerated simulation tools and integrating intuitive quantum–classical workflows, we contribute to building a **more inclusive and future-ready computational science toolkit**.

---

## 📘 Overview

This project implements and extends the methodology described in:

> **"Quantum-Accelerated Self-Consistent Field Method for Real-Space DFT Using QSVT"**  
> *Mohamed Lamane et al., arXiv:2307.07067*  
> https://arxiv.org/abs/2307.07067

We reproduce the core framework of the paper and expand it by:
- Integrating **generative quantum circuits (QCBMs)**,
- Estimating **conductivity via DOS**,
- Structuring it into a Colab-friendly, educational platform.

---

## 🎯 Objective

Our primary technical goals are:
- Simulate a real-space self-consistent field (SCF) loop for DFT,
- Approximate the Fermi–Dirac function \( f(H) \) using Chebyshev polynomials (QSVT-inspired),
- Compute electron densities iteratively until convergence,
- Estimate material conductivity via the density of states (DOS),
- Generate and benchmark candidate densities using a **Quantum Circuit Born Machine (QCBM)**.

---

## 🧪 Methods Implemented

### 1. Molecular Hamiltonian Construction
- Built using `pennylane.qchem.Molecule`
- Basis set: STO-3G
- Supports both test cases (e.g., LiH) and complex systems (e.g., Cu₂–C₆)

### 2. QSVT-Inspired Fermi–Dirac Filtering
- Approximates:
  \[
  f(H) = \frac{1}{1 + e^{\beta(H - \mu)}} \approx \sum_k c_k T_k(H)
  \]
- Chebyshev polynomials are used to simulate QSVT filtering in a classical setting

### 3. Self-Consistent Field (SCF) Loop
- Uses filtered density to update the Hamiltonian iteratively
- Simple local potential \( V[n] = \alpha \cdot \text{diag}(n) \) is used for updating \( H[n] \)
- Loop terminates when density change falls below a threshold

### 4. Quantum Circuit Born Machine (QCBM)
- 4-qubit variational quantum circuit (VQC) with entanglement and rotation layers
- Produces synthetic densities for benchmarking or future inverse-design tasks

### 5. Density of States (DOS) and Conductivity
- Eigenvalue histogram of \( H[n] \) used to estimate DOS
- Conductivity is approximated by evaluating:
  \[
  \sigma \propto g(E_F)
  \]
  where \( g(E_F) \) is the DOS at the Fermi level

---

## 🔁 Workflow Summary

```text
[Input Geometry]
      ↓
[Build Hamiltonian H₀]
      ↓
[Apply Chebyshev Filter f(H)]
      ↓
[Extract Density n(rⱼ)]
      ↓
[Update H[n]] → repeat until convergence
      ↓
[Estimate DOS & Conductivity] + [QCBM Sampling for Comparison]
````

---

## 📊 Results

* Visual and numerical comparison of QSVT-SCF-derived density vs QCBM-generated samples
* Density of States (DOS) plots for conductivity inference
* Demonstrated convergence of SCF loop in 5–20 iterations for various systems

---

## 📂 File Structure

```
├── main_notebook.ipynb        # Full simulation pipeline (Colab-compatible)
├── README.md                  # Project documentation
└── data/
    └── cached_H.npy           # Optional: saved Hamiltonians for faster reruns
```

---
## 🎥 Presentation

You can view the full presentation here:  
https://www.canva.com/design/DAGs1gttXeY/EdGxj6zRi65g-7BG9pG0Aw/edit?utm_content=DAGs1gttXeY&utm_campaign=designshare&utm_medium=link2&utm_source=sharebutton

---

## 📚 References and Related Work

1. **Lamane *et al.* (2023)** – *Quantum-Accelerated SCF for DFT via QSVT*.  
   [`arXiv:2008.06449`](https://arxiv.org/pdf/2008.06449)

2. **Pix2Pix–YOLOv7 with mmWave Radar for Object Detection** – *RSC Advances* (2023).  
   [Link](https://pubs.rsc.org/en/content/articlehtml/2023/ra/d3ra01982a)

3. **QML-Accelerated Real-Space DFT** – *Applied Sciences*, **14**(20), 9273 (2024).  
   [MDPI](https://www.mdpi.com/2076-3417/14/20/9273)

4. **Quantum-Enhanced Electronic Structure Modelling** – *Magnetic Resonance in Chemistry* (2024).  
   [Wiley Online Library](https://onlinelibrary.wiley.com/doi/full/10.1002/mgea.73)

5. **Ko *et al.* (2023)** – *DFT on Quantum Computers with Linear Scaling w.r.t. Number of Atoms*.  
   [`arXiv:2307.07067`](https://arxiv.org/pdf/2307.07067)

6. **Gorsse *et al.* (2023)** – *Mechanical Properties and Electrical Conductivity of Copper-Based Alloys*.  
   *Scientific Data*, **10**, Article 504.  
   [Nature](https://www.nature.com/articles/s41597-023-02411-9)

7. **World Bank (2025)** – *Electric power transmission and distribution losses (% of output)*.  
   [World Bank Indicator EG.ELC.LOSS.ZS](https://data.worldbank.org/indicator/EG.ELC.LOSS.ZS)

8. **United Nations (2015)** – *Sustainable Development Goals (SDGs)*.  
   [UN SDGs](https://sdgs.un.org/goals)

## 🧠 Credits

This work was developed as part of a hackathon initiative (Team 6), with the broader goal of empowering researchers, educators, and developers to integrate quantum acceleration into real-world scientific simulations — from materials discovery to energy systems.

We are committed to **accessible, interpretable, and ethically-aligned quantum computing**.

