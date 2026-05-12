# RCoMET-CSD-preliminary
Preliminary proof-of-concept for R-CoMET: Riemannian Covariance Mamba EEG Transformer with Cross-Spectral Density features. Cross-subject (PhysionetMI) and cross-session (BNCI2014-001) motor imagery benchmarks.
---

## How to Run

### Requirements

```bash
# Python 3.10+
pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118
pip install mamba-ssm
pip install moabb
pip install pyriemann
pip install mne
pip install scikit-learn pandas numpy scipy joblib tqdm
```

> **GPU required** for Mamba SSM.  
> Tested on: NVIDIA RTX 4050 6GB, CUDA 11.8, Python 3.10, Ubuntu 24.04 (WSL2)

### Experiment 1 — PhysionetMI

Open `experiment1_physionet.ipynb` in Jupyter and run all cells.

The dataset downloads automatically via MOABB on first run (~5 GB).

**Expected runtime:** ~6 hours on RTX 4050 (25 subjects × ~15 min/subject)

**Key constants you can adjust:**
```python
N_SUBJECTS       = 25      # max 109
RCOMET_EPOCHS    = 15      # increase for better results
RCOMET_AUG_RATIO = 0.1    # geodesic augmentation ratio
```

### Experiment 2 — BNCI2014-001

Open `experiment2_bnci.ipynb` in Jupyter and run all cells.

Dataset downloads automatically via MOABB (~380 MB).

**Expected runtime:** ~2 minutes (9 subjects × ~9 sec/subject)

**Key constants:**
```python
RCOMET_EPOCHS      = 30
LAMBDA_MANIFOLD    = 0.01   # manifold regularisation weight
RCOMET_AUG_RATIO   = 0.1
```

---

## Hardware Used

| Component | Specification |
|---|---|
| CPU | Intel Core i5-13420H @ 2.10 GHz |
| RAM | 32 GB DDR5 |
| GPU | NVIDIA RTX 4050 Laptop 6 GB |
| OS | Windows 11 / WSL2 Ubuntu 24.04 |
| Python | 3.10 |


datasets used:
