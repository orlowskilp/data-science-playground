ARG VERSION

FROM archlinux:${VERSION}

# Every argument other than VERSION is set after FROM
ARG USERNAME
ARG HOME_DIR=/home/${USERNAME}
ARG VENV=.env
ARG VENV_DIR=${HOME_DIR}/${VENV}
ARG VENV_ACTIVATE=${VENV_DIR}/bin/activate

# Create a non-root user
RUN useradd -ms /bin/bash -G wheel ${USERNAME}
# Install packages
RUN pacman -Suy --noconfirm \
    docker \
    git \
    python \
# Add `sudo` for convenience
    sudo && \
# Clear the package cache
    pacman -Scc
# Allow `sudo` without password for the non-root user
RUN echo "${USERNAME} ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers
# Create Python virtual environment
RUN python -m venv ${VENV_DIR} && \
# Acvitave the virtual environment for site packages installation
    . ${VENV_ACTIVATE} && \
    python -m pip install --upgrade pip && \
# --- Install packages here ---
    python -m pip install \
        wheel \
        jupyter \
        ipykernel \
        matplotlib \
        numpy \
        pandas \
        scikit-learn \
        seaborn \
        keras \
        tensorflow
# -----------------------------
# Move the virtual environment to the non-root user's home directory and activate it on new shell
RUN chown ${USERNAME}:${USERNAME} -R ${VENV_DIR} && \
    echo ". ${VENV_ACTIVATE}" >> ${HOME_DIR}/.bashrc
# Switch to the non-root user
USER ${USERNAME}