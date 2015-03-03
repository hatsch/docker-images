FROM ubuntu-upstart:14.04
MAINTAINER Stefan Hageneder <hatsch@gmail.com>

# Install Ansible and git
RUN apt-get update && \
apt-get install --no-install-recommends -y software-properties-common && \
apt-add-repository ppa:ansible/ansible && \
apt-get update && \
apt-get install -y ansible git
RUN echo '[local]\nlocalhost\n' > /etc/ansible/hosts

#Clone our Playbooks repository
WORKDIR /root/
RUN mkdir .ssh
RUN ssh-keyscan bitbucket.org  >> /root/.ssh/known_hosts
RUN ssh-keyscan github.com  >> /root/.ssh/known_hosts
RUN git clone --recursive https://github.com/hatsch/docker-images

#run the playbooks
WORKDIR /root/docker-images
RUN ansible-playbook drunomics-lamp.yml

