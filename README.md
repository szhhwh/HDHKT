# HDHKT

This repository contains the official implementation for the paper *"HDHKT: Heterogeneous Graph and Diﬃculty-aware
Hypergraph Fusion for Knowledge Tracing"*.

## Project Structure

```text
HDHKT/
├── data_process.py      # data download and preprocessing
├── train.py             # training entry point
├── scripts/             # helper scripts
├── model/HDHKT/         # HDHKT model implementation
├── utils/               # configs, data processing, training utilities
└── pixi.toml            # environment definition
```

## Environment

Use Pixi to create the environment.

```bash
# GPU, CUDA 11.7
pixi shell

# CPU
pixi shell -e cpu
```

## Data Preparation

Supported datasets: `assistments09`, `assistments12`, `assistments17`, `ednet_kt1`.

```bash
# download raw data
python data_process.py download -d assistments09

# preprocess data
python data_process.py process -d assistments09
```

Processed files will be saved to `data/<dataset>/`.

## Training

```bash
# train HDHKT
python train.py -m HDHKT -d assistments09

# train a specific fold
python train.py -m HDHKT -d assistments09 --fold 0

# train multiple folds
bash scripts/run_kfold.sh HDHKT "0 1 2 3 4" -d assistments09
```

Training outputs are saved under `runs/normal/`.
