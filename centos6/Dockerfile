# This dockerfile uses the centos image
# CentOS 6.7(Final) with EPEL and fully updated 2015-11-15
# VERSION 1 EDITION 1
# Author: pellok
# Command format: Instruction [arguments / command] ..

FROM scratch
MAINTAINER The CentOS6.7 Final Project <pellok@ocerp.org>
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


# Default command 
CMD ["/bin/bash"]
