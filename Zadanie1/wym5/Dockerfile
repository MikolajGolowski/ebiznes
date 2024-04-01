FROM ubuntu:22.04

ENV TZ=Europe/Warsaw
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

# instalacja pythona 3.8, javy, kotlina
RUN apt-get update && \
    apt-get install -y software-properties-common && \
    add-apt-repository ppa:deadsnakes/ppa && \
    apt-get update && \
    apt-get install -y python3.8 python3-pip openjdk-8-jdk wget unzip zip

RUN wget https://github.com/JetBrains/kotlin/releases/download/v1.9.23/kotlin-compiler-1.9.23.zip && \
    unzip kotlin-compiler-1.9.23.zip -d /usr/local && \
    rm kotlin-compiler-1.9.23.zip

# dodanie kotlina do path
ENV PATH="${PATH}:/usr/local/kotlinc/bin"

RUN wget https://services.gradle.org/distributions/gradle-8.1-bin.zip && \
    mkdir /opt/gradle && \
    unzip -d /opt/gradle gradle-8.1-bin.zip && \
    export PATH=$PATH:/opt/gradle/gradle-8.1/bin

ENV GRADLE_HOME=/opt/gradle/gradle-8.1
ENV PATH=$PATH:$GRADLE_HOME/bin

WORKDIR /app
RUN gradle init \
  --type kotlin-application \
  --dsl kotlin 
  
# COPY HelloWorld.kt /app/src/kotlin
# COPY build.gradle.kts /app/
# COPY settings.gradle /app/

RUN ./gradlew build
# CMD ["java","-jar","run.jar"]