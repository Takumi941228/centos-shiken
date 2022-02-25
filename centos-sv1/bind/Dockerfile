FROM centos:7

RUN yum install -y bind bind-utils
RUN yum -y install net-tools
RUN yum -y install firewalld

EXPOSE 53
EXPOSE 53/UDP
EXPOSE 53/TCP

COPY named.conf /etc/
COPY j21.jyoho.com.exzone /var/named/
COPY j21.jyoho.com.inzone /var/named/
COPY 1.16.172.rzone /var/named/
COPY named.service /usr/lib/systemd/system/
#ADD resolv.conf /etc/

#RUN firewall-cmd --add-service dns
#RUN firewall-cmd --add-service dns --permanent
#RUN firewall-cmd --reload
RUN systemctl enable named
RUN systemctl enable firewalld

CMD ["/sbin/init"]
