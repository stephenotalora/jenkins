#############################################
# Open ssh server on centos
# with pseudo user for testing purposes only
#############################################
FROM centos

RUN yum -y install openssh-server

RUN useradd remote_user:"1234" | chpasswd && \
	mkdir /home/remote_user/.ssh && \
	chmod 700 /home/remote_user/.ssh

