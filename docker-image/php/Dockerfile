FROM amazonlinux:2

RUN yum update -y

RUN yum install -y glibc-langpack-ja \
  unlink /etc/localtime \
  ln -s /usr/share/zoneinfo/Japan /etc/localtime \
  echo "LANG=ja_JP.UTF-8" | tee /etc/sysconfig/i18n

RUN ln -sf /usr/share/zoneinfo/Asia/Tokyo /etc/localtime \
  echo -e 'ZONE="Asia/Tokyo"\nUTC=true' | tee /etc/sysconfig/clock

#RUN yum -y reinstall glibc-common
#RUN localedef -f UTF-8 -i ja_JP ja_JP.UTF-8
#ENV LANG="ja_JP.UTF-8" \
#  LANGUAGE="ja_JP:ja" \
#  LC_ALL="ja_JP.UTF-8"

RUN amazon-linux-extras install -y php7.2
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
RUN yum -y install gzip
RUN yum -y install vim
RUN yum -y install unzip
RUN yum -y install curl
RUN yum -y install gnupg
RUN yum -y install libjpeg libjpeg-devel
RUN yum -y install libpng libpng-devel
RUN yum -y install freetype-devel
RUN yum -y install gd gd-devel
RUN yum -y install ImageMagick ImageMagick-devel
RUN yum -y install php-opcache
RUN yum -y install libmemcached
RUN yum -y install memcached

RUN yum -y install php-cli \
  php-common \
  php-fpm \
  php-json \
  php-mysqlnd \
  php-pdo \
  php \
  php-devel \
  php-gd \
  php-intl \
  php-mbstring \
  php-pecl-imagick \
  php-pear \
  php-pecl-imagick-devel \
  php-pecl-zip \
  php-xml \
  php-xmlrpc

### libxdiffを導入
RUN cd ~/ && \
  wget 'http://www.xmailserver.org/libxdiff-0.23.tar.gz' && \
  tar -xvzf libxdiff-0.23.tar.gz && \
  cd libxdiff-0.23 && \
  ./configure && \
  make && \
  make install

RUN cd ~/ && \
  wget 'https://pecl.php.net/get/xdiff-2.0.1.tgz' && \
  tar -xvzf xdiff-2.0.1.tgz && \
  cd xdiff-2.0.1 && \
  phpize && \
  ./configure && \
  make && \
  make install

### QDBMを導入
RUN cd ~/ && \
  wget 'http://qdbm.sourceforge.net/qdbm-1.8.77.tar.gz' && \
  tar -zxvf qdbm-1.8.77.tar.gz && \
  cd qdbm-1.8.77/ && \
  CC=gcc48 ./configure --enable-zlib && \
  make && \
  make install

### HyperEstraierを導入
RUN cd ~/ && \
  wget 'https://fallabs.com/hyperestraier/hyperestraier-1.4.13.tar.gz' && \
  tar -zxvf hyperestraier-1.4.13.tar.gz && \
  cd hyperestraier-1.4.13/ && \
  ./configure && \
  make && \
  make install

### MeCabを導入
RUN cd ~/ && \
  wget 'https://drive.google.com/uc?export=download&id=0B4y35FiV1wh7cENtOXlicTFaRUE' -O mecab-0.996.tar.gz && \
  tar -zxvf mecab-0.996.tar.gz && \
  cd mecab-0.996/ && \
  ./configure --with-charset=utf8 && \
  make && \
  make install

### IPA辞書を導入
RUN cd ~/ && \
  wget 'https://drive.google.com/uc?export=download&id=0B4y35FiV1wh7MWVlSDBCSXZMTXM' -O mecab-ipadic-2.7.0-20070801.tar.gz && \
  tar zxfv mecab-ipadic-2.7.0-20070801.tar.gz && \
  cd mecab-ipadic-2.7.0-20070801 && \
  ./configure --with-charset=utf8 && \
  make && \
  make install

### php-macabをインストール
RUN cd ~/ && \
  git clone https://github.com/rsky/php-mecab.git && \
  cd php-mecab/mecab/ && \
  phpize && \
  ./configure --with-mecab=/root/mecab-0.996/mecab-config && \
  make && \
  make test && \
  make install
COPY ./mecab.ini /etc/php.d/mecab.ini

EXPOSE 9000

# run php-fpm in the foreground
ENTRYPOINT /usr/sbin/php-fpm -F

# COPY ./www.conf /etc/php-fpm.d/www.conf
COPY ./php.ini /etc/php.ini
