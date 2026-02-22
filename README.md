# LLM Fine-Tuning Environment with JupyterLab & GPU

A Docker-based development environment for fine-tuning large language models (LLMs) on NVIDIA GPUs — with support for **public and private Hugging Face datasets**.



## Quickstart

GPU-enabled JupyterLab with PyTorch (cu130), Transformers, Diffusers, and more.

 **Run with GPU:**
```bash
docker run -it --rm --gpus all -p 8888:8888 abshkd/cuda-jupyter-train:cuda128-py312-torch210
```


## What’s Included

- **JupyterLab** (web IDE)
- **PyTorch + CUDA** (GPU-accelerated training)
- **Hugging Face ecosystem**: `transformers`, `datasets`, `peft`, `trl`, `accelerate`, `bitsandbytes`, `xformers`
- Supports **LoRA, QLoRA**, full fine-tuning, and more
- Access to **private & public HF datasets** via Hugging Face token

---

## Quick Start

### 1. Prerequisites
- Docker installed ([Install Docker](https://docs.docker.com/get-docker/))
- NVIDIA GPU + [NVIDIA Container Toolkit](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/install-guide.html)  
  (Required for GPU access in Docker)

### 2. Build the image

```bash
docker build -t cuda-jupyter-training <versionfolder>
```

### Paths
 - map `./data` to `/app/data` or `./local_notebooks` to `/app`