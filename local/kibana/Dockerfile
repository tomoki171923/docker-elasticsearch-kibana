# Using centos7 image
FROM centos:centos7 

# Set the application directory
WORKDIR /app

# Copy files to container from host .
COPY kibana.yml ./

# Install dependencies.(RUN = exec when docker image is created from dockerfile.)
RUN yum update -y \
    && yum install -y java-11-openjdk \
    && yum install -y wget \
    && wget https://artifacts.elastic.co/downloads/kibana/kibana-7.6.2-x86_64.rpm \
    && rpm --install kibana-7.6.2-x86_64.rpm \
    && mv kibana.yml /etc/kibana/kibana.yml \
    && /bin/systemctl enable kibana.service \
    && yum clean all

# Restart service. (CMD = exec when docker container is created from docker image.)
#CMD ["systemctl", "restart", "kibana.service"]
