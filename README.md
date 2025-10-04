# CFD Arrow Visualization for Butterfly Simulations in Grasshopper

This repository solves a common challenge in **CFD simulations with Butterfly** — exporting and baking **velocity vector arrows** from Grasshopper to Rhino for clear and customizable visualization.

The workflow combines **Butterfly CFD simulation results**, **Grasshopper scripting**, **Python automation**, and the **Human plugin** to produce editable 3D arrows representing flow direction and magnitude.

---
![Uploading image.png…]()

## 🔍 Overview

CFD airflow vectors are usually visualized inside Grasshopper but not directly exportable to Rhino as editable geometry.  
This project provides a solution with **two types of vector arrow generators** for post-processing and presentation:

1. **Cylinder + Cone arrows** for solid 3D representation.  
2. **Line + Polyline arrows** for lightweight visualization with simple arrowheads.

---

## ⚙️Components / Python GH Scripts

### 1. Vector Arrow Generator (Cylinder + Cone) — `vector_arrow_generator_cfd.py`
- Converts CFD vectors (`V`) into Rhino **cylinders (shaft)** and **cones (arrowhead)**.  
- Produces solid 3D arrows suitable for visual presentation or detailed modeling.  
- Works with Grasshopper’s GhPython component.  

**Inputs:**  
- `P` (points), `V` (vectors), `radius` (shaft radius), `cone_height`, `cone_radius`  

**Outputs:**  
- `final_cyl` (shaft Breps), `final_cone` (arrowhead Breps)

---

### 2. Vector Field Arrows (Line + Arrowhead) — `vector_field_arrows_line.py`
- Converts CFD vectors into **lines** with **triangle-shaped arrowheads**.  
- Lightweight alternative for quick visualization in Rhino.  
- Arrowhead size scales with vector magnitude.  

**Inputs:**  
- `P` (points), `V` (vectors)  

**Outputs:**  
- `lines`, `arrowheads` (lists of Rhino geometry representing arrows)

---

### 3. Brep & Color Baker — `CFD_brep_baker.py`
- Automates baking of **colored Breps** or surfaces into Rhino.  
- Assigns material colors using **Human plugin**.  
- Can be used in combination with arrow generators for colored CFD visualization.

**Inputs:**  
- `breps`, `colors`, `bake`  

**Outputs:**  
- Baked Breps in Rhino with assigned materials

---

## 🧠 Concept

The project explores **different methods for baking CFD data** from Grasshopper to Rhino:

- Visualize flow patterns directly in Rhino.  
- Control geometry type (line vs. solid arrow) and scale.  
- Automate post-processing tasks with Python scripting and the **Human plugin**.  

---

## 🧩 Requirements

- **Rhino 7 or 8**  
- **Grasshopper**  
- **Butterfly plugin** (OpenFOAM-based CFD)  for Simulation to create velocity vectors befor using this script
- **Human plugin** (for color/material baking)  
- **GhPython** component (for running scripts inside Grasshopper)  
- Optional: standalone `.py` files in `/Python-Scripts/` for versioning and GitHub language detection

---

## 🚀 Usage

1. Run CFD simulation using Butterfly in Grasshopper.  
2. Extract vectors (`P`, `V`).  
3. Use **Vector Arrow Generator** or **Vector Field Arrows** to create arrows in GhPython.  
4. Optionally, use **CFD_brep_baker.py** to bake colored Breps/surfaces into Rhino.  
5. Visualize and adjust arrow geometry and color in Rhino.
