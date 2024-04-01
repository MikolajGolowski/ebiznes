FROM ubuntu:22.04

ENV TZ=Europe/Warsaw
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

# instalacja pythona 3.8, javy, kotlina
RUN apt-get update && \
    apt-get install -y software-properties-common && \
    add-apt-repository ppa:deadsnakes/ppa && \
    apt-get update && \
    apt-get install -y python3.8 python3-pip openjdk-8-jdk wget unzip

RUN wget https://github.com/JetBrains/kotlin/releases/download/v1.4.32/kotlin-compiler-1.4.32.zip && \
    unzip kotlin-compiler-1.4.32.zip -d /usr/local && \
    rm kotlin-compiler-1.4.32.zip

ENV PATH="${PATH}:/usr/local/kotlinc/bin"