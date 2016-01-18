FROM ros:indigo-ros-core

# install docker-py
RUN easy_install docker-py

# install iptables
RUN apt-get update
RUN apt-get -y install iptables

# install goblin packages
COPY pygoblin/src/goblin        \
     /opt/ros/indigo/lib/python2.7/dist-packages/goblin/

COPY illuminant/src/illuminant  \
     /opt/ros/indigo/lib/python2.7/dist-packages/illuminant/

# install bin
COPY illuminant/bin/daemon.py   \
     /opt/ros/indigo/bin/gldaemon

# modify entrypoint
COPY patches/entrypoint/daemon_entrypoint.bash \
     /

ENTRYPOINT ["/daemon_entrypoint.bash"]

# exposing illuminant
EXPOSE 30000

# run bash as default
CMD ["bash"]
