# Dipmapper

Dipmapper is a **work-in-progress tool** designed to help set up automated *Diplomacy* adjudicators such as *digi-diplo*.

---

## Required Inputs

Place the following files inside the `assets/` folder:

* **`background.png`**
  An image of the provinces and their borders.

  * Borders must be **solid black**
  * Provinces must be **single-color (monocoloured)**

* **`centers.png`**
  An image of all supply centers in the variant.

  * Shape does not matter
  * Must be fully contained within their respective provinces

* **`names.png`**
  An image containing all province names.

  * Larger fonts and machine-readable fonts improve OCR reliability

* **`units.png`**
  An image of all units in the variant.

  * Shape does not matter
  * Must be mostly contained within their respective provinces

---

## 📦 Optional Inputs

Also placed inside the `assets/` folder:

* **`namelist.txt`**
  A list of province names.

  * Greatly improves OCR accuracy, especially for small fonts
  * Debug mode will output a generated list that you can refine and reuse

---

## ⚙️ Required Configuration (in `DipMapper.py`)

* **`COLOR_REGION_TYPE_MAPPING`**
  Maps province colors to player powers or tile types.

  * If your variant includes island provinces, ensure they use a **distinct color** from land tiles

* **`CAPITALS`**
  A list of capital provinces for each power.

  * Leave empty if your variant does not use capital rules

* **`THRESHOLD_SIZE` and `LARGER_UNIT`**
  Used to distinguish between unit types (army vs fleet).

  * Set a threshold between their sizes
  * Specify which unit type is larger

---

## ⚙️ Optional Configuration

* **`Custom_config`**
  Defines allowed characters in province names.

  * Defaults: Latin alphabet, apostrophe, numbers `1–5`

* **`DELETE_TINY_REGIONS`**
  Automatically removes very small detected regions (likely pixel noise)

  * Default: `True`

* **`SPACE_REPLACER`**
  Character used to replace spaces in province names

  * Default: underscore (`_`)

---

## 📤 Outputs

* **`Graph.yaml`**
  Main output file describing provinces and their adjacencies

* **`players.yaml`**
  Defines playable powers, starting centers, and units

* **`regions.png`** and **`tiles.png`**

  * Identical images
  * Not human-readable
  * Used internally by digi-diplo for map rendering

---

## ▶️ Run Modes

* **`debug`**

  * Outputs detected regions visualization
  * Compiles best guesses for province names

* **`full`**

  * Standard mode
  * Produces all output files

* **`first_half`**

  * Processes the map
  * Outputs `halfway.json`

* **`second_half`**

  * Reads `halfway.json` (once moved into the assets folder)
  * Produces final outputs

---

## 🚧 Status

This project is still under development.
