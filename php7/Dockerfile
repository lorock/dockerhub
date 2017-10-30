#Docker php7 image
#构建命令docker build -t lorock/php7-abao .
#docker run -tid -p 9000:9000 lorock/php7-abao /bin/bash
#Pull base image 
FROM lorock/centos
MAINTAINER xubaojin <lorock@qq.com>
RUN yum -y install php-mcrypt libmcrypt libmcrypt-devel php-pear libxml2 libxml2-devel curl curl-devel \
libjpeg libjpeg-devel libpng libpng-devel freetype freetype-devel && yum clean all
ADD php-7.0.18.tar.gz /usr/local/src/
RUN cd /usr/local/src/php-7.0.18 && \
./configure --prefix=/usr/local/php \
--with-config-file-path=/usr/local/php/ \
--enable-fpm  \
--with-mysqli=mysqlnd \
--with-pdo-mysql=mysqlnd \
--with-iconv-dir \
--with-freetype-dir \
--with-jpeg-dir \
--with-png-dir \
--with-zlib \
--with-libxml-dir=/usr \
--enable-xml \
--disable-rpath \
--enable-bcmath \
--enable-shmop \
--enable-sysvsem \
--enable-inline-optimization \
--with-curl \
--enable-mbregex \
--enable-mbstring \
--with-mcrypt \
--enable-ftp \
--with-gd \
--enable-gd-native-ttf \
--with-openssl \
--with-mhash \
--enable-pcntl \
--enable-sockets \
--with-xmlrpc \
--enable-zip \
--enable-soap \
--without-pear \
--with-gettext \
--disable-fileinfo \
--enable-maintainer-zts && \
make && make install
ADD php-fpm.conf /usr/local/php/etc/php-fpm.conf
ADD php.ini /usr/local/php/php.ini
ADD php-fpm /usr/local/bin/php-fpm
RUN chmod 755 /usr/local/bin/php-fpm && rm -rf /usr/local/src/*
#EXPOSE
EXPOSE 9000
WORKDIR /root/
#容器运行后默认执行的指令
CMD ["php-fpm","start"]
