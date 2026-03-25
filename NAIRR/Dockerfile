FROM quay.io/jupyter/tensorflow-notebook:cuda-python-3.13.12

USER root

RUN pip install --no-cache-dir tapipy \
    openai \
    keras \
    'jsonschema>=4.18' \
    torch \
    ultralytics \
    numba \
    numpy \
    "jupyter-ai[all]"==3.0.0b9

ENV JUPYTER_ENABLE_LAB=yes \
    USER=jovyan \
    LOGNAME=jovyan

RUN mkdir -p /home/jovyan/ai-tutorial-2026
RUN mkdir -p /home/jovyan/ai-tutorial-2026/notebooks
RUN mkdir -p /home/jovyan/ai-tutorial-2026/datasets
RUN mkdir -p /home/jovyan/ai-tutorial-2026/models

RUN chown -R jovyan:users /home/jovyan/ai-tutorial-2026
RUN chown -R jovyan:users /home/jovyan/ai-tutorial-2026/notebooks
RUN chown -R jovyan:users /home/jovyan/ai-tutorial-2026/datasets
RUN chown -R jovyan:users /home/jovyan/ai-tutorial-2026/models

COPY README.md /home/jovyan/ai-tutorial-2026/
COPY datasets /home/jovyan/ai-tutorial-2026/datasets
COPY models /home/jovyan/ai-tutorial-2026/models/
COPY notebooks/Code-Detection.ipynb /home/jovyan/ai-tutorial-2026/notebooks/Code-Detection.ipynb

RUN chmod -R 777 /home/jovyan/ai-tutorial-2026
RUN chmod -R 777 /home/jovyan/ai-tutorial-2026/notebooks
RUN chmod -R 777 /home/jovyan/ai-tutorial-2026/datasets
RUN chmod -R 777 /home/jovyan/ai-tutorial-2026/models

WORKDIR /home/jovyan

# Fix permissions for the home directory
RUN mkdir -p /home/jovyan/.cache/matplotlib && \
    chown -R jovyan /home/jovyan/ && \
    chmod 777 /home/jovyan && \ 
    chmod -R 777 /home/jovyan/.config/ && \
    chmod -R 777 /home/jovyan/.cache/matplotlib/ && \
    chmod -R 777 /home/jovyan/.cache/

USER jovyan

WORKDIR ${HOME}

# CMD ["jupyterhub-singleuser"]