# Run pidgin desktop app in a container with
# support for Skype for Business screen sharing
# audio and video calls
#
# docker run --rm -it \
#	-v /etc/localtime:/etc/localtime:ro \
#	-v /tmp/.X11-unix:/tmp/.X11-unix \
#	-e DISPLAY=unix$DISPLAY \
#	--device /dev/snd \
#	--device /dev/dri \
#	--device /dev/video0 \
#	--group-add audio \
#	--group-add video \
#	-v "${HOME}/.purple:/root/.purple" \
#	--ipc="host" \
#	--name pidgin \
#	pidgin

FROM ubuntu:16.04
LABEL maintainer "Alexandre Thenorio"

RUN apt-key adv --keyserver keyserver.ubuntu.com --recv-keys B5F8E4AE1D98D67FC02DF926737F9811F93FF666 \
    && echo "deb http://ppa.launchpad.net/sipe-collab/stable/ubuntu xenial main" >> /etc/apt/sources.list.d/pidgin.list \
    && apt-get update && apt-get install -y \
    pidgin \
    pidgin-sipe \
    && rm -rf /var/lib/apt/lists/*

ENV LANG en-US

ENTRYPOINT ["/usr/bin/pidgin"]