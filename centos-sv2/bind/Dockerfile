FROM centos:7

RUN yum -y install bind bind-utils
RUN yum -y install net-tools
RUN yum -y install firewalld

EXPOSE 53
EXPOSE 53/UDP
EXPOSE 53/TCP

COPY named.conf /etc/
COPY 1.168.192.rzone /var/named/
COPY named.service /usr/lib/systemd/system/
#COPY resolv.conf /etc/

#RUN firewall-cmd --add-service dns
#RUN firewall-cmd --add-service dns --permanent
RUN systemctl enable named
RUN systemctl enable firewalld

CMD ["/sbin/init"]

