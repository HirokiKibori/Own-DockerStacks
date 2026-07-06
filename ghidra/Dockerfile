# syntax=docker/dockerfile:1
FROM archlinux/archlinux:latest

WORKDIR /ghidra
RUN pacman -Syu --noconfirm

RUN pacman -S --noconfirm vim

RUN pacman -S --noconfirm xorg xorg-xinit
RUN pacman -S --noconfirm xf86-video-fbdev
RUN pacman -S --noconfirm i3-wm
ENV DISPLAY=:0 

COPY /etc/X11/xinit/xinitrc /root/.xinitrc
RUN echo "exec i3" >> /root/.xinitrc

# RUN pacman -Sy --noconfirm ghidra
# ENV JAVA_HOME=/usr/lib/jvm/default

EXPOSE 13100 13101 13102

# ENTRYPOINT ["startx"]
# CMD ["xeyes"]
# CMD ["i3"]
CMD ["/bin/sh"] 