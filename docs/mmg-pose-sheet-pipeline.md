# Featured container — `mmg-pose-sheet-pipeline`

## Purpose

`charlibillabert/mmg-pose-sheet-pipeline` is a containerized, headless GPU pipeline used in a character-generation workflow.

The goal of this portfolio entry is to demonstrate how an AI image pipeline can be packaged as a reproducible runtime instead of depending on a manually configured GPU workstation.

## Public image inspected

`charlibillabert/mmg-pose-sheet-pipeline:sm120-20260812-v6`

Public Docker Hub metadata currently exposes the following characteristics:

| Item | Public metadata |
|---|---|
| OS / architecture | Linux / amd64 |
| Compressed image size | ~4.9 GB |
| CUDA | 13.0.x |
| PyTorch | 2.11.0 |
| Core workflow | Headless sketch-to-pose-sheet pipeline |
| ComfyUI | Included, revision pinned at build time |
| Diffusers | Included, revision pinned at build time |
| Model volume | `/models` |
| Artifact volume | `/data/artifacts` |
| Service port | `8788/tcp` |
| Default mode | API-oriented entrypoint |

## Deployment-oriented design

The public layers also show deployment concerns beyond model execution:

- pinned framework revisions,
- NVIDIA GPU runtime support,
- dedicated model and artifact volumes,
- a process supervisor / init boundary,
- GPU preflight tooling,
- smoke / acceptance scripts,
- explicit service port exposure,
- and a dedicated application entrypoint.

This is useful for remote GPU execution because the environment can be versioned and deployed independently of the host machine.

## Portfolio positioning

This container is presented as evidence of experience with:

- Docker
- GPU inference
- CUDA environments
- Python AI services
- ComfyUI / Diffusers integration
- model pipeline packaging
- API-facing inference workers
- persistent model/artifact storage
- reproducible deployment
- remote GPU provider workflows

## Security and cost boundary

This repository does not publish production credentials or unrestricted hosted endpoints.

A public Docker image is a deployable artifact, not an invitation to use paid infrastructure owned by the developer.
