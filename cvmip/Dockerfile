FROM jupyter/base-notebook:latest

USER root

RUN conda install -y -c conda-forge mamba && \
    mamba install -y -c conda-forge fenics matplotlib && \
    mamba clean -afy

RUN pip install hippylib[notebook]

ENV JUPYTER_ENABLE_LAB=yes

RUN mkdir -p /home/jovyan/.cache/matplotlib && \
    chown -R jovyan ${HOME} && \
    chmod 777 /home/jovyan && \
    chmod -R 777 /home/jovyan/.cache/matplotlib/ && \
    chmod -R 777 /home/jovyan/.cache/

USER jovyan

WORKDIR ${HOME}

# CMD ["jupyterhub-singleuser"]