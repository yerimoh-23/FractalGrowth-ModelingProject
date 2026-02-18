# Models of Fractal Growth Simulation

- Yerim Oh
- Supervisor: Kenneth Mulder

## Project Overview
This project develops agent-based simulation models to analyze fractal growth dynamics under varying environmental parameters.

The primary objective was to generate structured simulation datasets and evaluate how parameter variation influences aggregation patterns, structural formation, and overall system variability.

Rather than focusing solely on theoretical modeling, this project emphasizes quantitative analysis of simulation outputs and parameter sensitivity.

### Model Overview
These models are implementations of fractal geometry and network theory, which is a modified version of the Triangular Growth Model (TGM) by Professor. Mulder, to understand the fractal patterns in absorptive polymers. Fractal growth processes are a class of phenomena that produce self‐similar, disordered objects in the course of development far from equilibrium.

### Modeling Approach
* Built agent-based growth models in NetLogo
* Implemented boundary-driven and centroid-driven growth mechanisms
* Simulated large-scale systems (up to 20,000 particles per run)
* Automated parameter sweeps using BehaviorSpace
* Generated structured output data for comparative evaluation

![Alt text](https://github.com/yerimoh-23/FractalGrowth-ModelingProject/blob/main/Images/Coalescing.png)


## Idea
The idea of these models is the combination of the original TGM’s triangular network and the Coalescing model. During the growth step, selected particles have the chance to bond with the nearest particle. Among those, selected bonds can connect to the nearest particle in the bond range and experience contraction in the direction of the links. The nearest particle is chosen by the effect of the solvent flow how much it is close to the center and also within the bond range.

![Alt text](https://github.com/yerimoh-23/FractalGrowth-ModelingProject/blob/main/Images/ModelProcess.png)

## Experimental Design
Key parameters tested:
- **Probability of bonding** (bond-rate): Probability that an active link seeks to bond to a new particle each time step
- **Probability of initial bonding** (initiation-rate): Probability of an unbonded particle to create a new active link each time step
- **Mobility period** (mobility): Number of time steps after bonding during which a particle experiences contraction
- **Effect of the solvent flow** (flow-effect): Directional effect of solvent flow upon bonding
- **Rate of the solvent drying** (drying-rate): Rate at which the solvent on the disk recedes
  - In the model setting, this is equal to [zone-speed]
- **Particle density** (density): Average density of particles per square unit
- **Maximum bonding distance** (bond-range): Maximum average distance to the endpoints of a link for a particle to be able to bond to the link

Each parameter configuration produced reproducible structural outputs for systematic comparison across conditions.

## Analytical Focus
The analysis concentrated on:
- Parameter sensitivity evaluation
- Structural aggregation patterns
- Fractal branching behavior
- Directional asymmetry effects
- Stability and convergence characteristics

Simulation outputs were compared across parameter combinations to identify consistent behavioral trends and nonlinear effects.

## Model Variants
The project includes multiple growth configurations designed to simulate different environmental conditions:

#### Outer Boundary Growth Model
- Boundary-driven aggregation toward the center
  ![Alt text](https://github.com/yerimoh-23/FractalGrowth-ModelingProject/blob/main/Images/OuterTGMnew.png)

#### Directional Flow Model (Horizontal)
- Growth influenced by lateral drying dynamics
  ![Alt text](https://github.com/yerimoh-23/FractalGrowth-ModelingProject/blob/main/Images/TGMS.png)

#### Multi-Centroid Growth Model
- Voronoi-based region separation with competing growth centers
  ![Alt text](https://github.com/yerimoh-23/FractalGrowth-ModelingProject/blob/main/Images/TGMC_Voronoi.png)

Each model shares a common bonding mechanism but differs in spatial growth constraints and environmental influence.

## Key Insights
- Higher bond rates increased cluster density while reducing branching variability.
- Directional flow effects introduced measurable asymmetry in growth patterns.
- Multi-centroid growth produced Voronoi-like structural boundaries.
- Mobility duration influenced contraction intensity and final cluster compactness.

These findings demonstrate how localized interaction rules scale into emergent structural behavior.

## Tools & Methods
- NetLogo (Agent-Based Modeling)
- BehaviorSpace (Automated Parameter Sweeps)
- Quantitative Output Evaluation
- ImageJ (Post-processing & Binarization)

