FROM centos:7

RUN yum -y install epel-release
RUN yum -y install httpd mod_pearl
RUN yum -y install firewalld

EXPOSE 80
EXPOSE 8080

ADD index.html /var/www/html/
#ADD resolv.conf /etc/

#RUN firewall-cmd --add-service http
#RUN firewall-cmd --add-service http --permanent
#RUN firewall-cmd --add-service https
#RUN firewall-cmd --add-service https --permanent
#RUN firewall-cmd --reload
RUN systemctl enable httpd
RUN systemctl enable firewalld

CMD ["/sbin/init"]