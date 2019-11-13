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

# install php7.2
RUN amazon-linux-extras install php7.2 -y

# use php-fpm default tcp
EXPOSE 9000

# run php-fpm in the foreground
ENTRYPOINT /usr/sbin/php-fpm -F

RUN yum -y install php-cli \
  php-common \
  php-fpm \
  php-json \
  php-mysqlnd \
  php-pdo \
  php-devel \
  php-gd \
  php-intl \
  php-mbstring \
  php-pecl-imagick \
  php-pecl-imagick-devel \
  php-pecl-zip \
  php-xml \
  php-xmlrpc

# put config
COPY ./www.conf /etc/php-fpm.d/www.conf
COPY ./php.ini /usr/local/etc/php/php.ini
