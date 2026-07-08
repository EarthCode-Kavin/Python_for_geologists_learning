# Setup Guide — Three Ways to Run the Course

Choose the option that matches your situation. You can start with Option A today and move to Option C when you're ready for serious research work.

---

## Option A — Zero Installation: JupyterLite (browser only)

**Best for:** trying the course right now, lab computers where you can't install software, tablets/Chromebooks.

1. Open: **https://kevinalexandr19.github.io/python_for_geologists/lab/index.html?path=0_start.ipynb**
2. That's it. Python runs *inside your browser* (via WebAssembly/Pyodide). No account, no install.

**Limitations:** slightly slower, some libraries unavailable, work is saved only in your browser's storage (export important notebooks with `File → Download`). Not suitable for large datasets.

---

## Option B — Cloud, No Installation: Google Colab

**Best for:** anyone with a Google account and unreliable local hardware; sharing work with a supervisor.

1. Go to https://colab.research.google.com
2. `File → Open notebook → GitHub` tab → paste `kevinalexandr19/python_for_geologists` → pick a notebook.
3. To use the data files inside Colab, add a cell at the top:

```python
!git clone https://github.com/kevinalexandr19/python_for_geologists.git
%cd python_for_geologists/content
```

**Advantages:** free GPU access (useful for later ML chapters), auto-saves to Google Drive, nothing to install.
**Limitations:** requires internet; sessions reset after idle time (re-run the clone cell).

---

## Option C — Local Installation (recommended for researchers)

**Best for:** thesis/research work, your own datasets, offline work, full control.

### Step 1 — Install Miniconda (the standard for scientific Python)

Download Miniconda for your OS from https://docs.conda.io/en/latest/miniconda.html and install with default settings.

> Why conda instead of plain Python? Conda manages *environments* — isolated toolboxes. Your "geology" environment can't break your system or other projects. This is standard practice in every geoscience research group.

### Step 2 — Get the repository

With Git (recommended):
```bash
git clone https://github.com/kevinalexandr19/python_for_geologists.git
cd python_for_geologists
```

Without Git: on the GitHub page, click the green **Code** button → **Download ZIP** → extract.

### Step 3 — Create the environment

Open a terminal (Anaconda Prompt on Windows) and run:

```bash
conda create -n pygeo python=3.11 -y
conda activate pygeo
pip install jupyterlab numpy pandas matplotlib scikit-learn ipywidgets ipympl ipyleaflet
```

(These match the project's `requirements.txt` core stack; exact pinned versions are optional for learning.)

### Step 4 — Launch JupyterLab

```bash
cd python_for_geologists/content
jupyter lab
```

Your browser opens JupyterLab. Double-click `0_start.ipynb` in the file panel on the left. **Every time you return:** open a terminal → `conda activate pygeo` → `jupyter lab`.

### Alternative: Visual Studio Code

If you prefer an editor: install VS Code + the "Python" and "Jupyter" extensions, open the repository folder, open any `.ipynb`, and select the `pygeo` environment as the kernel (top-right). Many researchers eventually settle here because it combines notebooks with script editing and Git tools.

---

## Verifying Your Setup

Open `notebooks/00_setup_check.ipynb` from this companion package and run all cells (`Run → Run All Cells`). It checks Python version, all required libraries, and loads each of the course datasets. If everything prints ✅, you're ready.

---

## Troubleshooting Quick Reference

| Symptom | Likely fix |
|---|---|
| `command not found: conda` | Restart terminal; on Windows use "Anaconda Prompt" |
| `ModuleNotFoundError: No module named 'pandas'` | You forgot `conda activate pygeo` before launching Jupyter |
| Notebook kernel keeps dying | Restart kernel; close other notebooks; check RAM usage |
| `FileNotFoundError: files/rocks.csv` | Launch Jupyter from the `content/` folder, or fix the relative path |
| Plots not showing | Add `%matplotlib inline` in a cell and re-run |
| Excel/CSV with strange characters | Try `pd.read_csv(path, encoding="latin-1")` — common with Spanish-language datasets like `earthquakes.csv` |
