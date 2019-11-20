FROM centos:6

RUN iptables -F
RUN service iptables stop
RUN chkconfig iptables off
# Enable remi and epel repository
RUN yum install -y \
        yum-utils \
        epel-release \
        http://rpms.famillecollet.com/enterprise/remi-release-6.rpm
RUN yum install -y http://rpms.remirepo.net/enterprise/remi-release-6.rpm
RUN yum-config-manager --enable remi-php72
RUN yum install -y php php-mcrypt php-cli php-gd php-curl php-mysql php-ldap php-zip php-fileinfo

RUN setenforce permissive
ADD config /etc/selinux/config

ADD kaltura.repo /etc/yum.repos.d/kaltura.repo
RUN yum install -y kaltura-server

# Kaltura settings
ADD local.ans /tmp/local.ans
ADD zzzkaltura.conf /etc/httpd/conf.d/zzzkaltura.conf