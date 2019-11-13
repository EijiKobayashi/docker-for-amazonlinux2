# FROM nginx:latest
FROM amazonlinux:2

RUN yum -y update

RUN yum -y install compat-gcc-48
RUN yum -y install compat-gcc-48-c++
RUN yum -y install gcc
RUN yum -y install gcc-c++
RUN yum -y install zlib-devel
RUN yum -y install make
RUN yum -y install wget
RUN yum -y install tar
RUN yum -y install php-devel
RUN yum -y install git
RUN yum -y install unzip
RUN yum -y install vim
RUN yum -y install unzip
RUN yum -y install curl
RUN yum -y install gnupg
RUN yum -y install libjpeg libjpeg-devel
RUN yum -y install libpng libpng-devel
RUN yum -y install freetype-devel
RUN yum -y install gd gd-devel
RUN yum -y install ImageMagick ImageMagick-devel

# install nginx
RUN amazon-linux-extras install nginx1.12

# automatic start
ENTRYPOINT ["/usr/sbin/nginx", "-g", "daemon off;"]
