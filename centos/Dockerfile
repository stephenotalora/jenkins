#############################################
# Open ssh server on centos
# with pseudo user for testing purposes only
#############################################
ARG REMOTE_USER_PSW

FROM centos

RUN yum -y install openssh-server

RUN useradd remote_user:"$REMOTE_USER_PSW" | chpasswd && \
	mkdir /home/remote_user/.ssh && \
	chmod 700 /home/remote_user/.ssh

