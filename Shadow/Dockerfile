FROM ros:indigo-ros-core

# install goblin packages
COPY pygoblin/src/goblin        \
     /opt/ros/indigo/lib/python2.7/dist-packages/goblin/

COPY illuminant/src/illuminant  \
     /opt/ros/indigo/lib/python2.7/dist-packages/illuminant/

COPY rosshadow/src/rosshadow    \
     /opt/ros/indigo/lib/python2.7/dist-packages/rosshadow

# install bin
COPY patches/bin/illuminant     \
     /opt/ros/indigo/bin

COPY rosshadow/src/main.py     \
     /opt/ros/indigo/bin/rosshadow

RUN chmod +x /opt/ros/indigo/bin/rosshadow

# modify entrypoint
COPY patches/entrypoint/shadow_entrypoint.bash \
     /

ENTRYPOINT ["/shadow_entrypoint.bash"]

# run bash as default
CMD ["bash"]
