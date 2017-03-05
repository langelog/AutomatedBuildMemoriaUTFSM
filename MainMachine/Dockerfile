FROM ubuntu:16.04
MAINTAINER Luis Gonzalez <langelog@me.com>

# Updating base repo
RUN apt update

# installing essentials
RUN apt install openssl -y
RUN apt install sudo -y
RUN apt install texlive-full -y
# some not essentials but might be usefull
RUN apt install rubber -y 

# Configuring user
ENV username memorista
ENV userpass memorista

RUN groupadd $username
RUN useradd -u 12345 -g $username -d /home/$username -s /bin/bash -p $(echo $userpass | openssl passwd -1 -stdin) $username
RUN mkdir /home/$username
RUN cp -rT /etc/skel /home/$username
RUN chown -R $username:$username /home/$username

RUN adduser $username sudo





# finishing some configs
WORKDIR /home/$username
CMD /bin/bash
USER $username

