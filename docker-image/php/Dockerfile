FROM amazonlinux:2

RUN yum update -y

RUN yum install -y glibc-langpack-ja \
  unlink /etc/localtime \
  ln -s /usr/share/zoneinfo/Japan /etc/localtime \
  echo "LANG=ja_JP.UTF-8" | tee /etc/sysconfig/i18n

RUN ln -sf /usr/share/zoneinfo/Asia/Tokyo /etc/localtime \
  echo -e 'ZONE="Asia/Tokyo"\nUTC=true' | tee /etc/sysconfig/clock

# install php7.2
RUN amazon-linux-extras install -y php7.2

# use php-fpm default tcp
EXPOSE 9000

# run php-fpm in the foreground
ENTRYPOINT /usr/sbin/php-fpm -F

# COPY ./www.conf /etc/php-fpm.d/www.conf
COPY ./php.ini /usr/local/etc/php/php.ini
