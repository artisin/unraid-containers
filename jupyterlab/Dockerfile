FROM python:3.10

# Install nicer Bash terminal
RUN git clone --depth=1 https://github.com/Bash-it/bash-it.git ~/.bash_it && \
  bash ~/.bash_it/install.sh --silent

# Install NodeJS 12
RUN curl -sL https://deb.nodesource.com/setup_12.x | bash - && \
  apt-get upgrade -y && \
  apt-get install -y nodejs texlive-latex-extra texlive-xetex && \
  rm -rf /var/lib/apt/lists/*

# Install Java
RUN apt-get update -y && \
    apt-get install default-jdk -y

# Install packages and extensions for JupyterLab
RUN pip install --upgrade pip && \
  pip install --upgrade \
    jupyterlab>=3.0.0 \
    ipywidgets \
    jupyter-lsp \
    python-language-server \
    jupyterlab-git \
    jupyter_bokeh \
    jupyterlab_widgets \
    jupyterlab_latex \
    jupyterlab-drawio \
    jupyterlab-lsp \
    'python-lsp-server[all]' \
    jupyterlab-git \
    jupyterlab-spreadsheet-editor \
    jupyter-dash
# from plotly documentation: install jupyter-dash

# Install SPARQL kernel
RUN pip install sparqlkernel
RUN jupyter sparqlkernel install 

# Install IJava kernel
RUN curl -L https://github.com/SpencerPark/IJava/releases/download/v1.3.0/ijava-1.3.0.zip > ijava-kernel.zip
RUN unzip ijava-kernel.zip -d ijava-kernel \
  && cd ijava-kernel \
  && python3 install.py --sys-prefix

# Install jupyter RISE extension (for IJava)
RUN pip install jupyter_contrib-nbextensions RISE \
  && jupyter-nbextension install rise --py --system \
  && jupyter-nbextension enable rise --py --system \
  && jupyter contrib nbextension install --system \
  && jupyter nbextension enable hide_input/main
RUN rm ijava-kernel.zip
RUN rm -rf ijava-kernel

# install python library
COPY requirements.txt .
RUN pip3 install --upgrade pip && \
    pip3 install --no-cache-dir -r requirements.txt \
    && rm -rf ~/.cache/pip

RUN jupyter lab build 

COPY bin/entrypoint.sh /usr/local/bin/
COPY config/jupyter_notebook_config.py /root/.jupyter/
# COPY config/ /root/.jupyter/

EXPOSE 9988
VOLUME /notebooks
WORKDIR /notebooks

ENTRYPOINT ["entrypoint.sh"]


