Signals Interpolation & Curve Fitting [DSP Task4]

# Signal Sampling & Reconstruction Studio — Curve Fitting Tool

A PyQt5 desktop application for interactive curve fitting, polynomial/linear interpolation, and error mapping of signal data.

---

## Features

- **Load CSV signal data** and visualize it on an interactive plot
- **Linear & Polynomial Interpolation** with configurable order (2nd–50th)
- **Multi-chunk fitting** — split the signal into N chunks and fit each independently
- **Extrapolation** — extend the fitted curve beyond the sampled region (10%–100% slider)
- **LaTeX equation display** — renders the fitted polynomial equation inline in a table
- **Error Mapping** — generates a 2D heatmap of fitting error across combinations of:
  - Number of chunks vs. interpolation order
  - Overlap % vs. number of chunks
  - Overlap % vs. interpolation order
- **Export** — save the curve fitting graph as a PNG image
- **Session logging** — all user actions are written to `Task4Log.txt` on exit

---

## Requirements

- Python 3.x
- PyQt5
- pyqtgraph
- numpy
- scipy
- matplotlib
- pandas
- opencv-python (`cv2`)
- fpdf

Install all dependencies with:

```bash
pip install PyQt5 pyqtgraph numpy scipy matplotlib pandas opencv-python fpdf
```

---

## Usage

```bash
python Task4GUI.py
```

1. **File → Open File** (`Ctrl+O`) — load a CSV file where column 1 is the X axis and the last column is the Y axis
2. Choose **One Chunk** or **Multiple Chunks** in the Fitting Options panel and set the number of chunks
3. Select **Linear** or **Polynomial** interpolation type; adjust the order slider for polynomial
4. Use the **Extrapolation slider** to control how much of the signal is used for fitting
5. In the **Error Mapping** section, select what the X and Y axes of the heatmap represent, then click **Run EM**
6. **File → Save Curve Fitting IMG** to export the plot as `curveFitting.png`
7. **File → Exit** (`Esc`) to quit and save the session log

---

## Project Structure

```
.
├── Task4GUI.py          # Main application (UI + logic)
├── Task4GUI.ui          # Qt Designer UI file
├── Task4Log.txt         # Auto-generated session log (created on exit)
├── Data files/          # Sample CSV data files
└── TestResults/         # Output/test result storage
```

---

## CSV Format

The input CSV should have at minimum two numeric columns:

```
x,y
0.0,1.23
0.1,1.45
...
```

The app reads the **first column** as X (feature) and the **last column** as Y (target).

---

## Keyboard Shortcuts

| Action | Shortcut |
|---|---|
| Open file | `Ctrl+O` |
| Exit | `Esc` |
| Zoom in (curve) | `+` |
| Zoom out (curve) | `-` |
| Run Error Mapping | `Ctrl+E` |
| Zoom in (error map) | `Ctrl+=` |
| Zoom out (error map) | `Ctrl+-` |

---

## Notes

- The app currently processes up to **1000 data points** from the loaded file for display and fitting
- Overlap values for error mapping range from **0% to 25%** in steps of 5%
- The session log (`Task4Log.txt`) records all major user interactions and is written when the app exits cleanly via File → Exit
