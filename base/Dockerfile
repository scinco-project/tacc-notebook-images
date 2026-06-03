# ---------------------------------
# Image: taccsciapps/jupyteruser-tc
# ---------------------------------
# The base user notebook image for the TACC JupyterHub.
#
# ------------------
# Building the image
# ------------------
# To build this image, simply change into this directory and issue:
# docker build -t taccsciapps/jupyteruser-base:<tag> .
#
# Tags follow semantic versioning based on the CHANGELOG. When building new versions, always start with a release
# candidate for the image tag; for example:
# docker build -t taccsciapps/jupyteruser-base:<tag> .
# 
# NOTE: Some machines (eg: M4 Mac) require this build command to be compatible with the VM architecture:
# docker buildx build --platform linux/amd64 -t taccsciapps/jupyteruser-base:<tag> .
#
# ------------------
# Building the image
# ------------------
# docker push taccsciapps/jupyteruser-base:<tag>

FROM jupyter/minimal-notebook:latest

USER root

RUN apt-get update && apt-get install -y \
    gdal-bin \
    libgdal-dev \
    g++ \
    && rm -rf /var/lib/apt/lists/*

RUN export GDAL_VERSION=$(gdal-config --version)

RUN pip install -U pip setuptools wheel

ADD requirements.txt /requirements.txt
RUN pip install -r /requirements.txt

RUN pip install jupyter-dash && \
    jupyter lab build

RUN python -m spacy download en_core_web_sm
RUN python -m spacy download en_core_web_md
RUN python -m spacy download en_core_web_lg

RUN chmod 777 /opt/conda

COPY jupyter_notebook_server_config.py ${HOME}/.jupyter/jupyter_notebook_config.py

WORKDIR /home/jovyan

RUN chown -R jovyan /home/jovyan/ && \
    chmod 777 /home/jovyan && \ 
    chmod -R 777 /home/jovyan/.conda/

USER jovyan