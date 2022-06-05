# syntax=docker/dockerfile:1.3

# ---
# Runtime
FROM debian:11-slim
WORKDIR /

# Setup non-root user
RUN \
  groupadd -g 1001 worldql && \
  useradd -mu 1001 -g worldql worldql

RUN apt-get update && apt-get install -y net-tools 

# Copy application
COPY --chown=1001:1001 worldql_server_linux_x86 .

# Define repo label
ARG GIT_REPO
LABEL org.opencontainers.image.source=${GIT_REPO}

# Expose default ports
EXPOSE 5555
EXPOSE 8080
EXPOSE 8081

# Define user and entrypoint
USER worldql
ENTRYPOINT ["/worldql_server_linux_x86"]
