# GeoTTER: Leveraging Local Geometry of Optimal Transport for Zero-Shot Classification

Authors: Wei-Yang Alex Lee, Rudrasis Chakraborty, Vishnu Suresh Lokhande

The 29th International Conference on Artificial Intelligence and Statistics (AISTATS)

## Abstract
We present GeoTTER, a novel framework that redefines optimal transport in the realm of zero-shot classification. Conventional methods often suffer from miscalibration and a lack of adaptability, as they rely on fixed cost matrices derived solely from pre-trained model embeddings. In contrast, GeoTTER addresses these limitations by incorporating two key techniques. First, to alleviate high-frequency label jaggedness (sample-level manifold jitter that assigns neighboring embeddings to different classes), GeoTTER integrates local geometric structure into the optimal transport formulation via graph-Laplacian smoothing, a technique grounded in spectral graph theory that enforces neighborhood consistency. Second, to correct coherent angular drift (a low-frequency orientation bias in which large groups of samples share the same angular offset from their true label prototypes), we fuse clustering-guided cost components with a globally adjusted transport cost, achieving a multi-objective optimization that respects both global distribution constraints and latent data structure. With a median improvement of +6.82% compared to zero-shot and +2.13% compared to OTTER, GeoTTER shows robust improvements across a diverse set of benchmarks. The code is available on https://github.com/TeleViaBox/GeoTTER







## Environment Setup

It is recommended to use a Python virtual environment (`venv`).

### 1. Create a virtual environment

On macOS / Linux:

```bash
python3 -m venv venv
```

On Windows:

```bash
python -m venv venv
```

### 2. Activate the virtual environment

On macOS / Linux:

```bash
source venv/bin/activate
```

On Windows (Command Prompt):

```bash
venv\Scripts\activate
```

On Windows (PowerShell):

```powershell
venv\Scripts\Activate.ps1
```

### 3. Install dependencies

```bash
cd GeoTTER/
pip install -r requirements.txt
```


## How to Run

### Run with the dummy dataset

In `run_geotter.py`, set:

```python
use_dummy = True
```

Then run:

```bash
python run_geotter.py
```

This will:

* generate a synthetic dataset
* run ZS, OT, and GeoTTER prediction
* print accuracy information
* save results to `GeoTTER_results/`

### Run with a real dataset

If you already have your real dataset loading pipeline, set:

```python
use_dummy = False
```

Then make sure the required dataset-loading utilities are available, such as:

* embedding loader
* label encoding loader
* label loader
* class count utility
* class balance utility

After that, run:

```bash
python run_geotter.py
```

## Output

The script writes experiment results to a CSV file, for example:

```text
GeoTTER_results/DummySet_results.csv
```

The CSV typically includes:

* dataset name
* backbone name
* method name (`GeoTTER`)
* parameter configuration
* accuracy
* prediction distribution



## Workflow

```bash
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
python run_geotter.py
```
