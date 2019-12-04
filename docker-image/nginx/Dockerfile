FROM amazonlinux:2

RUN yum update -y

RUN yum install -y glibc-langpack-ja \
  unlink /etc/localtime \
  ln -s /usr/share/zoneinfo/Japan /etc/localtime \
  echo "LANG=ja_JP.UTF-8" | tee /etc/sysconfig/i18n

RUN ln -sf /usr/share/zoneinfo/Asia/Tokyo /etc/localtime \
  echo -e 'ZONE="Asia/Tokyo"\nUTC=true' | tee /etc/sysconfig/clock

RUN mkdir -p /var/www/html/

RUN amazon-linux-extras install -y nginx1.12

ENTRYPOINT /usr/sbin/nginx -g 'daemon off;' -c /etc/nginx/nginx.conf

# COPY ./default.conf /etc/nginx/conf.d/default.conf
# COPY ./nginx.conf /etc/nginx/nginx.conf
