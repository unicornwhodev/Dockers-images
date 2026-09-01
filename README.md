# AI Automation, GPU Pipelines & Containerized Inference

Public portfolio repository for containerized AI workflows built and maintained by **Unicorn Who Dev**.

This repository documents practical work around reproducible GPU inference, model-serving environments, automated AI pipelines, preprocessing/post-processing stages, and deployment-oriented containers.

> This is a **portfolio and technical documentation repository**. It does not expose production credentials, private endpoints, model secrets, proprietary datasets, or unrestricted paid GPU services.

## What this demonstrates

- Docker-based AI deployment
- Reproducible GPU inference environments
- CUDA / PyTorch workloads
- Headless AI pipelines
- API-oriented model services
- Model and artifact volume separation
- Containerized preprocessing and post-processing
- Versioned runtime dependencies
- Local and remote GPU deployment patterns
- Integration of AI services into larger web and automation systems

## Public Docker Hub

**Docker Hub:** https://hub.docker.com/u/charlibillabert

Public images are used as technical proof of containerized AI workflows. Individual containers may belong to active R&D projects and can have different runtime, model, licensing, and hardware requirements.

## Featured container

### `charlibillabert/mmg-pose-sheet-pipeline`

A headless GPU pipeline created for a character-generation workflow.

Publicly inspectable image metadata shows a Linux/amd64 container built around:

- CUDA 13.0
- PyTorch 2.11
- ComfyUI
- Diffusers
- version-pinned runtime components
- dedicated `/models` and `/data/artifacts` volumes
- API-oriented execution
- exposed service port `8788`
- GPU-oriented preflight and acceptance tooling

The container packages the execution environment around a sketch-to-pose-sheet pipeline rather than relying on a manually configured workstation.

See [`docs/mmg-pose-sheet-pipeline.md`](docs/mmg-pose-sheet-pipeline.md).

## Typical architecture

```text
Client / App
    |
    v
API or job request
    |
    v
Containerized AI service
    |
    +--> input validation / preprocessing
    |
    +--> GPU model pipeline
    |
    +--> post-processing / validation
    |
    v
Versioned artifacts / structured output
```

Model files and generated artifacts are kept separate from the container image when appropriate. This makes it possible to update runtime code independently from large model assets and persistent outputs.

## Why containers

For AI workloads, Docker is used as part of the deployment architecture rather than only as a packaging step.

The goal is to make an inference pipeline:

- reproducible across machines,
- explicit about runtime dependencies,
- easier to deploy on remote GPU providers,
- easier to validate before accepting jobs,
- easier to version and roll back,
- and easier to integrate behind APIs or automated workflows.

## Related work

This container work is part of a broader development portfolio covering:

- AI automation and agentic workflows
- generative AI pipelines
- computer vision
- dataset engineering and fine-tuning
- web applications
- WebAudio and audio software
- geospatial and 3D systems

Portfolio: https://unicornwhodev.com

GitHub: https://github.com/unicornwhodev

Hugging Face: https://huggingface.co/Charlbi

FireViewer: https://github.com/fireviewer

## Scope

The public documentation intentionally avoids:

- credentials and API secrets,
- internal service URLs,
- unrestricted production endpoints,
- private datasets,
- proprietary model weights,
- provider-specific billing information,
- and operational details that would allow abuse of paid infrastructure.

Public containers should be treated as technical artifacts with their own requirements and licensing constraints, not as guaranteed free hosted services.
