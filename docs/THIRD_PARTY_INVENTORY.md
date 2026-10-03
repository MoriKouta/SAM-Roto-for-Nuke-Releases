# Pinned runtime dependency inventory

This is an inventory for maintainer review, not legal clearance. Runtime package binaries are
downloaded during setup, not bundled in the application ZIP. Their installed license files remain
with them. Versions come from the single runtime lock (packaged as bootstrap/runtime.json).
Windows entries were inspected through installed distribution metadata; Linux-only NVIDIA terms
and Triton require review with the actual Linux wheels. Metadata is not a substitute for LICENSE files.

## Models and source snapshots

- SAM 2 / 2.1 runtime-only source: official Meta revision
  `2b90b9f5ceec907a1c18123530e92e794ad901a4`, Apache-2.0 with retained LICENSE_cctorch.
  Inference modules/configs/build metadata/licenses remain; demo/fonts/notebooks/training/media are excluded.
  Original and runtime-only archive digests remain pinned in distribution/sources.lock.json.
- SAM 2 and SAM 2.1 Base+ checkpoints: downloaded during Full Setup, not bundled in the installer ZIP.
  Official Meta identities and SHA-256 pins are in nuke/samroto_models.py.
- Default ViTMatte: [hustvl/vitmatte-small-composition-1k](https://huggingface.co/hustvl/vitmatte-small-composition-1k),
  **Apache-2.0 model**, revision `6a58ad7646403c1df626fbd746900aec7361ea1d`.
  Installer-owned local config/processor/safetensors bytes have individual SHA-256 pins; all are loaded
  locally before readiness is recorded. The original ViTMatte code project's MIT license is distinct.
- SAM 3 / 3.1 runtime-only source retains package code/data, tokenizer dictionary, prompts, configs,
  build metadata and the complete Meta SAM License; demos/examples/test fixtures are excluded.
  Original and packaged hashes are pinned. Optional Linux Advanced setup downloads
  fixed-revision gated checkpoints only with explicit approved access; Windows standard setup excludes it.
  Model receipts include validated byte identity, not tokens. Shared Hugging Face caches are not removed.

Managed CPython 3.12.14 uses the Python license and bundled-component notices:
[Python license](https://docs.python.org/3/license.html). uv managed Python distributions also carry
[python-build-standalone licenses](https://github.com/astral-sh/python-build-standalone/blob/main/docs/distributions.rst).

| Package | Pin | Platforms | Declared license / review source |
|---|---|---|---|
| annotated-doc | 0.0.5 | Windows / Linux | [MIT](https://pypi.org/project/annotated-doc/0.0.5/) |
| antlr4-python3-runtime | 4.9.3 | Windows / Linux | [BSD-3-Clause](https://pypi.org/project/antlr4-python3-runtime/4.9.3/) |
| anyio | 4.15.1 | Windows / Linux | [MIT](https://pypi.org/project/anyio/4.15.1/) |
| certifi | 2026.7.22 | Windows / Linux | [MPL-2.0](https://pypi.org/project/certifi/2026.7.22/) |
| click | 8.5.0 | Windows / Linux | [BSD-3-Clause](https://pypi.org/project/click/8.5.0/) |
| colorama | 0.4.6 | Windows | [BSD License](https://pypi.org/project/colorama/0.4.6/) |
| cuda-bindings | 12.9.4 | Linux | [Apache-2.0; review individual wheel notices](https://github.com/NVIDIA/cuda-python/blob/main/LICENSE) |
| cuda-pathfinder | 1.8.2 | Linux | [Apache-2.0; review individual wheel notices](https://github.com/NVIDIA/cuda-python/blob/main/LICENSE) |
| einops | 0.8.2 | Windows / Linux | [MIT](https://pypi.org/project/einops/0.8.2/) |
| filelock | 4.0.4 | Windows / Linux | [MIT](https://pypi.org/project/filelock/4.0.4/) |
| fsspec | 2026.9.0 | Windows / Linux | [BSD-3-Clause](https://pypi.org/project/fsspec/2026.9.0/) |
| ftfy | 6.1.1 | Windows / Linux | [MIT](https://pypi.org/project/ftfy/6.1.1/) |
| h11 | 0.16.0 | Windows / Linux | [MIT](https://pypi.org/project/h11/0.16.0/) |
| hf-xet | 1.6.0 | Windows / Linux | [Apache-2.0](https://pypi.org/project/hf-xet/1.6.0/) |
| httpcore | 1.0.9 | Windows / Linux | [BSD-3-Clause](https://pypi.org/project/httpcore/1.0.9/) |
| httpx | 0.28.1 | Windows / Linux | [BSD-3-Clause](https://pypi.org/project/httpx/0.28.1/) |
| huggingface-hub | 1.31.0 | Windows / Linux | [Apache-2.0](https://pypi.org/project/huggingface-hub/1.31.0/) |
| hydra-core | 1.3.6 | Windows / Linux | [MIT](https://pypi.org/project/hydra-core/1.3.6/) |
| idna | 3.20 | Windows / Linux | [BSD-3-Clause](https://pypi.org/project/idna/3.20/) |
| iopath | 0.1.10 | Windows / Linux | [MIT](https://pypi.org/project/iopath/0.1.10/) |
| jinja2 | 3.1.6 | Windows / Linux | [BSD License](https://pypi.org/project/jinja2/3.1.6/) |
| markdown-it-py | 4.2.0 | Windows / Linux | [MIT License](https://pypi.org/project/markdown-it-py/4.2.0/) |
| markupsafe | 3.0.3 | Windows / Linux | [BSD-3-Clause](https://pypi.org/project/markupsafe/3.0.3/) |
| mdurl | 0.1.2 | Windows / Linux | [MIT License](https://pypi.org/project/mdurl/0.1.2/) |
| mpmath | 1.3.0 | Windows / Linux | [BSD-3-Clause](https://pypi.org/project/mpmath/1.3.0/) |
| networkx | 3.7 | Windows / Linux | [BSD-3-Clause](https://pypi.org/project/networkx/3.7/) |
| numpy | 1.26.4 | Windows / Linux | [BSD-3-Clause; wheel includes additional component notices](https://pypi.org/project/numpy/1.26.4/) |
| nvidia-cublas-cu12 | 12.8.4.1 | Linux | [NVIDIA terms (review individual wheel notices)](https://docs.nvidia.com/cuda/eula/index.html) |
| nvidia-cuda-cupti-cu12 | 12.8.90 | Linux | [NVIDIA terms (review individual wheel notices)](https://docs.nvidia.com/cuda/eula/index.html) |
| nvidia-cuda-nvrtc-cu12 | 12.8.93 | Linux | [NVIDIA terms (review individual wheel notices)](https://docs.nvidia.com/cuda/eula/index.html) |
| nvidia-cuda-runtime-cu12 | 12.8.90 | Linux | [NVIDIA terms (review individual wheel notices)](https://docs.nvidia.com/cuda/eula/index.html) |
| nvidia-cudnn-cu12 | 9.10.2.21 | Linux | [NVIDIA terms (review individual wheel notices)](https://docs.nvidia.com/cuda/eula/index.html) |
| nvidia-cufft-cu12 | 11.3.3.83 | Linux | [NVIDIA terms (review individual wheel notices)](https://docs.nvidia.com/cuda/eula/index.html) |
| nvidia-cufile-cu12 | 1.13.1.3 | Linux | [NVIDIA terms (review individual wheel notices)](https://docs.nvidia.com/cuda/eula/index.html) |
| nvidia-curand-cu12 | 10.3.9.90 | Linux | [NVIDIA terms (review individual wheel notices)](https://docs.nvidia.com/cuda/eula/index.html) |
| nvidia-cusolver-cu12 | 11.7.3.90 | Linux | [NVIDIA terms (review individual wheel notices)](https://docs.nvidia.com/cuda/eula/index.html) |
| nvidia-cusparse-cu12 | 12.5.8.93 | Linux | [NVIDIA terms (review individual wheel notices)](https://docs.nvidia.com/cuda/eula/index.html) |
| nvidia-cusparselt-cu12 | 0.7.1 | Linux | [NVIDIA terms (review individual wheel notices)](https://docs.nvidia.com/cuda/eula/index.html) |
| nvidia-nccl-cu12 | 2.27.5 | Linux | [NVIDIA terms (review individual wheel notices)](https://docs.nvidia.com/cuda/eula/index.html) |
| nvidia-nvjitlink-cu12 | 12.8.93 | Linux | [NVIDIA terms (review individual wheel notices)](https://docs.nvidia.com/cuda/eula/index.html) |
| nvidia-nvshmem-cu12 | 3.4.5 | Linux | [NVIDIA terms (review individual wheel notices)](https://docs.nvidia.com/cuda/eula/index.html) |
| nvidia-nvtx-cu12 | 12.8.90 | Linux | [NVIDIA terms (review individual wheel notices)](https://docs.nvidia.com/cuda/eula/index.html) |
| omegaconf | 2.3.1 | Windows / Linux | [BSD License](https://pypi.org/project/omegaconf/2.3.1/) |
| opencv-python-headless | 4.11.0.86 | Windows / Linux | [Apache-2.0; wheel includes additional third-party notices](https://pypi.org/project/opencv-python-headless/4.11.0.86/) |
| packaging | 26.3 | Windows / Linux | [Apache-2.0 OR BSD-2-Clause](https://pypi.org/project/packaging/26.3/) |
| pillow | 12.3.0 | Windows / Linux | [MIT-CMU](https://pypi.org/project/pillow/12.3.0/) |
| pip | 26.2.1 | Windows / Linux | [MIT](https://pypi.org/project/pip/26.2.1/) |
| portalocker | 4.4.0 | Windows / Linux | [BSD-3-Clause](https://pypi.org/project/portalocker/4.4.0/) |
| psutil | 7.2.2 | Windows / Linux | [BSD-3-Clause](https://pypi.org/project/psutil/7.2.2/) |
| pycocotools | 2.0.11 | Windows / Linux | [BSD-2-Clause](https://pypi.org/project/pycocotools/2.0.11/) |
| pygments | 2.21.0 | Windows / Linux | [BSD-2-Clause](https://pypi.org/project/pygments/2.21.0/) |
| pyyaml | 6.0.3 | Windows / Linux | [MIT](https://pypi.org/project/pyyaml/6.0.3/) |
| regex | 2026.9.10 | Windows / Linux | [Apache-2.0 AND CNRI-Python](https://pypi.org/project/regex/2026.9.10/) |
| rich | 15.0.0 | Windows / Linux | [MIT](https://pypi.org/project/rich/15.0.0/) |
| safetensors | 0.8.0 | Windows / Linux | [Apache Software License](https://pypi.org/project/safetensors/0.8.0/) |
| setuptools | 81.0.0 | Windows / Linux | [MIT](https://pypi.org/project/setuptools/81.0.0/) |
| shellingham | 1.5.4 | Windows / Linux | [ISC](https://pypi.org/project/shellingham/1.5.4/) |
| sympy | 1.14.0 | Windows / Linux | [BSD-3-Clause](https://pypi.org/project/sympy/1.14.0/) |
| timm | 1.0.29 | Windows / Linux | [Apache-2.0](https://pypi.org/project/timm/1.0.29/) |
| tokenizers | 0.23.2 | Windows / Linux | [Apache Software License](https://pypi.org/project/tokenizers/0.23.2/) |
| torch | 2.10.0+cu128 | Windows / Linux | [BSD-3-Clause](https://pypi.org/project/torch/2.10.0/) |
| torchvision | 0.25.0+cu128 | Windows / Linux | [BSD-3-Clause](https://pypi.org/project/torchvision/0.25.0/) |
| tqdm | 4.70.1 | Windows / Linux | [MPL-2.0 AND MIT](https://pypi.org/project/tqdm/4.70.1/) |
| transformers | 5.17.0 | Windows / Linux | [Apache-2.0](https://pypi.org/project/transformers/5.17.0/) |
| triton | 3.6.0 | Linux | [MIT; review wheel and bundled component notices](https://github.com/triton-lang/triton/blob/v3.6.0/LICENSE) |
| typer | 0.27.2 | Windows / Linux | [MIT](https://pypi.org/project/typer/0.27.2/) |
| typing-extensions | 4.16.0 | Windows / Linux | [PSF-2.0](https://pypi.org/project/typing-extensions/4.16.0/) |
| wcwidth | 0.9.1 | Windows / Linux | [MIT License](https://pypi.org/project/wcwidth/0.9.1/) |
| wheel | 0.48.0 | Windows / Linux | [MIT](https://pypi.org/project/wheel/0.48.0/) |

All 69 lock entries are listed, including Linux CUDA wheels. OpenCV, NumPy, PyTorch and
other wheels may bundle further components; retain their license directories. No claim that every
transitive binary is governed solely by its top-level package license is made.

Bundled artifacts (separate from the table): uv 0.12.17 MIT OR Apache-2.0, SAM2 source
2b90b9f5ceec907a1c18123530e92e794ad901a4 Apache-2.0, SAM3 source
660a5e9e1b8b4c02c0ad97229b88a09a6e4ff5b7 under the custom SAM License.
Their complete upstream notices are retained inside bootstrap/uv and bootstrap/sources archives.
Standard SAM2/2.1 and ViTMatte checkpoints are downloaded during Full Setup, not bundled.
Optional Linux SAM3/3.1 requires explicit Advanced setup; see [notices](../THIRD_PARTY_NOTICES.md).
