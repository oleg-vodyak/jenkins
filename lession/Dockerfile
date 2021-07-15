FROM centos:7
ENV container docker
RUN yum update -y; yum clean all -y
RUN yum install systemd -y; yum clean all -y; \
(cd /lib/systemd/system/sysinit.target.wants/; for i in *; do [ $i == systemd-tmpfiles-setup.service ] || rm -f $i; done); \
rm -f /lib/systemd/system/multi-user.target.wants/*;\
rm -f /etc/systemd/system/*.wants/*;\
rm -f /lib/systemd/system/local-fs.target.wants/*; \
rm -f /lib/systemd/system/sockets.target.wants/*udev*; \
rm -f /lib/systemd/system/sockets.target.wants/*initctl*; \
rm -f /lib/systemd/system/basic.target.wants/*;\
rm -f /lib/systemd/system/anaconda.target.wants/*;
RUN yum install net-tools -y
RUN yum install openssh-server -y
RUN yum install openssh-clients -y
RUN useradd -rm -d /home/arcsight -s /bin/bash -g root -u 1000 arcsight
RUN  echo 'arcsight:arcsight' | chpasswd
EXPOSE 22
VOLUME [ "/sys/fs/cgroup" ]
CMD ["/usr/sbin/init","-D"]