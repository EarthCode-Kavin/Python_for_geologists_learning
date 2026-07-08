# Python for Geologists — Complete Study Guide

*A companion guide to the [python_for_geologists](https://github.com/kevinalexandr19/python_for_geologists) repository by Kevin Alexander Gomez (v1.0, January 2026), prepared for students and researchers in Geology and related Earth Science fields.*

---

## 1. What This Project Is

**Python for Geologists** is a free, open-source curriculum that teaches Python programming through geological problems. Instead of learning to code with abstract examples, you learn with rock geochemistry tables, drillhole assay data, earthquake catalogs, and mineral classification problems.

The project is built entirely on **Jupyter notebooks** (`.ipynb` files) — interactive documents that mix explanatory text, live code, and plots. You read a concept, run the code, modify it, and see the result immediately. This is exactly how professional geoscientists work with data every day.

**Prerequisites (recommended, not mandatory):**
- General geology (mineralogy, petrology, structural basics)
- Introductory statistics (mean, standard deviation, distributions)
- Basic linear algebra (vectors, matrices) — needed only for later ML chapters
- **No prior programming experience required**

---

## 2. Repository Structure — What's Where

```
python_for_geologists/
├── README.md                  ← Project overview and index
├── requirements.txt           ← Python libraries used by the project
├── content/                   ← ★ THE NOTEBOOKS (this is where you work)
│   ├── 0_start.ipynb          ← Welcome / orientation notebook
│   ├── 1a_variables.ipynb     ← Python fundamentals begin here
│   ├── 1b_print.ipynb
│   ├── 1c_logic.ipynb
│   ├── 1d_structures.ipynb
│   ├── 1e_automation.ipynb
│   ├── 1f_objects.ipynb
│   ├── 1g_reserved_words.ipynb
│   ├── 2a_numpy.ipynb         ← Core scientific libraries
│   ├── 2b_pandas.ipynb
│   ├── 2c_matplotlib.ipynb
│   ├── 5a_exercises.ipynb     ← Hands-on practice (202 code cells!)
│   ├── files/                 ← Real geological datasets
│   │   ├── rocks.csv          (whole-rock geochemistry, GEOROC data)
│   │   ├── assay.csv          (drillhole assay: Cu, Au, Ag, Mo...)
│   │   ├── earthquakes.csv    (Peruvian earthquake catalog, 1960+)
│   │   └── rasters/           (lunar mapping raster data)
│   └── resources/             ← Figures and images used in notebooks
├── docs/                      ← Pre-built JupyterLite web app (don't edit)
└── jupyter_lite_config.json   ← Config for the browser version
```

**Key insight:** Everything you need is in `content/`. The `docs/` folder is just the compiled website version — you never need to touch it.

---

## 3. The Learning Roadmap

### Stage 1 — Programming Fundamentals (Notebooks 1a–1g)
*Estimated time: 2–3 weeks at ~1 notebook every 2 days*

| Notebook | Topic | Geology connection |
|----------|-------|--------------------|
| `1a_variables` | Variables, numbers, strings, type conversion | Storing sample IDs, grades, coordinates |
| `1b_print` | Displaying results, f-strings, formatting | Formatting lab reports, assay printouts |
| `1c_logic` | Booleans, if/elif/else, comparisons | Classifying rocks by SiO₂ thresholds |
| `1d_structures` | Lists, tuples, dictionaries, sets | Mineral assemblages, stratigraphic columns |
| `1e_automation` | for/while loops, list comprehensions | Batch-processing hundreds of samples |
| `1f_objects` | Object-oriented programming, classes | Modeling a "Drillhole" or "Sample" object |
| `1g_reserved_words` | Python keywords reference | Avoiding common naming errors |

**Milestone check:** Before moving on, you should be able to write a loop that classifies a list of SiO₂ values into felsic/intermediate/mafic/ultramafic categories without looking anything up.

### Stage 2 — The Scientific Core (Notebooks 2a–2c)
*Estimated time: 3–4 weeks. This is the most important stage for research work.*

| Notebook | Library | What you'll master |
|----------|---------|--------------------|
| `2a_numpy` | NumPy | Arrays, vectorized math, statistics, matrix operations — the foundation of ALL scientific Python |
| `2b_pandas` | Pandas | DataFrames: loading CSVs/Excel, filtering, grouping, cleaning messy field data |
| `2c_matplotlib` | Matplotlib | Publication-quality figures: scatter plots, histograms, cross-sections, maps |

**Milestone check:** Load `rocks.csv`, compute the mean SiO₂ per rock type, and plot a Total Alkali–Silica style scatter — all in under 15 lines.

### Stage 3 — Practice (Notebook 5a)
*Estimated time: 2 weeks, ongoing*

`5a_exercises.ipynb` is a large problem set (200+ code cells) that recaps everything: variables, logic, structures, automation, OOP, and the standard library, all with geological flavor. Do it in passes — first the fundamentals sections, return to the harder ones after Stage 2.

### Stage 4 — Statistics & Machine Learning (⏳ under development)
The README lists upcoming chapters: descriptive statistics, probability, linear/logistic regression, decision trees, random forests, K-Means clustering, and PCA. These are marked ⏳ in the repo — watch/star the repository on GitHub to be notified when they land. The `resources/` folder already contains figures for them (decision trees, neural networks, PCA), so they are actively being written. The two companion notebooks included in this package give you a head start on this stage using the repo's own datasets.

---

## 4. Required Libraries — What They Are and Why

The project's `requirements.txt` pins these core scientific libraries:

### Must know (used throughout the course)
| Library | Purpose | Analogy for a geologist |
|---------|---------|------------------------|
| **NumPy** | Fast numerical arrays and math | Your scientific calculator, but for a million samples at once |
| **Pandas** | Tabular data (rows/columns) | Excel, but scriptable, reproducible, and handles millions of rows |
| **Matplotlib** | Plotting and figures | Grapher/Origin — every figure in your thesis can come from here |
| **scikit-learn** | Machine learning | The toolbox for the ML chapters (classification, clustering, regression) |

### Interactive/notebook infrastructure (installed automatically with Jupyter)
| Library | Purpose |
|---------|---------|
| **JupyterLab / Notebook** | The environment where notebooks run |
| **ipywidgets** | Sliders and interactive controls inside notebooks |
| **ipympl** | Interactive (zoomable) matplotlib figures |
| **ipyleaflet** | Interactive maps inside notebooks (great for sample locations) |

### Worth learning next (not in this course, but standard in geoscience research)
- **SciPy** — interpolation, curve fitting, signal processing
- **GeoPandas** — Pandas + shapefiles/vector GIS data
- **Rasterio / rioxarray** — DEMs, satellite imagery, geophysical grids
- **xarray** — multidimensional data (climate, model outputs; the repo's resources hint at it)
- **PyGMT** — publication maps (the Python interface to Generic Mapping Tools)

---

## 5. How to Work Effectively — Study Method

1. **Never just read a notebook — run every cell.** Press `Shift+Enter` on each cell as you go. Passive reading teaches almost nothing in programming.
2. **Break the code on purpose.** Change a number, rename a variable, delete a comma. Read the error message. Errors are the fastest teacher in Python.
3. **Type, don't copy-paste.** For at least the first month, retype examples by hand. Muscle memory matters.
4. **Keep a personal "cookbook" notebook.** Every time you solve something (e.g., "filter a DataFrame by two conditions"), paste a minimal working example into your own notebook. In 3 months this becomes your most-used reference.
5. **Apply each topic to YOUR data immediately.** Have XRF results? Field measurements? A well-log CSV? After each chapter, redo one example with your own data. This is the single biggest accelerator.
6. **Use the datasets provided.** `rocks.csv`, `assay.csv`, and `earthquakes.csv` are real-style data with real problems (missing values, mixed formats, Spanish column headers in the earthquake file — a classic real-world situation).
7. **Work in small daily sessions.** 45–60 minutes daily beats a 6-hour Saturday marathon.
8. **When stuck for more than 20 minutes:** read the error's *last line* first, search it, check the official docs (numpy.org, pandas.pydata.org), then ask (Stack Overflow, or an AI assistant — but always run and understand the answer).

---

## 6. Version Control Tip for Researchers

Since notebooks are code, learn minimal Git early:

```bash
git clone https://github.com/kevinalexandr19/python_for_geologists.git
cd python_for_geologists
git checkout -b my-work        # your own branch — the original stays clean
```

Work on your branch; `git pull` on `main` later to receive the upcoming Statistics/ML chapters without losing your notes.

---

## 7. Reference Books (from the project's own bibliography)

- Petrelli, M. (2021). *Introduction to Python in Earth Science Data Analysis* — the best single companion book for this course.
- Trauth, M. (2022). *Python Recipes for Earth Sciences.*
- Petrelli, M. (2023). *Machine Learning for Geosciences* — for Stage 4.
- Pyrcz, M. — *Python Numerical Demos* (GitHub) — hundreds of geostatistics notebooks.

---

*Next: read `02_SETUP_GUIDE.md` to get Python running, then open `notebooks/00_setup_check.ipynb` to verify everything works.*
