FROM ubuntu:24.04

RUN apt-get update && apt-get install -y curl ca-certificates

WORKDIR /app

EXPOSE 8080

COPY greet .

CMD ["./greet"]
