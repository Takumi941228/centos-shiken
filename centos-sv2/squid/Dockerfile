FROM centos:7

RUN yum -y install squid
RUN yum -y install firewalld

EXPOSE 8080
EXPOSE 8080/TCP

COPY squid.conf /etc/squid/
#COPY resolv.conf /etc/

#RUN firewall-cmd --add-port 8080/tcp
#RUN firewall-cmd --add-port 8080/tcp --permanent
#RUN firewall-cmd --reload

RUN systemctl enable squid
RUN systemctl enable firewalld

CMD ["/sbin/init"]