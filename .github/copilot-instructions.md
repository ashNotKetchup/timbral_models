# Copilot Instructions for timbral_models

## Project Overview

- **timbral_models** is a Python package for predicting eight timbral characteristics from audio files: hardness, depth, brightness, roughness, warmth, sharpness, booming, and reverberation.
- The main entry point is the `timbral_extractor(fname)` function in the `timbral_models` package, which returns a dictionary of all attributes for a given audio file.
- Each attribute can also be computed individually via functions like `timbral_hardness(fname)`.
- The repository also contains a MATLAB implementation of the reverb model in `MATLAB:Weka Timbral Reverb/`.

## Key Files and Structure

- **timbral_models/**: Python source code for all timbral models and utilities.
  - `Timbral_*.py`: Each file implements a specific timbral attribute.
  - `timbral_util.py`: Shared utilities for feature extraction and processing.
  - `Timbral_Extractor.py`: Implements the main `timbral_extractor` function.
- **test.ipynb**: Example Jupyter notebook for running the extractor.
- **MATLAB:Weka Timbral Reverb/**: MATLAB code and models for reverb classification.
- **setup.py, setup.cfg**: Python package configuration.

## Usage Patterns

- To extract all timbral features from an audio file:
  ```python
  import timbral_models
  timbre = timbral_models.timbral_extractor('audio.wav')
  # timbre is a dict with all 8 attributes
  ```
- To extract a single attribute:
  ```python
  import timbral_models
  value = timbral_models.timbral_hardness('audio.wav')
  ```
- Optional parameter: `clip_output=True` constrains regression outputs to [0, 100].

## Dependencies & Installation

- Install via PyPI: `pip install timbral_models`
- For local development: `pip install -e .` (dependencies must be installed manually)
- Core dependencies: `numpy`, `soundfile`, `librosa`, `scikit-learn`, `scipy`, `six`, `pyloudnorm`

## Conventions & Patterns

- All model functions expect a file path to a readable audio file (WAV recommended).
- Outputs for regression models may exceed [0, 100] unless `clip_output=True` is set.
- The reverb model is a binary classifier (1 = reverberant, 0 = not reverberant).
- No CLI entry point; usage is via Python import or notebook.

## Testing & Examples

- See `test.ipynb` for example usage and quick validation.
- No formal test suite; validate changes by running the extractor on sample files.

## MATLAB Integration

- MATLAB code is independent; see `MATLAB:Weka Timbral Reverb/README.md` and Deliverable D5.8 for details.

## References

- For detailed model documentation, see Deliverable D5.8: http://www.audiocommons.org/materials/

---

If any conventions or workflows are unclear, please request clarification or examples from the user.
