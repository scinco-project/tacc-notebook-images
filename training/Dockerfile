FROM jupyter/scipy-notebook:2022-08-15

USER root

RUN chown -R jovyan /home/jovyan/ && \
    chmod 777 /home/jovyan

RUN pip3 install tapipy
RUN pip3 install tqdm
RUN pip3 install transformers
RUN pip3 install torch

RUN export HOME='/home/jovyan'

COPY sentiment_analysis.ipynb $HOME

RUN echo "export PATH=$HOME/.local/bin:${PATH}" >> ~/.bashrc

WORKDIR $HOME

USER jovyan
