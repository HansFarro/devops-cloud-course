FROM jenkins/ssh-agent:jdk17

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
        git \
        maven && \
    rm -rf /var/lib/apt/lists/*