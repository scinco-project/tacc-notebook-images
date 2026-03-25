FROM jupyter/base-notebook:latest

# Image metadata.
ENV IMAGE_NAME="dr-nb-img:base"
LABEL image_name="taccsciapps/${IMAGE_NAME}"
LABEL image_name_alt="taccsciapps/${IMAGE_NAME}"
LABEL maintainer="Gilbert Curbelo <gcurbelo@tacc.utexas.edu>"

USER root

RUN apt clean && \
    apt update && \
    apt upgrade --yes && \
    apt install --yes --quiet --no-install-recommends \ 
    libgl1-mesa-glx \
    xvfb \
    libxrender1 \
    pkg-config \
    build-essential \
    gcc \
    gfortran \
    libopenblas-dev

COPY requirements.txt ${HOME}/.python/requirements.txt
RUN python -m pip install -r ${HOME}/.python/requirements.txt --no-cache-dir && \
    python -m pip freeze > ${HOME}/.python/pip_freeze.txt

RUN pip uninstall -y scipy scikit-learn
RUN pip install --no-binary scipy scikit-learn

COPY jupyter_notebook_config.py ${HOME}/.jupyter/jupyter_notebook_config.py

RUN chown -R jovyan ${HOME} && \
    chmod 777 ${HOME}

USER jovyan

WORKDIR ${HOME}