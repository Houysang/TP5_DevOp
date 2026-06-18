FROM ubuntu:22.04

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && apt-get install -y \
    apache2 \
    openssh-server \
    git \
    curl \
    php \
    libapache2-mod-php \
    tzdata \
    && rm -rf /var/lib/apt/lists/*

# avoid tzdata prompt
RUN ln -fs /usr/share/zoneinfo/Asia/Phnom_Penh /etc/localtime && \
    dpkg-reconfigure -f noninteractive tzdata

RUN mkdir /var/run/sshd

EXPOSE 22 80

CMD service apache2 start && /usr/sbin/sshd -D