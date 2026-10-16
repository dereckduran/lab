# allows dynamic ubuntu versions from the terminal: `docker build --build-arg UBUNTU_VERSION=22.04 -t my_app .
ARG UBUNTU_VERSION=24.04
FROM ubuntu:${UBUNTU_VERSION}

WORKDIR /app

COPY backup .

RUN chmod +x backup

ENTRYPOINT ["./backup"]
CMD ["list"]
