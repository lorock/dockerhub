#构建命令docker build -t lorock/centos .
#启用实例命令docker run -tid lorock/centos
#nginx配置文件默认文件夹/etc/nginx
#网站默认根目录为/www
#拉取基本镜像  
FROM centos:6.9
MAINTAINER xubaojin <lorock@qq.com>
#设置默认语言
ENV LANG en_US.UTF-8
ENV LANGUAGE en_US:en  
ENV LC_ALL en_US.UTF-8 
#设置为北京时间
RUN /bin/cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime \
#添加运行用户和组WWW,ID为8388
&& groupadd www -g 8388 && useradd -g www www -u 8388 -s /sbin/nologin \
&& yum update -y \
&& yum -y install epel-release gcc gcc-c++ make cmake aotomake autoconf libtool openssl openssl-devel \
&& yum clean all
