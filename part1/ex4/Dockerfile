FROM ubuntu:16.04

WORKDIR /mydir
COPY skripti.sh .
RUN apt-get update && apt-get install -y curl
CMD ./skripti.sh