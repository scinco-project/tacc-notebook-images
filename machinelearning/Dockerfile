FROM jupyter/tensorflow-notebook

USER root

WORKDIR /home/jovyan

RUN chown -R jovyan /home/jovyan/ && \
    chmod 777 /home/jovyan

RUN mkdir /home/jovyan/software/ 
    
WORKDIR /home/jovyan/software

RUN pip install tapipy --ignore-installed certifi

RUN chown -R jovyan /home/jovyan/software && \
    chmod 777 /home/jovyan/software && \
    chmod -R 777 /home/jovyan/software/ && \
    chmod -R 777 /home/jovyan/.config/ && \
    chmod -R 777 /home/jovyan/.cache/matplotlib/ && \
    chmod -R 777 /home/jovyan/.cache/

WORKDIR /home/jovyan

USER jovyan