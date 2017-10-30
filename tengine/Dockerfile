#构建命令docker build -t lorock/tengine .
#启用实例命令docker run -tid -p 80:80 lorock/tengine
#nginx配置文件默认文件夹/etc/nginx
#网站默认根目录为/www
#拉取基本镜像  
FROM lorock/centos
MAINTAINER xubaojin <lorock@qq.com>
#安装tengine
#特别注意此步骤，无需操作解压，否则会报错。
RUN yum install jemalloc jemalloc-devel pcre pcre-devel perl zlib zlib-devel ncurses-devel -y && yum clean all
ADD tengine-2.2.0.tar.gz /usr/local/src/
#wget http://tengine.taobao.org/download/tengine-2.2.0.tar.gz
#切换到源码目录
RUN cd /usr/local/src/tengine-2.2.0 && \
./configure \
--prefix=/usr/local/tengine --user=www \
--group=www --with-http_ssl_module \
--with-http_stub_status_module \
--with-http_gzip_static_module \
--with-jemalloc \
&& make install \
&& mkdir -p /usr/local/nginx/sbin/ \
&& ln -s /usr/local/tengine/sbin/nginx /usr/local/nginx/sbin/nginx \
&& ln -s /usr/local/tengine/conf/ /etc/nginx \
&& rm -v /usr/local/tengine/conf/nginx.conf
#配置tengine
ADD nginx.conf /usr/local/tengine/conf/
ADD index.html /www/
#Append "daemon off;" to the beginning of the configuration
RUN echo "daemon off;" >> /etc/nginx/nginx.conf && \
rm -rf /usr/local/src/* && \
yum clean all && \
mkdir -p /www && \
#配置 nginx 环境变量
echo 'export PATH=$PATH:/usr/local/nginx/sbin' >> /etc/profile
#ENV定义环境变量
ENV PATH /usr/local/nginx/sbin:$PATH 
#EXPOSE 映射端口
EXPOSE 80
CMD ["nginx"]