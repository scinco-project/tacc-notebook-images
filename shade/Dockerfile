# ---------------------------------
# Image: taccsciapps/darpa-shade
# ---------------------------------
# The user notebook image for the TACC DesignSage JupyterHub.
#
# ------------------
# Building the image
# ------------------
# To build this image, simply change into this directory and issue:
# docker build -t taccsciapps/darpa-shade:<date_tag> .
#
# Tags follow versioning based off date of build -- YYMMDD. For example, if building on January 1, 2022, build as:
# docker build -t taccsciapps/darpa-shade: 220101 .
#
# If building on January 2, 2022, build as:
# docker build -t taccsciapps/darpa-shade: 220102 .
#
# Pulls from base TACC image
FROM taccsciapps/jupyteruser-base:220214

USER root

ADD requirements.txt /requirements.txt

RUN pip install -r /requirements.txt

COPY jupyter_notebook_config.py ${HOME}/.jupyter/jupyter_notebook_config.py
