# A Humble Pedigree - Project Documentation

## Overview
**A Humble Pedigree** is a web-based pedigree charting engine designed for clinical and educational use. It provides a reliable interface for creating, editing, and exporting family pedigree charts with precise generational alignment and structural integrity.

---

## Technical Architecture

### 1. Data Model
* **Individuals (`ped` array):** Stores personal metadata including unique IDs, sex/shape representation, affection/carrier status, genotype, custom labels, deceased markers, and proband flags.
* **Marriages (`marriages` array):** Explicitly pairs individuals as partners and maintains an ordered array of children belonging to each union. This prevents disconnected tree branches and missing connection lines.

### 2. Layout & Alignment Engine
* **BFS Generation Mapping:** Uses a Breadth-First Search algorithm across the explicit marriage and parent-child links to map relative generations ($I, II, III\dots$) correctly, even when accounting for in-laws.
* **Subtree Block Measuring:** Calculates the precise pixel footprint of individual family branches recursively, ensuring that parents are perfectly centered above their offspring and spacing remains non-overlapping.
* **Viewport Centering:** Automatically computes the minimum and maximum X coordinates of the rendered tree and centers it within the canvas viewport.
* **Dynamic Text Halos:** Labels and genotypes are rendered with solid white background bounds to ensure text cleanly floats over any intersecting relationship lines.

---

## User Interface & Features

### 1. Visual Attribute Inspector
* **Visual Pickers:** Replaces standard dropdown menus with intuitive SVG button grids for selecting biological sex (Male, Female, Unknown, Termination) and affection status (Unaffected, Affected, Carrier).
* **Selection State Management:** Adding children, partners, or siblings keeps the user's focus locked onto the currently selected individual for fast data entry.

### 2. Family Actions & Customization
* **Relational Building:** Supports adding parents, partners, siblings, sons, daughters, and twins (Fraternal and Identical) through dedicated control buttons.
* **Smart Deletion:** Features cascade deletion that sweeps away dependent descendants and prevents orphaned in-laws from lingering on the chart.
* **Display Options:** Offers dynamic toggles for generation roman numerals, auto-numbering, generation prefix notation (e.g., `II-1`), custom chart titles, and adjustable font sizing.
* **Legend & Symbology:** Features a dynamically updating pedigree key that only displays symbols (e.g., Deceased, Proband, Unknown, Twins) when they are actively present on the canvas. Includes a global toggle to set carrier representation as either half-shaded or dotted.

### 3. Random Pedigree Generator
* **Sample Engine:** Automatically builds biologically accurate sample trees based on user-defined parameters, perfect for quickly generating quiz or test materials.
* **Tuning Parameters:** Users define the inheritance pattern (AR, AD, XR, XD, Y-Linked, or None), carrier visibility, generation depth (2-5), and custom offspring distribution limits (minimum, median, and maximum bounds).

### 4. Export Capabilities
* **PNG Download:** Renders the canvas stage into a timestamped image file.
* **Clipboard Copy:** Copies the pedigree directly to the system clipboard via the Clipboard API.

---

## Version Information
* **Current Version:** V 1.2.0
* **Author:** Steven Humble
