FROM redhat/ubi8
RUN \
  groupadd -g 1001 mcserver && \
  useradd -mu 1001 -g mcserver mcserver
RUN chmod 777 /tmp
RUN dnf install -y java-17-openjdk
RUN dnf install -y net-tools 
#TODO ^^
COPY --chown=1001:1001 docker-entrypoint.sh /
WORKDIR  /app
RUN chown 1001:1001 ./
COPY --chown=1001:1001 patina*.jar patina.jar
COPY --chown=1001:1001 config/ ./
USER mcserver
RUN echo eula=true > eula.txt
RUN ls -la
EXPOSE 25566-25666
EXPOSE 29000-30000
ENTRYPOINT ["/docker-entrypoint.sh"]
