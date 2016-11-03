FROM alpine:3.4
MAINTAINER Oscar Perez Fuentes <oscar@xmltravelgate.com>

#
# Follow the server installation parameters specified on the OSSEC website for
# ubuntu installations
#
RUN apt-key adv --fetch-keys http://ossec.wazuh.com/repos/apt/conf/ossec-key.gpg.key &&\
  echo "deb http://ossec.wazuh.com/repos/apt/ubuntu xenial main" >> /etc/apt/sources.list &&\
  apt-get update && DEBIAN_FRONTEND=noninteractive apt-get -yf install expect ossec-hids \
  ossec-hids=2.8.3-4trusty

#
# Add a default agent due to this bug
# https://groups.google.com/forum/#!topic/ossec-list/qeC_h3EZCxQ
#
ADD default_agent /var/ossec/default_agent
RUN service ossec restart &&\
  /var/ossec/bin/manage_agents -f /default_agent &&\
  rm /var/ossec/default_agent &&\
  service ossec stop &&\
  echo -n "" /var/ossec/logs/ossec.log



##Elastic FileBeat configuration





#
# Initialize the data volume configuration
#
ADD data_dirs.env /data_dirs.env
ADD init.bash /init.bash
# Sync calls are due to https://github.com/docker/docker/issues/9547
RUN chmod 755 /init.bash &&\
  sync && /init.bash &&\
  sync && rm /init.bash

#
# Add the bootstrap script
#
ADD run.bash /run.bash
RUN chmod 755 /run.bash

#
# Specify the data volume
#
VOLUME ["/var/ossec/data"]

# Expose ports for sharing (Ossec ports)
EXPOSE 1514/udp 1515/tcp

#
# Define default command.
#
ENTRYPOINT ["/run.bash"]