# qe2w90-band-plot

Plotting scripts for first-principles band structures computed with **Quantum ESPRESSO** and Wannier-interpolated bands from **Wannier90**. Each notebook is self-contained: specifying the data path, configuring the plot, interactively zooming/panning, and saving the figure all happen in a single notebook, making it easy to go from raw calculation output to a publication-ready figure.

## Features

- Band structure plotting (QE and Wannier90, side by side or overlaid)
- Projected density of states (PDOS) alongside band structures
- Spin-texture visualization (Sx / Sy / Sz expectation values on the band structure)
- Comparison plots between different pseudopotentials / SOC settings (e.g. SOC vs. without SOC)
- Appendix - Optical activity analysis (natural optical activity from third-rank conductivity tensors)

## Requirements

Tested with:

- Python 3.12+
- uv 0.11+
- VS Code with the Jupyter extension (recommended, but any Jupyter frontend works)

## Usage

1. Clone this repository:
   ```bash
   git clone https://github.com/your-username/qe2w90-band-plot.git
   cd qe2w90-band-plot
   ```

2. Install dependencies with uv:
   ```bash
   uv sync --frozen
   ```

3. Place your calculation output under `data/<material_name>/`, then edit the dataset dictionary at the top of the relevant notebook to point at your files (see the example below).

4. Open the relevant notebook under `scripts/` and run all cells. Figures are saved automatically to `scripts/<notebook_name>_save/`.

## Notebooks

| Notebook | Purpose |
|---|---|
| `QE_band_pdos.ipynb` | QE band structure with projected DOS |
| `QE_band_spin.ipynb` | QE band structure with spin-texture coloring |
| `QE_band_vs_qe.ipynb` | Compare two QE band structures (e.g. NC vs. PAW) |
| `W90_band_vs_qe.ipynb` | Compare QE bands against Wannier90-interpolated bands |
| `OSD.ipynb` | Natural optical activity (rotatory strength / CD) from conductivity tensor data |

## Repository layout

This repository does not include calculation data (see [Data availability](#data-availability) below).

```
.
├── scripts/
│   ├── QE_band_pdos.ipynb
│   ├── QE_band_spin.ipynb
│   ├── QE_band_vs_qe.ipynb
│   ├── W90_band_vs_qe.ipynb
│   └── OSD.ipynb
├── data/
│   └── <material_name>/
│       └── cif/
├── pyproject.toml
├── uv.lock
└── README.md
```

`data/<material_name>/cif/` holds the crystal structure file(s) for that material. Everything below that (which pseudopotential, SOC on/off, which calculation type, etc.) is not fixed by this repository — each notebook's dataset dictionary just points at whatever file paths your calculations actually produced, so you're free to organize them however fits your workflow.

## Data availability

The raw calculation data referenced by these notebooks belong to unpublished research and are not included in this repository. The notebooks are provided to document the analysis workflow; dataset dictionaries use placeholder material names (`MaterialA`, `MaterialB`, ...) as examples. To use these scripts with your own data, place your files under `data/`, following whatever internal layout suits your calculations, and update the dataset dictionary at the top of each notebook accordingly.
