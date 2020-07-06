#############################################
# Open ssh server on centos
# with pseudo user for testing purposes only
#############################################
ARG REMOTE_USER_PSW
ARG PUB_KEY

FROM centos

RUN yum -y install openssh-server

RUN useradd remote_user:"$REMOTE_USER_PSW" | chpasswd && \
	mkdir /home/remote_user/.ssh && \
	chmod 700 /home/remote_user/.ssh

COPY "$PUB_KEY" /home/remote_user/.ssh/authorized_keys

RUN chown remote_user:remote_user -R /home/remote_user/.ssh/ && \
	chmod 600 /home/remote_user/.ssh/authorized_keys

RUN /user/sbin/sshd-keygen

CMD /user/sbin/sshd -D
