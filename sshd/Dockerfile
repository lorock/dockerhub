FROM       ubuntu:16.04
MAINTAINER Lorock.Xu "https://github.com/lorock"
ENV LANG=en_US.UTF-8
ENV LC_ALL=en_US.UTF-8
ENV TZ=Asia/Shanghai
RUN apt-get update \
&& apt-get install -y openssh-server \
&& mkdir /var/run/sshd \
&& echo 'root:root' |chpasswd \
&& sed -ri 's/^PermitRootLogin\s+.*/PermitRootLogin yes/' /etc/ssh/sshd_config \
&& sed -ri 's/^#AuthorizedKeysFile/AuthorizedKeysFile/g' /etc/ssh/sshd_config \
&& sed -ri 's/UsePAM yes/#UsePAM yes/g' /etc/ssh/sshd_config
EXPOSE 22
CMD    ["/usr/sbin/sshd", "-D"]
