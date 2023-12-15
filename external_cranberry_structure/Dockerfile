FROM mambaorg/micromamba:1-mantic
LABEL authors="tjs334"

WORKDIR /home/mambauser/

COPY --chown=$MAMBA_USER:$MAMBA_USER env.yml /tmp/env.yml

RUN micromamba install -y -n base -f /tmp/env.yml && \
    micromamba install -y -n base jupyter && \
    micromamba clean --all --yes

#RUN python3 -m pip install --no-cache-dir notebook jupyterlab

## Added for PlantCV and Pytesseract
##############################################
# Switch to the root user
USER root

# Update and install the required packages
RUN apt-get update && \
    apt-get install -y mesa-utils && \
    apt-get install -y tesseract-ocr libtesseract-dev

# Switch back to the regular user
USER $MAMBA_USER
##############################################


## Change the UID of the existing user to 1000
#RUN usermod -u 1000 $MAMBA_USER

ARG NB_USER=mambauser
ARG NB_UID=57439
ENV USER ${NB_USER}
ENV NB_UID ${NB_UID}
ENV HOME /home/${NB_USER}

# Make sure the contents of our repo are in ${HOME}
COPY . ${HOME}
USER root
RUN chown -R ${NB_UID} ${HOME}
USER ${NB_USER}

ARG MAMBA_DOCKERFILE_ACTIVATE=1
ENV ENV_NAME=base

# Add a new CMD to start Jupyter Notebook
CMD [ "jupyter", "notebook", "--NotebookApp.default_url=/lab/" ]
