# 🧊 CSC 380 – Homework 2: FrozenLake Reinforcement Learning  

**Author:** Gabrielle Boyer-Baker  
**Course:** CSC 380 – Artificial Intelligence, Fall 2025  
**Instructor:** Dr. Tomuro  
**Language:** Python (Gymnasium, NumPy, Matplotlib, Jupyter Notebook)

---

## 📘 Overview
This project explores **Reinforcement Learning** using the `FrozenLake-v1` environment from **Gymnasium**.  
It includes two main parts:

1. **Part 1 – Random Fixed Policies:**  
   Five random deterministic policies were generated and evaluated over 100 experiments of 10,000 episodes each to measure success rates and consistency.

2. **Part 2 – Value Iteration Algorithm:**  
   A dynamic programming approach was implemented to compute an optimal policy that maximizes expected reward using the full environment transition model (`env.unwrapped.P`).

---

## 🧩 Part 1: Random Policy Evaluation
- **Environment:** 8×8 Frozen Lake, slippery = True  
- **Trials:** 5 random seeds × 100 experiments × 10,000 episodes each  
- **Metrics:** mean goals, standard deviation, and mean steps-to-goal  

**Top 2 Performing Policies**

| Rank | Seed | Mean Goals | Stdev | Mean Steps-to-Goal |
|------|------|-------------|--------|---------------------|
| 🥇 1 | 123 | 87.89 | 8.45 | 61.91 |
| 🥈 2 | 17 | 23.29 | 5.05 | 52.79 |

The best policy (Seed 123) achieved high stability and success through safer directional patterns (frequent Down / Right actions).  
The weaker policy (Seed 17) demonstrated more randomness and higher failure rates by wandering into holes.

**Visualization Samples**
- `part1_top1_hist.png`  
- `part1_top2_hist.png`  
- `part1_top1_policy_grid.txt`  
- `part1_top2_policy_grid.txt`

---

## 🧠 Part 2: Value Iteration (Optimal Policy)
The **Value Iteration** algorithm was implemented with:  
- γ = 1.0 θ = 1e-4 (two-table convergence)  
- Initial V(s): small random non-zero values for non-terminal states  
- Transitions from `env.unwrapped.P`  

After convergence, the derived **optimal policy** achieved roughly **5153 successful episodes per 10,000**, a **58× improvement** over the best random policy.

**Optimal Policy Grid (8×8)**
3 2 2 2 2 2 2 2
3 3 3 3 3 3 3 2
0 0 0 0 2 3 3 2
0 0 1 0 0 2 2 2
0 3 0 0 2 1 3 2
0 0 1 3 0 0 2 2
0 0 2 0 0 0 2 2
0 1 0 0 1 2 1 0
*(0 = Left, 1 = Down, 2 = Right, 3 = Up)*  

**Optimal Value Table:** Values gradually increase toward the goal, showing higher rewards for safer, successful paths.

**Mean Goals:** 5152.8 **Stdev:** 53.5  

---

## 🌟 Reflection
This assignment gave me hands-on experience connecting reinforcement learning theory to real code.  
It was interesting to see how random deterministic policies can vary so much under stochastic conditions.  
The Value Iteration part was my favorite because it clearly demonstrated how the agent “learns” to move efficiently while avoiding danger.  

Running all 10,000-episode tests took around **21 minutes** on my MacBook Pro with an **M1 chip**, and it was rewarding to see everything converge smoothly after optimizing my setup.  
If I revisited this, I’d add progress bars, visualize the path dynamically, and experiment with different γ values.  
Overall, it made me appreciate how algorithms can turn randomness into structured, intelligent behavior.

---

## 📂 Files in This Repository
CSC380_HW2/
├── HW2_FrozenLake_Gabrielle.ipynb # Main Jupyter Notebook source
├── HW2_FrozenLake_Gabrielle.html # HTML export
├── HW2_Writeup_Gabrielle.pdf # Full write-up report
├── deliverables/ # Output grids & histograms
└── .gitignore # Excludes .venv and temp files

---

## ⚙️ Requirements
- Python 3.10+
- `gymnasium`
- `numpy`
- `matplotlib`
- `jupyter`

Install with:
```bash
pip install gymnasium numpy matplotlib jupyter
```
Run the notebook in VS Code or JupyterLab:
jupyter notebook HW2_FrozenLake_Gabrielle.ipynb
🏁 Acknowledgments
Environment: Gymnasium FrozenLake Documentation
Assignment prompt and example code by Dr. Naoyuki Tomuro, DePaul University
Student: Gabrielle Boyer-Baker

---

