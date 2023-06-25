FROM ubuntu:latest

# Install dependencies
RUN apt-get update && apt-get install -y \
    openjdk-8-jre-headless \
    openjdk-8-jdk \
    wget \
    nano \
    python3-pip

# Download and extract Spark
RUN cd home \
    && mkdir Downloads \
    && cd Downloads \
    && wget https://dlcdn.apache.org/spark/spark-3.4.1/spark-3.4.1-bin-hadoop3.tgz \
    && tar xvzf spark-3.4.1-bin-hadoop3.tgz \
    && rm spark-3.4.1-bin-hadoop3.tgz \
    && mv spark-3.4.1-bin-hadoop3 /usr/local/spark

# Set environment variables
ENV SPARK_HOME=/usr/local/spark
ENV PATH=$PATH:$SPARK_HOME/bin
ENV PYSPARK_PYTHON=/usr/bin/python3.10
ENV PYSPARK_DRIVER_PYTHON=/usr/bin/python3.10
# Set the working directory
WORKDIR /app

# Copy your application code (if any)
# COPY app.py .

# Start the PySpark shell
CMD ["pyspark"]
