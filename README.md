# Python for Geologists — Student & Researcher Learning Package

A complete companion package for the open-source course

> ```text
> Gomez, K. A. (2026). python_for_geologists (v1.0) [Computer software].
> GitHub. https://github.com/kevinalexandr19/python_for_geologists
> ```
>
> Star ⭐ the original repo to support it and get notified when new chapters are released.

## Contents

```
├── README.md                            ← you are here
├── docs/
│   ├── 01_STUDY_GUIDE.md                ← what the course is, roadmap, required libraries, study method
│   ├── 02_SETUP_GUIDE.md                ← 3 ways to run it: JupyterLite / Colab / local conda
│   └── 03_CHEAT_SHEET.md                ← one-page NumPy–Pandas–Matplotlib reference for geologists
├── notebooks/
│   ├── 00_setup_check.ipynb             ← run first: verifies Python + libraries + datasets
│   └── 01_geology_data_workflow.ipynb   ← executed example: TAS diagram, drillhole grades, earthquake catalog
├── lessons/                             ← one notebook per library (see roadmap below)
└── data/
    ├── rocks.csv                        ← whole-rock geochemistry (GEOROC)
    ├── assay.csv                        ← drillhole assays (Cu, Au, Ag, Mo…)
    ├── earthquakes.csv                  ← Peruvian earthquake catalog (1960+)
    └── generated/                       ← rasters & NetCDF files created by the lessons themselves
```

## 📚 Library roadmap — 20 lessons

Every lesson is a standalone Jupyter notebook in [`lessons/`](lessons/) using the
repo's own geology datasets. **✅ Executed** means the notebook was run end-to-end
and ships with its outputs confirmed; **📝 Code-ready** means the code is complete
but needs an external account or binary you must set up yourself.

### 🟢 Beginner

| # | Lesson | What you learn | Status |
|---|--------|----------------|--------|
| 01 | [Python Basics](lessons/01_python_basics.ipynb) | variables, lists, dicts, loops, functions | ✅ Executed |
| 02 | [NumPy](lessons/02_numpy.ipynb) | arrays, vectorised math, boolean cutoff masks | ✅ Executed |
| 03 | [Pandas](lessons/03_pandas.ipynb) | assay tables, filtering, length-weighted grades | ✅ Executed |
| 04 | [Matplotlib](lessons/04_matplotlib.ipynb) | histograms, Harker diagrams, downhole logs | ✅ Executed |
| 05 | [Pathlib & OS](lessons/05_pathlib_os.ipynb) | finding files, batch-processing CSVs | ✅ Executed |

### 🟡 Intermediate

| # | Lesson | What you learn | Status |
|---|--------|----------------|--------|
| 06 | [GeoPandas](lessons/06_geopandas.ipynb) | GeoDataFrames, reprojection, buffers, GeoJSON | ✅ Executed |
| 07 | [Shapely](lessons/07_shapely.ipynb) | points/lines/polygons, intersections, claims | ✅ Executed |
| 08 | [PyProj](lessons/08_pyproj.ipynb) | CRS transforms, UTM zones, geodesic distance | ✅ Executed |
| 09 | [Rasterio](lessons/09_rasterio.ipynb) | GeoTIFF read/write, DEMs, windows, hillshade | ✅ Executed |
| 10 | [Rioxarray](lessons/10_rioxarray.ipynb) | labelled rasters, clip, reproject, raster math | ✅ Executed |
| 11 | [Xarray](lessons/11_xarray.ipynb) | time × lat × lon cubes, groupby, NetCDF I/O | ✅ Executed |
| 12 | [NetCDF4](lessons/12_netcdf4.ipynb) | building .nc files, dimensions, groups, metadata | ✅ Executed |
| 13 | [Earth Engine API](lessons/13_earth_engine.ipynb) | SRTM, Sentinel-2, NDVI at planetary scale | 📝 Code-ready (needs GEE account) |
| 14 | [Geemap](lessons/14_geemap.ipynb) | interactive EE maps, split maps, ROI export | 📝 Code-ready (needs GEE account) |
| 15 | [SciPy](lessons/15_scipy.ipynb) | lognormal grade fits, hypothesis tests, griddata | ✅ Executed |

### 🟠 Advanced

| # | Lesson | What you learn | Status |
|---|--------|----------------|--------|
| 16 | [PyKrige](lessons/16_pykrige.ipynb) | ordinary kriging, variograms, uncertainty maps | ✅ Executed |
| 17 | [Scikit-learn](lessons/17_scikit_learn.ipynb) | rock classification, feature importance, KMeans | ✅ Executed |
| 18 | [Plotly](lessons/18_plotly.ipynb) | interactive Harker/3-D drillhole plots, HTML export | ✅ Executed |
| 19 | [Cartopy](lessons/19_cartopy.ipynb) | map projections, seismicity maps, gridlines | ✅ Executed |
| 20 | [PyGMT](lessons/20_pygmt.ipynb) | shaded relief, GMT-quality maps, profiles | 📝 Code-ready (needs GMT via conda) |

### Installing the lesson libraries

The 🟢 beginner lessons need only the scientific-Python basics (they come with Anaconda):

```bash
pip install numpy pandas matplotlib
```

The 🟡/🟠 geospatial lessons additionally use:

```bash
pip install geopandas shapely pyproj rasterio rioxarray xarray netCDF4 scipy pykrige scikit-learn plotly kaleido cartopy
```

And the two "set-up-yourself" stacks:

```bash
pip install earthengine-api geemap        # lessons 13–14, needs a free GEE account
conda install -c conda-forge pygmt        # lesson 20, GMT is a C library
```

## Recommended order

1. Read **`docs/01_STUDY_GUIDE.md`** (10 min) — overview, roadmap, libraries.
2. Follow **`docs/02_SETUP_GUIDE.md`** — pick JupyterLite (instant), Colab (cloud), or local conda (research).
3. Run **`notebooks/00_setup_check.ipynb`** — confirm everything works.
4. Start the course: clone the repo and open `content/0_start.ipynb`, then work through `1a`→`1g`, `2a`→`2c`, `5a`.
5. Alongside chapters 2a–2c, study **`notebooks/01_geology_data_workflow.ipynb`** and do its ✏️ challenges.
6. Work through the **`lessons/`** notebooks in order (01 → 20); each ends with ✏️ exercises.
7. Keep **`docs/03_CHEAT_SHEET.md`** open while you work.

Or try it instantly in the browser (nothing to install):
https://kevinalexandr19.github.io/python_for_geologists/lab/index.html?path=0_start.ipynb

*Course content © Kevin Alexander Gomez (see the repository's LICENSE).*
