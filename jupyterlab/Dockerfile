# Use archlinux:latest as parent image
FROM archlinux:latest

# Update mirrors and packages. Install jupyterlab
RUN pacman --noconfirm -Syyu python-pip jupyterlab neovim-git nvm

# nvm source
RUN echo "source /usr/share/nvm/init-nvm.sh" >> ~/.bashrc

ENV JUPYTERLAB_DIR /appdata/lab

# Build the lab
RUN jupyter lab build --minimize=False

# Expose port and path
EXPOSE 9988
VOLUME /appdata


# Run JupyterLab
CMD cp -R -n /usr/share/jupyter/* /appdata && jupyter lab --ip=* --port=9988 --no-browser --notebook-dir=/opt/app/data --allow-root