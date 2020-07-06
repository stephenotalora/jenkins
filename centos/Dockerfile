#############################################
# Open ssh server on centos
# with pseudo user for testing purposes only
#############################################
FROM centos

ARG REMOTE_USER_PSW
ARG PUB_KEY

RUN yum -y install openssh-server

RUN useradd remote_user && \
	echo "remote_user:$REMOTE_USER_PSW" | chpasswd && \
	mkdir /home/remote_user/.ssh && \
	chmod 700 /home/remote_user/.ssh

COPY "$PUB_KEY" /home/remote_user/.ssh/authorized_keys

RUN chown remote_user:remote_user -R /home/remote_user/.ssh && \
	chmod 600 /home/remote_user/.ssh/authorized_keys

RUN /usr/bin/ssh-keygen -A

EXPOSE 22
RUN rm -rf /run/nologin
CMD ["/usr/sbin/sshd", "-D"]
