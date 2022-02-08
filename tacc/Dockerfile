# ---------------------------------
# Image: taccsciapps/jupyteruser-tc
# ---------------------------------
# The user notebook image for the TACC DesignSage JupyterHub.
#
# ------------------
# Building the image
# ------------------
# To build this image, simply change into this directory and issue:
# docker build -t taccsciapps/jupyteruser-ds:<some_tag> .
#
# Tags follow semantic versioning based on the CHANGELOG. When building new versions, always start with a release
# candidate for the image tag; for example:
# docker build -t taccsciapps/jupyteruser-ds:1.1.0-rc1 .
#
# ---------------
# Running Locally
# ---------------
# After building a release candidate, run it locally to test out your changes.
# This image is built to run on the JupyterHub. In order to run it locally, you need to provide a config file and a
# separate command. For example, change into this directory and run:
# docker run --rm -p 8888:8888 -v $(pwd)/jupyter-notebook-localconf.py:/home/jupyter/.jupyter/jupyter_notebook_config.py taccsciapps/jupyteruser-ds start-notebook.sh
# Note than an example of a jupyter-notebook-localconf.py file is provided in this directory.

FROM taccsciapps/jupyteruser-base:0.1.9

USER root
###################################################################
# record version in /etc - image_version is injected by build_jupyteruser.sh
###################################################################
ARG image_version=test
# RUN echo "${image_version}" > /etc/jupyteruser-ds-release
# RUN chmod a+r /etc/jupyteruser-base-release
###################################################################


ADD requirements.txt /requirements.txt

RUN pip install -r /requirements.txt

#RUN python -m spacy download en_core_web_sm
#RUN python -m spacy download en_core_web_md
RUN python -m spacy download en_core_web_lg

RUN pip install jupyter_plotly_dash \
    && pip install dash_daq \
    && pip install nbgitpuller \
    && pip install tensorflow \
    && pip install torch \
    && pip install keras