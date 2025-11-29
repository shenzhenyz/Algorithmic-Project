# Smart Multimodal Mobility - Vehicle Routing Problem Optimization

[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## 📋 Project Overview

This project addresses the **Vehicle Routing Problem (VRP)** as part of ADEME's (French Environment and Energy Management Agency) call for innovative mobility solutions. The goal is to optimize delivery routes to reduce energy consumption and greenhouse gas emissions while managing logistical constraints in urban and suburban environments.

The project focuses on calculating optimal delivery routes on road networks, connecting multiple delivery points and returning to the starting depot while minimizing total travel time and considering real-world constraints.

## 🎯 Objectives

- **Primary Goal**: Develop a Python-based solver capable of handling large-scale instances (1,000+ cities)
- **Environmental Impact**: Reduce CO₂ emissions through optimized routing
- **Real-world Application**: Support various logistics operations (mail distribution, product delivery, waste collection)

## 🚀 Features

### Basic Version
- Route optimization for delivery networks
- Support for instances with several thousand cities
- Statistical performance analysis
- Benchmark validation using CVRPLIB

### Additional Constraints (2+ implemented)
Choose from the following constraints to make the model more realistic:

| Constraint | Basic Version | Advanced Version |
|------------|---------------|------------------|
| **Time Windows** | No delivery outside time window | Waiting allowed before opening |
| **Heterogeneous Fleet** | k identical trucks | 3D capacity + compatibility constraints |
| **Dynamic Traffic** | Constant travel time | Variable distance matrix per time slot |
| **Pickup Points** | Single depot | Multi-depot + object-specific constraints |

## 🛠️ Technical Stack

- **Language**: Python 3.8+
- **Key Libraries**:
  - `vrplib` - Benchmark instance management
  - `numpy` - Numerical computations
  - `matplotlib` - Visualization
  - `pandas` - Data analysis

## 📦 Installation

```bash
# Clone the repository
git clone https://github.com/yourusername/smart-mobility-vrp.git
cd smart-mobility-vrp

# Create virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt
```

## 🎮 Usage

### Basic Example

```python
import vrplib
from solver import solve_vrp

# Load instance
instance = vrplib.download_instance("X-n101-k25.vrp")

# Solve
solution = solve_vrp(instance)

# Evaluate performance
optimal_sol = vrplib.download_solution("X-n101-k25.sol")
gap = 100 * (solution["cost"] - optimal_sol["cost"]) / optimal_sol["cost"]
print(f"Gap vs reference: {gap:.2f}%")
```

### Running Experiments

```bash
# Run full experimental study
python experiments.py --instances A-n32-k5 X-n101-k25 M-n200-k17 --runs 20

# Generate performance reports
python analysis.py --output results/
```

## 📊 Performance Benchmarks

| Instance | Optimum Cost | Our Cost | Gap (%) | Time (s) |
|----------|--------------|----------|---------|----------|
| A-n32-k5 | 784 | 812 | 3.57% | 45.2 |
| X-n101-k25 | 27591 | 28995 | 5.09% | 182.7 |

**Target**: Average Gap < 7% on instances with < 200 customers

## 📁 Project Structure

```
smart-mobility-vrp/
├── notebooks/
│   ├── 01_modeling.ipynb          # Formal problem modeling
│   ├── 02_implementation.ipynb    # Algorithm implementation
│   └── 03_experimental_study.ipynb # Performance analysis
├── src/
│   ├── solver.py                  # Main VRP solver
│   ├── algorithms/                # Metaheuristic implementations
│   ├── constraints/               # Constraint handlers
│   └── utils.py                   # Helper functions
├── experiments/
│   ├── experiments.py             # Experimental design
│   └── analysis.py                # Statistical analysis
├── data/
│   └── instances/                 # Test instances
├── results/
│   ├── convergence/               # Convergence curves
│   └── statistics/                # Performance statistics
├── requirements.txt
└── README.md
```

## 🧪 Methodology

### 1. Formal Modeling
- Mathematical formulation of the VRP
- Complexity analysis (NP-hard problem)
- Constraint integration

### 2. Solution Approach
Choose one metaheuristic:
- **Simulated Annealing**
- **Tabu Search**
- **Adaptive Large Neighborhood Search (ALNS)**

### 3. Experimental Validation
- Test on growing instances (50 → 2000 clients)
- Generate convergence curves
- Statistical analysis (20 runs per instance)
- Comparison with CVRPLIB benchmarks

## 📈 Results & Analysis

The experimental study includes:
- **Convergence analysis**: Solution quality over iterations
- **Scalability study**: Performance on growing instance sizes
- **Statistical validation**: Boxplots showing solution distribution
- **Gap analysis**: Comparison with optimal/best-known solutions

## 🌍 Environmental Impact

This project contributes to:
- **Reduction of CO₂ emissions** through optimized routing
- **Fuel consumption optimization** via shorter travel distances
- **Traffic congestion reduction** through better route planning

## 👥 Contributors

This project was developed by the CesiCDP team in response to ADEME's call for innovative mobility solutions.

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🔗 References

- [CVRPLIB - VRP Benchmark Library](http://vrp.atd-lab.inf.puc-rio.br/index.php/en/)
- [vrplib Python Package](https://pypi.org/project/vrplib/)
- [PEP 8 Style Guide](https://www.python.org/dev/peps/pep-0008/)

## 📞 Contact

For questions or collaboration opportunities, please open an issue or contact the team.

---

**Note**: This project is part of an academic research initiative focused on sustainable transportation and logistics optimization.
