# Using centos7 image
FROM centos:centos7 

# Set the application directory
WORKDIR /app

# Copy files to container from host .
COPY elasticsearch.yml ./

# Install dependencies.(RUN = exec when docker image is created from dockerfile.)
RUN yum update -y \
    && yum install -y java-11-openjdk \
    && curl -L -O https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-7.6.2-x86_64.rpm \
    && rpm --install elasticsearch-7.6.2-x86_64.rpm \
    && cp -pi /etc/elasticsearch/elasticsearch.yml /etc/elasticsearch/elasticsearch.yml.org\
    && mv elasticsearch.yml /etc/elasticsearch/elasticsearch.yml \
    && /usr/share/elasticsearch/bin/elasticsearch-plugin install analysis-kuromoji \
    && /bin/systemctl enable elasticsearch.service \
    && yum clean all

# Ref Roles: https://www.elastic.co/guide/en/elasticsearch/reference/current/built-in-roles.html
RUN /usr/share/elasticsearch/bin/elasticsearch-users useradd esroot -p esroot123 -r superuser \
    && /usr/share/elasticsearch/bin/elasticsearch-users useradd kibanaroot -p kibanaroot123 -r kibana_system \
    && /usr/share/elasticsearch/bin/elasticsearch-users useradd apmroot -p apmroot123 -r apm_system

# Restart service. (CMD = exec when docker container is created from docker image.)
#CMD ["systemctl", "restart", "elasticsearch.service"]
