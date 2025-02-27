# Description

The C++ code provided here has been used to simulate fluid flow in a two-dimensional DFN (Discrete Fracture Network) to study the spatial distribution of permeability in fault damage zones. The results of these simulations are presented in Bernier et al. (2025).  

This code was originally built to model electrical resistivity in DFNs. Please find the documentation attached. This code was then adapted to simulate permeability in our study.  

# Fluid flow  

Fluid only flows through the connected fractures by enforcing a unit pressure gradient from the left to the right side of the square domain. Permeability anisotropy is characterized by simulating fluid flow in this square for different angles of an entire rotation of the fracture network (Long et al., 1982).  

Fluid flow equations are solved by assuming steady-state and laminar flow, considering Stokes' equation at the fracture scale and mass conservation at the fracture nodes (e.g., Zimmerman and Paluszny, 2023). Consequently, fracture permeability is defined by the intrinsic law **b²/12**, where **b** is the fracture aperture (Snow, 1969).  

The equivalent hydraulic conductivity **K** (m/s) is determined from the flow rate on the right side of the domain by applying Darcy’s law (Darcy, 1856), and is then converted to equivalent permeability **k** (m²) as follows:  
**k = Kμ / ρg**,  
where:  
- **ρ** = 1000 kg/m³ (water density),  
- **g** = 9.81 m/s² (gravity intensity),  
- **μ** = 1.01 × 10⁻³ kg/(m·s) (water viscosity).  

The input parameters of flow simulations are the fracture coordinates, aperture, and hydraulic transmissivity, the latter being defined as:  
**T_f = (ρg/μ) * (b²/12)**,  
with **b** the fracture aperture.  

# How to perform a simulation?  

## Input  

### `DFN.txt`  
To perform a fluid flow simulation in a DFN, you first need to create a DFN text file (`DFN.txt`) containing the coordinates of your fractures.  

1. These coordinates must be in an **X-Y orthonormal system**, with an origin at (0,0).  
   - If your coordinates are georeferenced, adjust them to this system by **subtracting the lower X-coordinate from all X-values** and **subtracting the lower Y-coordinate from all Y-values**.  

2. To maintain the **real geometry** of a fracture network, fractures must often be discretized into multiple segments. Extract the coordinates of all nodes constituting each fracture.  

3. The first line of the `DFN.txt` file must specify **the number of segments** in the DFN.  

4. Each segment's **aperture** must be specified. See `Help_DFN.txt` for details on formatting.  

5. The **hydraulic transmissivity** of each segment must be defined as:  
   **T_f = (ρg/μ) * (b²/12)**,  
   where:  
   - **ρ** = 1000 kg/m³ (water density),  
   - **g** = 9.81 m/s² (gravity intensity),  
   - **μ** = 1.01 × 10⁻³ kg/(m·s) (water viscosity),  
   - **b** = segment aperture (m).  

### `DomainProperties.txt`  
This file defines the **size of the simulated area**.  

- The domain must be a **square**, so **X length = Y length**.  
- The first two lines of the file must specify these dimensions and must be the same.  
- Fractures must **intersect the square’s limits**.  
- Avoid defining a square size **larger than the fracture network area**, as this may distort results.  

### `Simu.txt`  
This file contains the **intrinsic parameters** of the simulation, such as:  
- The **calculation method**,  
- The **code used**,  
- The **number of rotations** to apply to the network.  

The number of rotations must be specified in **lines 3 and 4** (identical values).  

- The rotation parameter determines the number of simulations performed over a **full 360° anti-clockwise rotation** of the fracture network.  
- The fluid always flows from **west to east** (left to right).  
- The first simulation starts at **0°**, and the last is at **360°**.  

For example, if you want to simulate every **90°**, you must specify **5 rotations**.  

## Output  

The output contains:  
- The **hydraulic conductivity** and  
- Its corresponding **rotation angle** (in radians).  

To convert **hydraulic conductivity K (m/s) to permeability k (m²)**, use:  
**k = Kμ / ρg**,  
with the same **ρ**, **g**, and **μ** values as defined earlier.  

# How to cite this code?  

### For permeability simulation:  
To use this code for permeability simulation, please cite:  

> Bernier, L., Soliva, R., Roubinet, D., Dominguez, S., Mayolle, S., Bulliard, M., Wibberley, C., & Korbar, T. (2025).  
> *Spatial distribution of permeability in carbonate fault damage zones.*  
> Journal of Structural Geology, **194**, 105371.  
> [https://doi.org/10.1016/j.jsg.2025.105371](https://doi.org/10.1016/j.jsg.2025.105371)  

### For electrical resistivity simulation:  
To use this code for electrical resistivity simulation, please refer to `Documentation.pdf` and cite:  

> **Caballero-Sanz et al. (2017)**  
> Caballero-Sanz, V., Roubinet, D., Demirel, S., & Irving, J. (2017).  
> *2.5D discrete-dual-porosity model for simulating geoelectrical experiments in fractured rock.*  
> Geophysical Journal International, **209**(2), 1099-1110.  
> [https://doi.org/10.1093/gji/
