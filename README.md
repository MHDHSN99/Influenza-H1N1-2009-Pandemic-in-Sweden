# Epidemic Simulation & Graph Coloring Optimization

This project implements discrete-time simulations on networks using two models:

1. A **networked SIR epidemic model**, simulating the spread of H1N1 on various graph structures (regular, preferential attachment).
2. A **graph coloring optimization**, minimizing interference in WiFi networks using probabilistic color updates driven by Gibbs sampling.

---

## Part 1: Epidemic Simulation (H1N1 in Sweden)

### Overview
A discrete-time SIR model simulates the spread of H1N1 over 15 weeks using two network topologies:
- Symmetric k-regular graph
- Preferential attachment graph

### Key Concepts
- Infection spread with probability **β**
- Recovery with probability **ρ**
- Simulations averaged over 100 runs for robustness

### Features
- Tracks weekly susceptible, infected, recovered, and vaccinated nodes
- Includes simulation **with and without vaccination**
- Implements **parameter optimization (grid search)** to minimize RMSE with real-world H1N1 data

### Results
- Best-fit parameters:  
  `k = 8`, `β = 0.1`, `ρ = 0.4`  
- Achieved minimum RMSE = **7.90**

---

## Part 2: Graph Coloring Optimization

### Overview
Two coloring simulations minimize a **potential function** using a Gibbs sampling update rule:
1. **Line Graph (10 nodes)**: Binary colors (red, green)
2. **General Graph (100 routers)**: 8 frequency bands as colors

### Goal
Assign colors (channels) to nodes such that:
- No two adjacent nodes share the same (or similar) colors
- Potential (conflict cost) is minimized

### Features
- Stochastic update rule with decreasing noise η(t)
- Cost function varies by color difference
- Tested from both uniform and random initialization

### Results
- Line graph reaches optimal solution with potential = 0
- WiFi graph reaches near-optimal solution with potential in the range of **4–6**
- Random initialization shows smoother convergence

---

## Technologies Used

- Python
- NumPy
- NetworkX
- Matplotlib
- Discrete Markov chains, Gibbs sampling
- SIR model, vaccination strategy, RMSE fitting

---

## How to Run

```bash
# Clone the repo
git clone https://github.com/your-username/network-dynamics-coloring.git
cd network-dynamics-coloring

# Run simulation notebooks
jupyter notebook notebooks/Pandemic.ipynb
jupyter notebook notebooks/Coloring.ipynb
