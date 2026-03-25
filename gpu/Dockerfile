# ============================================================
# JupyterHub Single-User Notebook Server with NVIDIA GPU Support
# ============================================================
# Base image: NVIDIA CUDA + cuDNN runtime on Ubuntu 22.04
# ============================================================

ARG CUDA_VERSION=12.4.1
ARG UBUNTU_VERSION=22.04

FROM nvidia/cuda:${CUDA_VERSION}-cudnn-runtime-ubuntu${UBUNTU_VERSION}

LABEL maintainer="gcurbelo@tacc.utexas.edu"
LABEL description="JupyterHub single-user notebook server with NVIDIA GPU support"

ENV DEBIAN_FRONTEND=noninteractive
RUN apt-get update && apt-get install -y --no-install-recommends \
        python3 \
        python3-pip \
        python3-dev \
        build-essential \
        curl \
        git \
        wget \
        ca-certificates \
        libssl-dev \
        libffi-dev \
        libgomp1 \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

RUN ln -sf /usr/bin/python3 /usr/bin/python

RUN pip install --no-cache-dir --upgrade pip setuptools wheel

ARG JUPYTERHUB_VERSION=4.*
RUN pip install --no-cache-dir \
        "jupyterhub==${JUPYTERHUB_VERSION}" \
        notebook \
        jupyterlab \
        ipywidgets \
        ipykernel

RUN pip install --no-cache-dir \
        torch torchvision torchaudio \
        --index-url https://download.pytorch.org/whl/cu124

RUN pip install --no-cache-dir \
        numpy \
        pandas \
        scipy \
        scikit-learn \
        matplotlib \
        seaborn \
        plotly \
        tqdm \
        Pillow

RUN pip install --no-cache-dir \
        pynvml \
        gputil \
        cupy-cuda12x   # match your CUDA major version (e.g. cupy-cuda11x)

# Create jovyan user
ARG NB_USER=jovyan
ARG NB_UID=1000
ARG NB_GID=100

RUN useradd --create-home --shell /bin/bash \
        --uid ${NB_UID} --gid ${NB_GID} ${NB_USER}

ENV HOME=/home/${NB_USER}
WORKDIR ${HOME}

RUN chown -R ${NB_UID}:${NB_GID} ${HOME}

EXPOSE 8888

USER ${NB_USER}

CMD ["jupyterhub-singleuser"]
