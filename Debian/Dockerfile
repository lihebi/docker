FROM debian:testing
ENV DEBIAN_FRONTEND noninteractive
# essentail
RUN apt-get update && apt-get install -y \
  emacs build-essential tmux exuberant-ctags \
  global cmake libsqlite3-dev \
  sudo git \
  cifs-utils \
  sqlite3

RUN apt-get update && apt-get install -y \
  openssh-server

RUN apt-get update && apt-get install -y \
  locate

RUN apt-get update && apt-get install -y \
  rxvt-unicode-256color
# optional
# RUN apt-get update && apt-get install -y \
#   graphviz \
#   curl \
#   openjdk-8-jdk \

# RUN apt-get update && apt-get install -y \
#   llvm clang

# RUN apt-get update && apt-get install -y \
#   texlive-full

RUN mkdir /var/run/sshd
# RUN echo X11Forwarding yes >> /etc/ssh/ssh_config

# ADD . /src
# RUN groupadd -r hebi && useradd -m -g hebi hebi
RUN echo 'root:hebijk' | chpasswd

RUN useradd -m hebi
# RUN groupadd -g sudo hebi
RUN usermod -aG sudo hebi
RUN echo 'hebi:hebijk' | chpasswd
RUN chsh -s /bin/bash hebi

# CMD ["/bin/bash", "/src/startup.sh"]
EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]
