FROM scratch

MAINTAINER NGINX Docker Maintainers "pellok@amt.com"
# Create os from file
ADD centos-6-root.tar.xz /

LABEL Vendor="CentOS"
LABEL License=GPLv2

# Update RPM Packages
RUN yum -y install deltarpm && yum -y update && yum clean all

# Install EPEL
RUN yum install -y epel-release && yum clean all

# Install base tools
RUN yum install -y git vim && yum clean all

# Update RPM Packages
RUN yum -y update && yum clean all

# Install Nginx
RUN yum install -y nginx && yum clean all

# forward request and error logs to docker log collector
RUN ln -sf /dev/stdout /var/log/nginx/access.log
RUN ln -sf /dev/stderr /var/log/nginx/error.log

# be backwards compatible with pre-official images
RUN ln -sf ../share/nginx /usr/local/nginx

# prepare container
ADD prepare.sh /prepare.sh
RUN chmod 755 /prepare.sh
RUN /prepare.sh

# add startup script
ADD startup.sh /startup.sh
RUN chmod 755 /startup.sh

VOLUME ["/etc/nginx"]
VOLUME ["/usr/share/nginx/html"]
VOLUME ["/var/www"]

EXPOSE 80 443

CMD ["nginx", "-g", "daemon off;"]
#CMD /startup.sh
