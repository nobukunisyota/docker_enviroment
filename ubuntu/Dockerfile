FROM --platform=linux/amd64 ubuntu:latest

RUN apt update -y
RUN apt install -y sudo make vim openjdk-18-jdk
RUN useradd -m -s /bin/bash nobukuni
RUN echo "nobukuni:nobukuni" | chpasswd
RUN gpasswd -a nobukuni sudo

USER nobukuni

WORKDIR /home/nobukuni/
