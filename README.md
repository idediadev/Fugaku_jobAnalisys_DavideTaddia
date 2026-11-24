# Fugaku_jobAnalisys_DavideTaddia

Tesi sperimentale UniBo a cura di Davide Taddia: analisi dei job del supercomputer Fugaku e modelli di regressione (Linear, Decision Tree, Random Forest, GBT, rete neurale) sul dataset F-DATA.

## Dataset e codice originale

Basato su F-DATA di Antici et al. (repository originale: https://github.com/francescoantici/F-DATA, dati: https://doi.org/10.5281/zenodo.11467483).

> Antici F., Bartolini A., Domke J., Kiziltan Z., Yamamoto K. (2025). F-DATA: A Fugaku Workload Dataset for Job-centric Predictive Modelling in HPC Systems. Scientific Data 12, 1321. doi:10.1038/s41597-025-05633-1

## Struttura

- `FDATA_analisi.ipynb`: notebook di analisi ed esperimenti
- `requirements.txt`: dipendenze Python
- `docs/`, `generate_plots.py`, `baseline_experiments.py`, `generation_scripts/`, `plots/`: materiale del repository originale
- `F-DATA/`: i 38 file `.parquet` (non inclusi, da scaricare)

## Setup

```bash
uv venv --python 3.10
source .venv/bin/activate
uv pip install -r requirements.txt pyarrow jupyterlab ipykernel
mkdir -p F-DATA
for ym in 21_{03..12} 22_{01..12} 23_{01..12} 24_{01..04}; do
  curl -L -C - -o F-DATA/$ym.parquet "https://zenodo.org/records/11467483/files/$ym.parquet?download=1"
done
jupyter lab FDATA_analisi.ipynb
```
