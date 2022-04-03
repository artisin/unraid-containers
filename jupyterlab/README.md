# Unraid - JupyterLab

**Links**
+ @repo: [https://github.com/jupyterlab/jupyterlab](https://github.com/jupyterlab/jupyterlab)
+ @wiki: [https://jupyterlab.readthedocs.io/en/stable/](https://jupyterlab.readthedocs.io/en/stable/)
+ @pkg: [https://github.com/artisin/unraid-containers/pkgs/artisin/unraid-containers](https://github.com/artisin/unraid-containers/pkgs/artisin/unraid-containers)

**Notes**

container runs as root user,  helpful with jupyter/datascience-notebook


#### Installed kernels

* Python 3.10 with autocomplete and suggestions ([LSP](https://github.com/krassowski/jupyterlab-lsp))
* [IJava](https://github.com/SpencerPark/IJava)
* [SPARQL kernel](https://github.com/paulovn/sparql-kernel)

#### Installed Jupyterlab extensions

- Additional packages via `requirements.txt`
- [Jupyter Widgets](https://ipywidgets.readthedocs.io/en/latest/examples/Widget%20Basics.html)
- [@jupyterlab/git](https://www.npmjs.com/package/@jupyterlab/git)
- [@krassowski/jupyterlab-lsp](https://github.com/krassowski/jupyterlab-lsp)
- [@jupyterlab/latex](https://github.com/jupyterlab/jupyterlab-latex)
- [jupyterlab-plotly](https://www.npmjs.com/package/jupyterlab-plotly)
- [jupyterlab-drawio](https://github.com/QuantStack/jupyterlab-drawio)
- [jupyterlab-spreadsheet](https://github.com/quigleyj97/jupyterlab-spreadsheet)
- [@bokeh/jupyter_bokeh](https://github.com/bokeh/jupyter_bokeh)
- [@jupyterlab/toc](https://www.npmjs.com/package/@jupyterlab/toc)

### Your notebooks

Volumes can be mounted into `/notebooks` folder.

The container will install requirements from files present in the `/notebooks` folder when it starts up (in this order):

- `packages.txt`: install apt-get packages
- `requirements.txt`: install pip packages
- `extensions.txt`: install JupyterLab extensions


