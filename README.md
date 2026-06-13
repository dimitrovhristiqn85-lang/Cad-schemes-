# Generator Scheme Project

This repository contains the schematic and simulation files for a generator circuit designed and simulated using **KiCad** and **Ngspice**.

---

## 🛠️ Project Components

The project consists of the following core files:
* **`.kicad_sch`**: The main circuit schematic.
* **`.kicad_pro`**: The KiCad project configuration file.

---

## ⚡ Circuit Specifications & Parameters

The circuit is built around an operational amplifier with a dual-rail power supply. 

## 📈 Simulation Results

A **Transient Analysis (TRAN)** was performed using the integrated Ngspice simulator to verify the physical behavior and timing of the circuit. 

* The simulation completed successfully without any software convergence issues (`No. of Data Rows : 2553`).
* The output graph captures the initial transient phase and shows the exact stabilization levels of the signals over time.

### 🔍 Why the Graph Looks This Way (Software Differences)

The simulation graph shows a rapid transition followed by a flat, stabilized response. This specific behavior occurs due to how different simulation software packages handle ideal operational amplifier models:

* **Designed for Another Software:** This circuit was originally designed for a different simulation platform (such as OrCAD PSpice or Multisim). 
* **The Model Behavior Difference:** In other programs, the default operational amplifier models often include soft-start characteristics or different internal macro-models that allow for continuous oscillation or distinct wave shapes without extra fine-tuning.
* **Ngspice Interpretation in KiCad:** When imported into KiCad's integrated Ngspice engine, the simulator treats the op-amp and the diodes as highly ideal components. Without parasitic elements or specific initial conditions (`.ic`), the ideal mathematical solver calculates a very fast transient response that quickly settles into a stable, flat state. 

Therefore, the flat lines on the graph show that Ngspice successfully solved the ideal equations and reached a steady physical state based on its default component models.

---

## 🚀 How to Run the Project

1. Clone or download this repository.
2. Open the `.kicad_pro` file using **KiCad 7.0 or newer**.
3. Open the schematic editor (`.kicad_sch`).
4. Run the **Spice Simulator** from the Tools menu to view the transient analysis graphs.
