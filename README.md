# GDS2 Wafer Map Converter

A desktop application for converting **GDS2 text data** into **ASCII wafer maps** for semiconductor workflows.  
Built with **Python** and **tkinter**, the tool provides a classic Windows-style interface for loading layout data, generating wafer maps, editing outputs live, and exporting results in **SINF / KLA-compatible text format**.

---

## Overview

The GDS2 Wafer Map Converter is designed to simplify the process of turning coordinate-based GDS2 layout references into wafer map text files suitable for downstream manufacturing or inspection systems. It combines file parsing, die-grid generation, visual map rendering, and editable raw output in a single lightweight desktop tool.

The application is intended for engineers who need a fast, local, and dependency-free solution for wafer map generation and review.

---

## Features

- Load **GDS2 text files**
- Parse **SREF / SNAME / XY** structure references
- Filter dies by selected **structure names**
- Automatically detect **die pitch**
- Generate wafer maps based on:
  - wafer diameter
  - die size
  - edge-die rules
- Export ASCII wafer maps in:
  - **SINF format**
  - **CRLF**
  - **LF**
- Open and edit existing **ASCII wafer map files**
- Live update of wafer map from edited raw output
- Interactive map tools:
  - zoom in / zoom out
  - fit to window
  - grid line toggle
  - mouse coordinate display
  - click-to-cycle cell state
- Editable **bin definition table**
- Classic Windows desktop GUI using **tkinter**

---

## Tech Stack

- **Python 3.8+**
- **tkinter** for GUI
- Standard Python libraries only

No third-party packages are required.

---

## File Input

The converter expects a **GDS2 text-format file** containing records such as:

- `SREF`
- `SNAME`
- `XY`
- `ENDEL`

It extracts die placement coordinates from matching structure names and converts them into a wafer grid representation.

You can also open an existing **ASCII wafer map** (`.txt`, `.map`, `.csv`) directly for inspection or editing.

---

## Output

The generated wafer map is exported as a text file containing:

- header metadata
- optional bin definitions
- wafer map rows using symbols such as:
  - `?` active die
  - `*` edge die / scribe
  - `.` empty location

Supported output line modes:

- **SINF**
- **CRLF**
- **LF**

---

## Interface Summary

### Input File
Load a GDS2 text file from disk.

### Wafer Settings
Set:
- wafer ID
- wafer diameter
- die size X / Y
- structure names
- edge-die visibility

### Output Settings
Choose:
- output filename
- line ending mode

### Actions
- Convert
- Export
- Reset

### Statistics
Displays:
- dies found
- rows
- columns
- file size
- parse time

### Map View
Shows the generated wafer map with zoom and interaction controls.

### Raw Output
Displays the full exported text output and allows direct editing with live map refresh.

---

## How It Works

1. Open a **GDS2 text file**
2. Enter or auto-detect **die pitch**
3. Define wafer settings
4. Click **Convert**
5. Review the generated wafer map visually
6. Optionally edit the raw output directly
7. Export the final wafer map as a text file

---

## Running the Application

```bash
python wafermap_gui.py
