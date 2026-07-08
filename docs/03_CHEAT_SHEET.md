# NumPy · Pandas · Matplotlib — Cheat Sheet for Geologists

Keep this open while working through the course. Every snippet is copy-paste-runnable.

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
```

---

## NumPy — arrays & fast math

```python
a = np.array([54.2, 61.7, 48.9])      # array from a list
np.arange(0, 100, 2)                  # 0, 2, 4, ... 98  (like sample depths)
np.linspace(0, 10, 50)                # 50 evenly spaced values

a.mean(), a.std(), a.min(), a.max()   # basic statistics
np.median(a), np.percentile(a, 75)    # robust statistics

a * 2.2                               # vectorized: applies to every element
a[a > 50]                             # boolean filtering
np.log10(a); np.sqrt(a)               # elementwise functions

rng = np.random.default_rng(42)       # reproducible random numbers
rng.normal(58, 8, size=200)           # simulate 200 SiO2 values
```

## Pandas — tables

```python
df = pd.read_csv("files/rocks.csv")            # also: read_excel, read_json
df.head(); df.info(); df.describe()            # first look — ALWAYS do this
df.shape                                       # (rows, columns)

df["SiO2"]                                     # one column (a Series)
df[["SiO2", "MgO"]]                            # several columns
df[df["SiO2"] > 63]                            # filter rows
df[(df["SiO2"] > 52) & (df["SiO2"] <= 63)]     # AND = &, OR = |, note the ()

df["Alkalis"] = df["Na2O"] + df["K2O"]         # new column from old ones
df["class"] = pd.cut(df["SiO2"],
    bins=[0,45,52,63,100],
    labels=["ultramafic","mafic","intermediate","felsic"])

df.groupby("Name")["SiO2"].mean()              # stats per rock type
df.sort_values("SiO2", ascending=False)        # sorting
df.isna().sum()                                # count missing values per column
df.dropna(subset=["CU_pct"])                   # drop rows missing that column
df["CU_pct"].fillna(0)                         # or fill them

df.rename(columns={"fecha UTC": "date"})       # clean messy column names
pd.to_datetime(df["date"], format="%d/%m/%Y")  # parse dates
df.to_csv("results.csv", index=False)          # save your work
```

## Matplotlib — figures

```python
fig, ax = plt.subplots(figsize=(8, 5))

ax.scatter(x, y, s=15, alpha=0.6, c=depth, cmap="viridis")   # scatter (maps!)
ax.plot(grade, depth)                                        # line (logs)
ax.hist(values, bins=30, edgecolor="white")                  # histogram
ax.boxplot([g1, g2, g3], labels=["basalt","andesite","dacite"])

ax.set_xlabel("SiO$_2$ (wt%)")     # LaTeX subscripts work: $_2$
ax.set_ylabel("Depth (m)")
ax.set_title("My figure")
ax.legend(); ax.grid(alpha=0.3)
ax.invert_yaxis()                  # depth increases downward!
ax.set_xscale("log")               # log axis (trace elements, grades)

plt.tight_layout()
plt.savefig("figure.png", dpi=300) # publication quality
plt.show()
```

## Multi-panel figures

```python
fig, axes = plt.subplots(1, 2, figsize=(10, 4), sharey=True)
axes[0].plot(cu, depth); axes[0].set_title("Cu")
axes[1].plot(au, depth); axes[1].set_title("Au")
```

---

## Golden rules

1. `df.head()` and `df.info()` **before anything else** — know your data.
2. Filtering needs parentheses: `df[(A) & (B)]`, never `and`/`or`.
3. Missing values: check `isna().sum()` early; decide drop vs. fill *consciously*.
4. If you wrote a `for` loop over rows of a DataFrame — there's almost always a vectorized one-liner.
5. Read errors from the **last line up**; the last line names the actual problem.
6. `Shift+Enter` runs a cell; `Kernel → Restart & Run All` proves your notebook is reproducible.
