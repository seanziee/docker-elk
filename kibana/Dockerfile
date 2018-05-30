# https://github.com/elastic/kibana-docker
FROM docker.elastic.co/kibana/kibana-oss:6.2.4
USER root
# node and npm
RUN yum -y update
RUN yum -y install epel-release
RUN yum -y install nodejs
RUN yum -y install npm
#
# tools
RUN yum -y install net-tools
RUN yum -y install curl
RUN yum -y install git
RUN npm install -g bower

# Add your kibana plugins setup here
# Example: RUN kibana-plugin install <name|url>
# Time Picker
RUN mkdir -p /usr/share/kibana/plugins
WORKDIR /usr/share/kibana/plugins
RUN git clone https://github.com/nreese/kibana-time-plugin.git
WORKDIR /usr/share/kibana/plugins/kibana-time-plugin
RUN bower install --allow-root
RUN sed -i 's/"version": "kibana"/"version": "kibana-6.2.4"/g' package.json

# Transform plugin – for conversion funnel
WORKDIR /usr/share/kibana/plugins
RUN git clone https://github.com/PhaedrusTheGreek/transform_vis.git
WORKDIR /usr/share/kibana/plugins/transform_vis
RUN npm install
RUN sed -i 's/"version": "kibana"/"version": "kibana-6.2.4"/g' package.json

# Radar Visual
WORKDIR /usr/share/kibana/plugins
RUN git clone https://github.com/dlumbrer/kbn_radar.git -b 6-dev
WORKDIR /usr/share/kibana/plugins/kbn_radar
RUN npm install
RUN sed -i 's/"version": "kibana"/"version": "kibana-6.2.4"/g' package.json
