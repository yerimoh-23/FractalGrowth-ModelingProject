# Models of Fractal Growth with Application to Adsorptive Polymers

- Yerim Oh
- Supervisor: Kenneth Mulder

This document summarizes the models I developed over the past year, including their structure, differences from base models, associated BehaviorSpace experiments, and any follow-up analysis conducted. It serves as a reference to quickly locate models and outputs.

## Model Overview
These models are implementations of fractal geometry and network theory, which is a modified version of the Triangular Growth Model (TGM) by Professor. Mulder, to understand the fractal patterns in absorptive polymers. Fractal growth processes are a class of phenomena that produce self‐similar, disordered objects in the course of development far from equilibrium. The models explores how polymers behave under different drying techniques.

## Objective
Thin films are produced by various polymer solvents. Depending on how the solvent dries—whether through spin coating, or horizontal or vertical air drying—the films develop different structural and physical characteristics. Under certain conditions, polymers aggregate into diffuse structures with a fractal dimension. The specific processes are complex and not well understood because producing films happens quickly, and because they are tiny. However, it is important to materials science that we understand the relationship between fractal characteristics and other material properties.

### Problem we aim to address:
1. The polymer fractals grow from the outside-in.
2. Based on how the solvent is dried, the structure of the films are different.

## Earlier Models (Summer 2024, FA 2024)
1. **Outer TGM old**
2. **Coalescing Model**

### Coalescing Model
- **Folder:** `02_Coalescing`
- **Description:** The model starts with the particles around the boundary, and each particle forms a bond with the closest particle. At each iteration, these bonds link with the new particles. Bond formation stops once all the links merge into a single structure.
- **Distinction from base model:** It does not imply the triangular networks as the bonds are created.
- **Model file:** `Coalesce.nlogo`
  
![Alt text](https://github.com/yerimoh-23/FractalGrowthModels-AdsorptivePolymers/blob/master/Image/Coalescing.png)


## Current Models
Mixed the method of this coalescing model and the triangular network from the TGM to build our current models
1. **Outer TGM (new)**; for the spin-coating polymers
2. **TGMS**; for the horizontal air blowing technique
3. **TGMC**; for the vertical air blowing technique

### Idea
The idea of these models is the combination of the original TGM’s triangular network and the Coalescing model. During the growth step, selected particles have the chance to bond with the nearest particle. Among those, selected bonds can connect to the nearest particle in the bond range and experience contraction in the direction of the links. The nearest particle is chosen by the effect of the solvent flow how much it is close to the center and also within the bond range.

![Alt text](https://github.com/yerimoh-23/FractalGrowthModels-AdsorptivePolymers/blob/master/Image/ModelProcess.png)

### Parameters
- **Probability of bonding** (bond-rate): Probability that an active link seeks to bond to a new particle each time step
- **Probability of initial bonding** (initiation-rate): Probability of an unbonded particle to create a new active link each time step
- **Mobility period** (mobility): Number of time steps after bonding during which a particle experiences contraction
- **Effect of the solvent flow** (flow-effect): Directional effect of solvent flow upon bonding
- **Rate of the solvent drying** (drying-rate): Rate at which the solvent on the disk recedes
  - In the model setting, this is equal to [zone-speed]
- **Number of Particles** (num-particles): Nember of particles on the disk
- **Particle density** (density): Average density of particles per square unit
- **Maximum bonding distance** (bond-range): Maximum average distance to the endpoints of a link for a particle to be able to bond to the link

### Outer TGM
- **Folder:** `05_OuterTGM`
- **Description:** The model is based on the spin-coating polymer films. The disk of the model becoming grey represents the solvent drying from the outside. After all the bonds are connected into a mass and experience contraction, the model saves the output as an image file.
  - `setup`: Set world parameters, the particles, and the parameters
  - `go`: At each iteration, these bonds link with the new particles. Bond formation stops once all the links merge into a single structure.
- **Distinction from base model:** Bonds form from the boundary of a circular disk and grow toward the center, where they connect.
- **Model file:** `OuterTGM (2).nlogo`

![Alt text](https://github.com/yerimoh-23/FractalGrowthModels-AdsorptivePolymers/blob/master/Image/OuterTGMnew.png)

### TGMS
- **Folder:** `06_TGMS`
- **Description:** The model is to observe how the polymers grow as the solvent is dried from the side by blowing air horizontally. The disk of the model becoming grey represents the solvent drying from the left side. After all the particles are connected into bonds and experience contraction, the model saves the output as an image file.
  - `setup`: Set world parameters, the particles, and the parameters
  - `go`: At each iteration, these bonds link with the new particles. Bond formation stops once all the bonds link to bonds.
- **Distinction from base model:** It is based on the same idea as the Outer TGM, but the solvent is dried from the left side.
- **Model file:** `TGMS (1).nlogo`

![Alt text](https://github.com/yerimoh-23/FractalGrowthModels-AdsorptivePolymers/blob/master/Image/TGMS.png)

### TGMC
- **Folder:** `07_TGMC`
- **Description:** The model is based on the vertical air blowing technique. The disk of the model becoming grey represents the solvent start to dry from different centroids. After all the bonds are connected into a mass and experience contraction, the model saves the output as an image file.
  - `setup`: Set world parameters to achieve correct sizes
  - `place-centers`: Click the coordinates to set the centroids you want
  - `particles`: Based on the centeroids, set the particles and their parameters
  - `go`: At each iteration, these bonds link with the new particles. Bond formation stops when the ticks became 1000.
- **Distinction from base model:** Previous films had one centroid with all the branches connected to it, or no centers for the horizontal air blowing. However, this film has several centroids, and each has boundaries that separate the bonds from one another. The branches grow the same way as the Outer TGM and the TGMS, but start to form bonds from the centroids. However, the condition for the bonds to stop growing is when they meet with the bonds from the other centroid.
  - The model is based on the Voronoi diagram, which divides space into regions based on distance to a set of points in a plane. Each region contains all space that is closer to one point than any other point. Which means that the border of the two regions would have the same distance from the two points of those regions.
- **Model file:** `TGMC Voroni.nlogo`

![Alt text](https://github.com/yerimoh-23/FractalGrowthModels-AdsorptivePolymers/blob/master/Image/TGMC_Voronoi.png)

- still developing this model

### Files
- `MATH-395 Independent Studies/`: All `.nlogo` files are in the Google Drive
- `BS******/`: All image outputs from BehaviorSpace runs are stored in each folder of the models named by the date runned
- `ImageProcess_Crop/`: All outputs after image processing
- `README.md`: This file

## BehaviorSpace Experiments
First, try the below parameters and adjust the parameter for future behavior space.

### Outer TGM
- Bond rate: 0.05, 0.1, 0.3, 0.5
- Initiation rate: 0.05, 0.1, 0.3, 0.5
- Mobility: 100, 300, 500
- Flow effect: 0.1, 0.5, 0.9
- Zone speed: 0.1, 0.5, 0.9
- Bond range: 1.0, 2.0, 3.0
- Density: 1.0, 2.0, 3.0
- N-particles: 20000

### TGMS
- Bond rate: 0.05, 0.1, 0.3, 0.5
- Initiation rate: 0.05, 0.1, 0.3, 0.5
- Mobility: 100, 300, 500
- Flow effect: 0.1, 0.5, 0.9
- Zone speed: 0.1, 0.5, 0.9
- Bond range: 1.0, 2.0, 3.0
- Density: 1.0, 2.0, 3.0
- N-particles: 20000

### TGMC
- Bond rate: 0.05, 0.1, 0.3, 0.5
- Initiation rate: 0.05, 0.1, 0.3, 0.5
- Mobility: 100, 300, 500
- Flow effect: 0.1, 0.5, 0.9
- Zone speed: 0.1, 0.5, 0.9
- Bond range: 1.0, 2.0, 3.0
- Density: 1.0, 2.0, 3.0
- N-particles: 20000

## Image Processing
- **Tool used:** ImageJ
- **Purpose:** Make binary and crop (scale if needed)

### Binarize images
run("Options...", "iterations=1 count=1 black");
run("8-bit");
setAutoThreshold("Default");
//run("Threshold...");
//setThreshold(“Default”);
setOption("BlackBackground", true);
run("Convert to Mask");

### Crop images
makeRectangle(100, 800, 700, 400);
run("Crop");

**for TGMC**
scale = 0.633;
w = getWidth*scale; h=getHeight*scale;
run("Size...", "width=w height=h interpolation=Bilinear");

