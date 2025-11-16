# KADARIVENU_RISC-V_WEEK-7

 **Week 7 – BabySoC Physical Design & Post-Route SPEF Generation**

This week focuses on taking the **BabySoC** design through a **complete Physical Design (PD) flow** using **OpenROAD**, covering:

* Floorplanning
* Placement
* Routing
* Post-route parasitic extraction (SPEF)

This task integrates everything you learned from RTL → Synthesis → Early Layout into a full backend SoC flow.

---

## **📌 Objective**

To perform a complete physical implementation of the **BabySoC** using OpenROAD and generate accurate parasitics (SPEF) for timing analysis.

You will:

* Understand full RTL-to-GDSII physical design stages
* Learn how placement density & routing affect timing
* Generate and analyze post-route SPEF
* Validate layout completion and design quality

---

## **📂 Reference**

Use **Task 13** from the following repository for detailed commands:

**OpenROAD Physical Design Reference – Task 13**

---

# **🧩 Task Components**

---

## **1. BabySoC Floorplanning**

### Steps:

* Import synthesized BabySoC netlist
* Define floorplan parameters:

  * Die size
  * Core size
  * Core utilization
  * Aspect ratio
* Insert Power Rings and Straps
* Place all standard cells & macros inside the boundary

### Outputs:

* Floorplan screenshot
* Terminal logs

---

## **2. Placement**

### Steps:

* Run **Global Placement**
* Run **Detailed Placement**
* Verify cell density and legality
* Dump placement reports

### Outputs:

* Placement view screenshot
* Density report

---

## **3. Routing**

### Steps:

* Run **Global Routing**
* Run **Detailed Routing**
* Check for **DRC violations**
* Dump routing summary

### Outputs:

* Routed layout image
* Routing statistics

---

## **4. Post-Route SPEF Generation (Important)**

### Steps:

* Use OpenROAD’s built-in **RC extraction engine**
* Generate SPEF file for all nets
* Verify that parasitics (R/C) were extracted

### What SPEF Contains:

* Wire resistance
* Wire capacitance
* Coupling capacitance
* Net-to-net parasitic interactions

### Why SPEF Matters:

SPEF → Post-Route STA → Accurate delays & timing closure
(Post-route timing = Real wiring + real parasitics)

### Outputs:

* Terminal screenshot of SPEF generation
* Extracted SPEF file in repo

---

# **📘 Deliverables**

---

## **1. Screenshots / Images**

Include the following in your repo:

* ✔ Floorplan view
* ✔ Placement view
* ✔ Global + detailed routing view
* ✔ Terminal logs showing SPEF extraction

---

## **2. Documentation (README + Folder)**

Add in your repository:

* Step-by-step OpenROAD command summary
* Observations at each stage
* Issues faced and how they were resolved
* Explanation of SPEF and its importance in STA

---

## **3. Verification Note**

Summaries to be included:

* Total standard cell count
* Floorplan utilization
* Number of routed nets
* DRC count after routing (should be zero)
* Confirmation that SPEF was successfully generated

---

# **📝 Example OpenROAD Command Summary (for README)**

```bash
read_lef <path_to_tech_lef>
read_lef <path_to_stdcell_lef>
read_def <initial_def>

read_verilog soc.v
link_design soc

# Floorplan
initialize_floorplan -util 50 -aspect 1.0 -core_space 10

# Power Planning
add_global_connections ...
define_pdn_grid ...
pdngen

# Placement
global_placement
detailed_placement

# Routing
global_routing
detailed_routing

# SPEF Extraction
estimate_parasitics -placement
write_spef soc_post_route.spef
```

---

# **🎯 Final Outcome**

By the end of Week 7, you will:

* Complete BabySoC physical design using OpenROAD
* Generate post-route SPEF with real parasitics
* Understand how layout affects STA timing
* Gain full RTL → Layout → Parasitics knowledge

This is a critical step toward **tapeout-level ASIC design** experience.

---

If you want, I can also create:

✅ A well-formatted GitHub folder structure
✅ A PDF version of this README
✅ A commands-only cheat sheet

Just tell me!
