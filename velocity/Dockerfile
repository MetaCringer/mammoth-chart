FROM redhat/ubi8
RUN \
  groupadd -g 1001 velocity && \
  useradd -mu 1001 -g velocity velocity
RUN chmod 777 /tmp
RUN dnf install -y java-17-openjdk
COPY --chown=1001:1001 docker-entrypoint.sh /
WORKDIR  /app
RUN chown 1001:1001 ./
COPY --chown=1001:1001 velocity*.jar velocity.jar
COPY --chown=1001:1001 velocity.toml .
USER velocity
RUN echo eula=true > eula.txt
RUN ls -la
EXPOSE 25565
ENTRYPOINT ["/docker-entrypoint.sh"]