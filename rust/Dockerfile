FROM ubuntu:latest

RUN apt-get update && apt-get install -y \
    build-essential \
    curl \
    lldb \
    vim

ENV PATH="/root/.cargo/bin:$PATH"

WORKDIR /code
