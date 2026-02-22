FROM nvidia/cuda:12.9.1-cudnn-runtime-ubuntu24.04

# #install dependencies python 3.12
RUN apt-get update && apt-get install -y --no-install-recommends \
    python3.12 \
    python3-pip \
    python3-venv \
    && rm -rf /var/lib/apt/lists/*

# Set up virtual environment
RUN python3.12 -m venv /opt/venv
ENV PATH="/opt/venv/bin:$PATH"


# Upgrade pip & install JupyterLab
RUN pip install --no-cache-dir --upgrade pip && \
    pip install --no-cache-dir jupyterlab  

# Install PyTorch & ecosystem packages. Adjust the CUDA version in the index URL as needed.
# base container cuda must be compatible with host cuda.
RUN pip install --no-cache-dir \
    torch torchvision torchaudio \
    --index-url https://download.pytorch.org/whl/cu128

# Additional libraries
RUN pip install --no-cache-dir \
    transformers diffusers xformers bitsandbytes peft trl

# Set the working directory
# Add after venv install:
RUN useradd -m -s /bin/bash jupyter
WORKDIR /app
RUN chown jupyter:jupyter /app
USER jupyter

# Expose the JupyterLab port
EXPOSE 8888


CMD ["jupyter", "lab", "--ip=0.0.0.0", "--port=8888", "--no-browser"]

