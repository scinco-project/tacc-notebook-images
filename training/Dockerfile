FROM jupyter/scipy-notebook:2022-08-15

USER root

RUN chown -R jovyan /home/jovyan/ && \
    chmod 777 /home/jovyan

RUN pip3 install tapipy
RUN pip3 install tqdm
RUN pip3 install transformers
RUN pip3 install torch

RUN export HOME='/home/jovyan'

RUN apt-get update && apt-get install -y curl
RUN curl -L https://raw.githubusercontent.com/tapis-project/sgx3-tapis-tutorial/refs/heads/main/Jupyter-Notebook/sentiment_analysis.ipynb -o $HOME/sentiment_analysis.ipynb

RUN echo "export PATH=$HOME/.local/bin:${PATH}" >> ~/.bashrc

WORKDIR $HOME

USER jovyan
