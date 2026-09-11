# Contrastive Learning

Live presentation demo at https://mzelbash.github.io/contrastive-learning/

# SimCLR SEAS-8525 Homework Week 2 

Open **SimCLR_CIFAR10_Homework.ipynb**. It contains the complete implementation, explanations, environment setup, and reflection prompts.

## Colab Pro

1. Go to https://colab.research.google.com/ and upload the notebook.
2. Save your own copy in Drive.
3. Select **Runtime > Change runtime type > Python 3 > GPU**.
4. Run the notebook with its default `MODE = "debug"` first.
5. For submission, set `MODE = "homework"` and optionally `USE_DRIVE = True`, then restart the session and run all cells.
6. Complete the final reflection and download the notebook with outputs.

Keep Colab's preinstalled torch and torchvision. The first code cell installs missing lightweight dependencies. The next checks versions and GPU availability.

The full run uses 50 pretraining epochs and 30 classifier epochs. Runtime is hardware dependent; an estimate appears after the first pretraining epoch. The debug run is not the homework submission.

## Local setup

Use Python 3.11 or 3.12. In a new folder:

```powershell
py -3.11 -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
```

On macOS/Linux:

```bash
python3.11 -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
```

For NVIDIA GPU support, install a **matched torch/torchvision pair** using the command generated for your machine at https://pytorch.org/get-started/locally/ . Do this before installing the other notebook requirements. Use a compatible NVIDIA driver; do not guess a CUDA wheel version.

For CPU debugging only:

```bash
python -m pip install torch torchvision --index-url https://download.pytorch.org/whl/cpu
```

Then install the notebook dependencies:

```bash
python -m pip install -r requirements-notebook.txt
python -m ipykernel install --user --name simclr-homework --display-name "SimCLR Homework"
jupyter lab
```

Choose the **SimCLR Homework** kernel. The notebook selects CUDA when available and CPU otherwise. Full homework mode requires CUDA; use debug mode on CPU. No pretrained model download is needed, but CIFAR-10 downloads on the first data-cell run.

## Files saved by a run

- `last_checkpoint.pt`: model, optimizer, scheduler, random states, and initial encoder baseline.
- `config.json`, `environment.json`, `splits.npz`: experimental configuration and data splits.
- Training history, figures, classifier checkpoints, and final `results.json`.

The data is downloaded to the runtime's local disk for speed. If Drive is enabled, checkpoints and results go to `MyDrive/SEAS8525_SimCLR`. Notebook outputs must still be saved in the notebook itself.

After a reset, rerun the notebook with the same run name and settings. It resumes at the next completed-epoch boundary. A changed experiment needs a new run name. Only load your own checkpoints.


