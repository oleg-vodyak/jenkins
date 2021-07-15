FROM centos:7
ENV container docker
RUN yum update -y
RUN yum install net-tools -y
RUN yum –y install openssh-server openssh-clients -y
VOLUME [ "/sys/fs/cgroup" ]
CMD ["/usr/sbin/init"]
