FROM nvidia/cuda:12.9.1-cudnn-runtime-ubuntu24.04

# #install dependencies python 3.12
RUN apt-get update && apt-get install -y --no-install-recommends \
    python3.12 \
    python3-pip \
    python3-venv \
    && rm -rf /var/lib/apt/lists/*

RUN useradd -m -s /bin/bash jupyter

# Set working dir and ownership
WORKDIR /home/jupyter
RUN chown jupyter:jupyter /home/jupyter

USER jupyter

# Set up virtual environment
RUN python3.12 -m venv /home/jupyter/.venv
ENV PATH="/home/jupyter/.venv/bin:$PATH"


# Upgrade pip & install JupyterLab
RUN pip install --no-cache-dir --upgrade pip && \
    pip install --no-cache-dir \
        jupyterlab  \
        transformers diffusers xformers \
        bitsandbytes peft trl

RUN pip install --no-cache-dir \
        torch torchvision torchaudio \
        --index-url https://download.pytorch.org/whl/cu128
        
WORKDIR /app
RUN chown jupyter:jupyter /app

EXPOSE 8888


CMD ["jupyter", "lab", "--ip=0.0.0.0", "--port=8888", "--no-browser"]

