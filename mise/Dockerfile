FROM jupyter/datascience-notebook:python-3.11.6

USER root
###################################################################
# record version in /etc - image_version is injected by build_jupyteruser.sh
###################################################################
# RUN echo "${image_version}" > /etc/jupyteruser-ds-release
# RUN chmod a+r /etc/jupyteruser-base-release
###################################################################


ADD requirements.txt /requirements.txt

RUN pip install -r /requirements.txt

RUN python -m spacy download en_core_web_lg

RUN pip install jupyter_plotly_dash \
    && pip install dash_daq \
    && pip install nbgitpuller \
    && pip install tensorflow \
    && pip install torch \
    && pip install keras

# COPY jupyter_notebook_config.py ${HOME}/.jupyter/jupyter_notebook_config.py
