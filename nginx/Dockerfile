# FROM nginx:latest
FROM amazonlinux:2

RUN yum -y update

# install nginx
RUN amazon-linux-extras install nginx1.12

# automatic start
ENTRYPOINT ["/usr/sbin/nginx", "-g", "daemon off;"]
