FROM jenkins/ssh-agent:jdk21

# Instalar Docker CLI
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
        git \
        maven \
        ca-certificates \
        curl \
        gnupg && \
    # Configurar repositorio de Docker
    install -m 0755 -d /etc/apt/keyrings && \
    curl -fsSL https://download.docker.com/linux/debian/gpg | gpg --dearmor -o /etc/apt/keyrings/docker.gpg && \
    chmod a+r /etc/apt/keyrings/docker.gpg && \
    echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/debian \
        $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | tee /etc/apt/sources.list.d/docker.list > /dev/null && \
    apt-get update && \
    apt-get install -y docker-ce-cli && \
    # Crear grupo docker con mismo GID que el host
    groupadd -g 998 docker && \
    usermod -aG docker jenkins && \
    # Limpiar
    rm -rf /var/lib/apt/lists/*

# Agregar usuario jenkins al grupo docker
RUN usermod -aG docker jenkins
