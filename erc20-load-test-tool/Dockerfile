# From Ubuntu:21.10 as the base image.
FROM ubuntu:impish

# Description of the container image.
LABEL description="VMware Blockchain Starter Kit - ERC20 Load Test Tool"

# Copy the erc20 code to the container image.
COPY . /workspace/erc20-load-test-tool

# Install dependencies for running the application.
RUN apt-get autoremove && apt-get autoclean -y && apt-get -yy update
# Installing bash for running the script.
RUN apt-get -y install bash
# Installing openjdk11.
RUN apt-get install -yy -q openjdk-11-jdk
# Installing python3 and pip.
RUN apt-get install -y python3 && apt-get install -y python3-pip
# Installing wget for downloading maven 3.8.1.
RUN apt-get -yy -q install wget
# Installing maven-3.8.1.
RUN wget https://archive.apache.org/dist/maven/maven-3/3.8.1/binaries/apache-maven-3.8.1-bin.tar.gz && tar xzvf apache-maven-3.8.1-bin.tar.gz
# Setting maven path.
ENV PATH=/apache-maven-3.8.1/bin:$PATH
# Installing python requirements for running the application.
RUN pip install -r /workspace/erc20-load-test-tool/script/requirements.txt

# Changing work directory to be used by the startup script.
WORKDIR /workspace/erc20-load-test-tool/script

CMD bash /workspace/erc20-load-test-tool/script/run.sh && tail -f -n +1 /workspace/erc20-load-test-tool/script/nohup.out

# env file is mounted when running the container with user values entered by the user for the run.
# -v {ABS_PATH}/env_file:/.env
