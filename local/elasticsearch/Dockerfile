# Using centos7 image
FROM centos:centos7 

# Set the application directory
WORKDIR /app

# Copy files to container from host .
COPY elasticsearch.yml ./

# Install dependencies.(RUN = exec when docker image is created from dockerfile.)
RUN yum update -y \
    && yum install -y java-11-openjdk \
    && yum install -y wget \
    && wget https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-7.6.2-x86_64.rpm \
    && rpm --install elasticsearch-7.6.2-x86_64.rpm \
    && mv elasticsearch.yml /etc/elasticsearch/elasticsearch.yml \
    && /usr/share/elasticsearch/bin/elasticsearch-plugin install analysis-kuromoji \
    && /bin/systemctl enable elasticsearch.service \
    && yum clean all

RUN /usr/share/elasticsearch/bin/elasticsearch-users useradd esroot -p esroot123 -r superuser

# Restart service. (CMD = exec when docker container is created from docker image.)
#CMD ["systemctl", "restart", "elasticsearch.service"]
