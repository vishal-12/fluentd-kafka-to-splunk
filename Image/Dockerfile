
FROM fluent/fluentd:v1.15.2-debian-amd64-1.0
MAINTAINER vibhu0891@gmail.com
USER root
RUN apt-get update && apt-get -y install
RUN apt-get -y install vim
RUN fluent-gem install fluent-plugin-kafka
RUN gem install fluent-plugin-splunk-hec --no-document

