FROM python:3-slim
COPY --from=docker.io/astral/uv:latest /uv /uvx /bin/


ARG USERNAME
ARG USER_UID=1000
ARG USER_GID=$USER_UID
RUN groupadd --gid $USER_GID $USERNAME \
    && useradd --uid $USER_UID --gid $USER_GID -m $USERNAME -s /bin/zsh \
    && apt update && apt install -y git curl wget unzip zsh \
    && apt clean && rm -rf /var/lib/apt/lists/*

USER $USERNAME

# Se crea el directorio .local/bin y se agrega al PATH
ENV PATH="/home/${USERNAME}/.local/bin:${PATH}"
ENV UV_PROJECT_ENVIRONMENT="/home/${USERNAME}/.virtualenvs/uv"
RUN mkdir -p /home/${USERNAME}/.local/bin

# se deja el workdir en /workspace
WORKDIR /workspace

# se instala oh-my-posh y se configura zsh con el theme kushal
RUN curl -s https://ohmyposh.dev/install.sh | bash && \
    echo 'eval "$(oh-my-posh init zsh --config ${HOME}/.cache/oh-my-posh/themes/kushal.omp.json)"' >> ${HOME}/.zshrc

# Se agrega el compinit para zsh
RUN echo 'autoload -Uz compinit && compinit -i' >> ${HOME}/.zshrc
RUN uv tool install httpie