# OSMnx + GeoPandas + NetworkX + Jupyter: Conda environment setup (all OS)

This is a standalone setup guide for the spatial networks notebook:
`class_06_spatial.ipynb`.

## What you are installing

A single Conda environment with:

- `osmnx` (download + analyze OpenStreetMap street networks and features)
- `geopandas` + `shapely` + `pyproj` (geospatial vector stack)
- `networkx` (graph analysis)
- the usual scientific stack (`numpy`, `pandas`, `scipy`, `matplotlib`)
- Jupyter (`jupyterlab`, `ipykernel`)

Everything is installed from **conda-forge** (binary builds; no local compilation).

---

## 0) Install a Conda distribution

Recommended: **Miniforge** (Conda configured for conda-forge).

After installation, open a new terminal and verify:

```bash
conda --version
```

Optional (recommended): install `mamba` for faster installs:

```bash
conda install -n base -c conda-forge mamba
```

---

## 1) Create the environment

### 1.1 Configure conda-forge (recommended)

```bash
conda config --add channels conda-forge
conda config --set channel_priority strict
```

### 1.2 Create + install (recommended: from `environment_osmnx.yml`)

From the folder containing `environment_osmnx.yml`:

```bash
mamba env create -f environment_osmnx.yml
conda activate oxcnet5052
```

Alternative (manual install, same result):

```bash
mamba create -n oxcnet5052 python=3.11
mamba install -n oxcnet5052 -c conda-forge \
  "osmnx>=2.0,<3" geopandas shapely pyproj rtree \
  networkx numpy pandas scipy matplotlib jupyterlab ipykernel tqdm

conda activate oxcnet5052
```


### macOS note (Apple Silicon)

Check your architecture:

```bash
uname -m
```

If it prints `arm64`, you’re in a native Apple Silicon shell (recommended).  
If it prints `x86_64`, you’re in an Intel/Rosetta shell. That can work too, but be consistent — mixing architectures is a common source of geospatial-library errors.


---

## 2) Register the environment as a Jupyter kernel (recommended)

This makes kernel selection unambiguous.

```bash
conda activate oxcnet5052
python -m ipykernel install --user --name oxcnet5052 --display-name "Python (oxcnet5052 / osmnx)"
```

Then in Jupyter: **Kernel → Change Kernel → Python (oxcnet5052 / osmnx)**.

---

## 3) Verify the install

### 3.1 Import test

```bash
conda activate oxcnet5052
python -c "import osmnx as ox; import geopandas as gpd; import shapely; import networkx as nx; import numpy as np; print('OK:', ox.__version__)"
```

### 3.2 (Optional) Quick OSMnx sanity check

This makes a small request to OpenStreetMap’s APIs.

```bash
python - <<'PY'
import osmnx as ox
ox.settings.use_cache = True
ox.settings.log_console = True

G = ox.graph_from_place("Back Bay, Boston, Massachusetts, USA", network_type="walk")
print(len(G), "nodes;", G.number_of_edges(), "edges")
PY
```

If you run this repeatedly, you may hit rate limits. Prefer caching and saving graphs (see below).

---

## 4) Practical tip for teaching: cache + save graphs

For class demos, it’s often nicer to avoid re-downloading data each run:

```python
import osmnx as ox

ox.settings.use_cache = True
G = ox.graph_from_place("Boston, Massachusetts, USA", network_type="drive")

ox.save_graphml(G, filepath="boston_drive.graphml")
# later:
G = ox.load_graphml("boston_drive.graphml")
```

---

## 5) Windows notes

This stack works on native Windows via conda-forge.

Common pitfalls:
- **Do not** `pip install geopandas/shapely/pyproj` into this environment.
- If you already did, it’s usually faster to delete the env and recreate it.

Delete + recreate:

```powershell
conda env remove -n oxcnet5052
mamba env create -f environment_osmnx.yml
```

---

## 6) Troubleshooting

### PROJ / CRS errors (most common)
If you see errors mentioning `PROJ`, `proj.db`, or coordinate reference systems, it’s almost always a mixed install (pip + conda, or non-forge packages).

Fix:
1. delete the environment
2. recreate from `environment_osmnx.yml`
3. keep **strict** conda-forge channel priority

### API timeouts / 429 errors
OSMnx queries Nominatim + Overpass. You can get throttled, especially in a classroom.

Mitigations:
- enable caching: `ox.settings.use_cache = True`
- run fewer/lower-area queries (neighborhood instead of city)
- save graphs to disk (`save_graphml`) and reuse them

---

## 7) Optional add-ons (only if you want them)

Interactive mapping + basemaps:

```bash
conda activate oxcnet5052
mamba install -c conda-forge folium contextily
```

