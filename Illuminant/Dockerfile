FROM ros:indigo-ros-core

# install docker-py
RUN easy_install docker-py

# install goblin packages
COPY pygoblin/src/goblin/       \
     illuminant/src/illuminant  \
     rosshadow/src/rosshadow    \
     /opt/ros/indigo/lib/python2.7/dist-packages/

# install bin
COPY patches/bin/illuminant     \
     /opt/ros/indigo/bin

# patch roslaunch
# using patched files as there is no patch tool in upstream image...
COPY patches/*.py $RLROOT       \
     /opt/ros/indigo/lib/python2.7/dist-packages/roslaunch/

# modify entrypoint
COPY patches/entrypoint/illuminant_entrypoint.bash /
ENTRYPOINT ["/illuminant_entrypoint.bash"]

# exposing illuminant
EXPOSE 11311

# run bash as default
CMD ["bash"]
