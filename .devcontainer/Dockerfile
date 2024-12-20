# Use an official Rust image
FROM rust:latest

# Install additional dependencies if needed
RUN apt-get update && apt-get install -y \
    curl \
    git \
    build-essential \
    && apt-get clean

# Create a user and set up the working directory
ARG USERNAME=vscode
ARG USER_UID=1000
ARG USER_GID=$USER_UID
RUN groupadd --gid $USER_GID $USERNAME \
    && useradd --uid $USER_UID --gid $USER_GID -m $USERNAME \
    && apt-get update \
    && apt-get install -y sudo \
    && echo "$USERNAME ALL=(ALL) NOPASSWD:ALL" > /etc/sudoers.d/$USERNAME \
    && chmod 0440 /etc/sudoers.d/$USERNAME

USER $USERNAME
WORKDIR /workspace

# Set the default command for the container
CMD ["sleep", "infinity"]
