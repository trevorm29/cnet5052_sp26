# graph-tool + NetworkX + Jupyter: Conda environment setup (all OS)

This is a standalone setup guide for the Class 05 `graph-tool` notebook.

## What you are installing

A single Conda environment with:

- `graph-tool`
- `networkx`
- the usual scientific stack (`numpy`, `pandas`, `scipy`, `matplotlib`)
- Jupyter (`jupyterlab`, `ipykernel`)

We’ll install everything from **conda-forge** (binary builds; no local compilation).

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

## 1) Create the environment (macOS / Linux)

### 1.1 Configure conda-forge (recommended)

```bash
conda config --add channels conda-forge
conda config --set channel_priority strict
```

### 1.2 Create + install

```bash
mamba create -n gtcnet5052 python=3.11
mamba install -n gtcnet5052 graph-tool networkx numpy pandas scipy matplotlib jupyterlab ipykernel tqdm

conda activate gtcnet5052
```

### 1.3 macOS note (Apple Silicon)

Check your architecture:

```bash
uname -m
```

If it prints `arm64`, you’re in a native Apple Silicon shell (recommended).  
If it prints `x86_64`, you’re in an Intel/Rosetta shell (it can work, but be consistent — mixing architectures is a common source of pain).

---

## 2) Windows (recommended): WSL2 + Ubuntu

`graph-tool` does not ship native Windows builds. Use WSL2.

### Step A — install WSL2 (PowerShell as Administrator)

```powershell
wsl --install
```

Reboot if prompted.

### Step B — open Ubuntu and install Miniforge inside WSL

Then run the same environment creation commands from the Linux section.

### Step C — run notebooks

Two workflows:

**Option 1: VS Code Remote (WSL)**  
- install VS Code on Windows  
- install the “Remote - WSL” extension  
- open your course folder in WSL  
- choose the `gtcnet5052` kernel

**Option 2: Jupyter in WSL → browser in Windows**

```bash
conda activate gtcnet5052
jupyter lab --no-browser --ip 0.0.0.0 --port 8888
```

Open the printed URL in your Windows browser.

---

## 3) Register the environment as a Jupyter kernel (recommended)

This makes the kernel selection unambiguous.

```bash
conda activate gtcnet5052
python -m ipykernel install --user --name gtcnet5052 --display-name "Python (gtcnet5052 / graph-tool)"
```

Then in Jupyter: **Kernel → Change Kernel → Python (gtcnet5052 / graph-tool)**.

---

## 4) Verify the install

```bash
conda activate gtcnet5052
python -c "import graph_tool.all as gt; import networkx as nx; import numpy as np; print('graph-tool OK')"
```

---

## 5) Reproducible installs with `environment.yml`

Save the following as `environment.yml`:

```yaml
name: gtcnet5052
channels:
  - conda-forge
dependencies:
  - python=3.11
  - graph-tool
  - networkx
  - numpy
  - pandas
  - scipy
  - matplotlib
  - jupyterlab
  - ipykernel
  - tqdm
```

Then run:

```bash
mamba env create -f environment.yml
conda activate gtcnet5052
```

---

## 6) Troubleshooting

If imports crash or the solver gets stuck:

- delete the environment and recreate it:
  ```bash
  conda env remove -n gtcnet5052
  ```
- stick to conda-forge with strict channel priority
- avoid mixing heavyweight compiled stacks in the same env (keep deep learning in a different env)

---

## 7) Fallback: Docker (if you cannot install locally)

There is an official Docker image:

```bash
docker pull tiagopeixoto/graph-tool
```

You can mount your course folder into the container and run Python/Jupyter inside it.
