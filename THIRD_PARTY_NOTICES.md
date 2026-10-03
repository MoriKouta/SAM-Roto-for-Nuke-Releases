# Third-Party Notices

## SAM Roto for Nuke original project code

The original project code is licensed under the [MIT License](LICENSE):
Copyright (c) 2026 Kota Mori. This project license does not replace the
separate upstream terms below for bundled or downloaded components.

## Meta SAM 3 / SAM 3.1

The application ZIP bundles a **runtime-only snapshot** of official SAM 3 revision
`660a5e9e1b8b4c02c0ad97229b88a09a6e4ff5b7`. Package code/data, the tokenizer dictionary,
agent prompts, package configs, build metadata and the complete upstream LICENSE are retained.
Top-level demo media, examples, utility scripts and test fixtures are excluded. Retained file bytes
are unchanged; ZIP metadata is normalized. Original and packaged SHA-256 values are pinned in
`distribution/sources.lock.json` and the packaged `bootstrap/sources/manifest.json`.
This source is governed by Meta's **SAM License**, not by SAM Roto's project license or MIT.
The complete agreement is retained inside the bundled archive. Distribution and use must comply
with its redistribution, use and trade-control conditions; no broader rights are granted here.
SAM 3 / SAM 3.1 checkpoints are not bundled and remain subject to Meta's terms and Hugging Face
gated-access requirements; no authentication or gated checkpoint is requested during basic setup.

- Source: https://github.com/facebookresearch/sam3
- SAM 3 checkpoints: https://huggingface.co/facebook/sam3
- SAM 3.1 checkpoints: https://huggingface.co/facebook/sam3.1

## Meta SAM 2 / SAM 2.1

The application ZIP bundles SAM 2 source from Meta's official revision
`2b90b9f5ceec907a1c18123530e92e794ad901a4` as a **runtime-only snapshot**, retaining LICENSE and
LICENSE_cctorch. Inference modules, Hydra inference configs, optional CUDA source and build metadata
are retained. Demo/frontend fonts, notebooks, sample images/video, training/dataset tooling and
documentation assets are excluded. For portable, link-free
installation, four upstream config symlinks (`sam2/sam2_hiera_b+.yaml`, `sam2/sam2_hiera_l.yaml`,
`sam2/sam2_hiera_s.yaml`, `sam2/sam2_hiera_t.yaml`) are stored as regular files with their internal target's
exact bytes. Retained file contents are unchanged; ZIP metadata is normalized. Original/archive hashes
and the exact alias mapping are recorded in the source lock/manifest. SAM 2/2.1 Base+ checkpoints are
not bundled in the ZIP; Full Setup downloads pinned bytes from official public Meta URLs, validates
their SHA-256 and local loading, and stores them in the application's managed model directory.

- Source: https://github.com/facebookresearch/sam2
- License: Apache License 2.0 (see the upstream repository)
- Official public checkpoint host: https://dl.fbaipublicfiles.com/segment_anything_2/

## Sammie-Roto 2 reference

The UI/workflow has used the public Sammie-Roto 2 project as a design reference.
Sammie-Roto 2 itself is licensed under GNU GPL v3. No source code, icons,
resources, model files, or other assets from Sammie-Roto 2 are included in
this project. This notice is not a historical provenance audit of every
implementation line.

- Reference: https://github.com/Zarxrax/Sammie-Roto-2
- Upstream license: GNU GPL v3

## ViTMatte

Optional edge matting uses the ViTMatte model interface via Hugging Face Transformers.
The original ViTMatte project uses MIT. The Transformers integration is part of
the separately downloaded Transformers package and follows its own upstream
license. The default **hustvl/vitmatte-small-composition-1k model is Apache-2.0** according to its
official model card. Full Setup downloads its config/processor/safetensors files at revision
`6a58ad7646403c1df626fbd746900aec7361ea1d`, with SHA-256 pins in nuke/samroto_models.py.
No checkpoint is bundled in the SAM Roto ZIP. The managed local copy is validated and used offline;
this notice does not relicense the downloaded model. SAM Roto's MIT license does not replace its terms.

- Original project: https://github.com/hustvl/ViTMatte
- Public model used by default: https://huggingface.co/hustvl/vitmatte-small-composition-1k
- Transformers integration: https://huggingface.co/docs/transformers/model_doc/vitmatte

## Bundled uv installer runtime

The ZIP bundles unmodified official uv **0.12.17** executables for Windows x86_64 and Linux x86_64.
Build-time asset/binary SHA-256 pins are in `distribution/uv.lock.json`; the same manifest and upstream
`LICENSE-MIT` / `LICENSE-APACHE` texts are included under `bootstrap/uv/` in the ZIP. uv is dual-licensed
MIT OR Apache-2.0. No uv source modifications are made.

- Official release: https://github.com/astral-sh/uv/releases/tag/0.12.17
- Upstream licenses: https://github.com/astral-sh/uv/blob/0.12.17/LICENSE-MIT
  and https://github.com/astral-sh/uv/blob/0.12.17/LICENSE-APACHE

## Runtime tools and Python packages downloaded during setup

Apart from uv, the application ZIP does not bundle Python, PyTorch, CUDA, or third-party
package binaries. The isolated installer retrieves these separately; their
upstream notices and license files remain in the downloaded installations.
These downloaded components follow their respective upstream licenses, not
the MIT license of SAM Roto's original project code.
The [pinned inventory](docs/THIRD_PARTY_INVENTORY.md) lists all 69 direct/transitive runtime requirements,
versions, platform conditions and declared-license references. Bundled components inside downloaded
wheels (including CUDA libraries) retain additional notices; top-level package metadata is not exhaustive.

- uv: https://github.com/astral-sh/uv (MIT or Apache-2.0; upstream license files).
- Managed CPython: https://docs.astral.sh/uv/concepts/python-versions/#managed-python-distributions
  and https://docs.python.org/3/license.html (including bundled dependency notices).
- PyTorch / torchvision: https://github.com/pytorch/pytorch/blob/main/LICENSE
  and https://github.com/pytorch/vision/blob/main/LICENSE.
- CUDA dependencies supplied by the PyTorch wheels retain their NVIDIA terms:
  https://docs.nvidia.com/cuda/eula/index.html.
- OpenCV: https://github.com/opencv/opencv/blob/4.x/LICENSE;
  Pillow: https://github.com/python-pillow/Pillow/blob/main/LICENSE.
- einops: https://github.com/arogozhnikov/einops/blob/main/LICENSE;
  pycocotools: https://github.com/ppwwyyxx/cocoapi;
  psutil: https://github.com/giampaolo/psutil/blob/master/LICENSE.
- Transformers: https://github.com/huggingface/transformers/blob/main/LICENSE;
  Hugging Face Hub: https://github.com/huggingface/huggingface_hub/blob/main/LICENSE.
- pip, setuptools and wheel are installation tools, downloaded into the isolated
  environment: https://github.com/pypa/pip, https://github.com/pypa/setuptools,
  https://github.com/pypa/wheel. Transitive dependencies retain their own notices.

The project LICENSE and the current text of this notice are approved by the
maintainer in `distribution/public_release.json`. That approval does not
certify compatibility with every separately downloaded component. The pinned
inventory and platform-specific upstream terms still require release review.
