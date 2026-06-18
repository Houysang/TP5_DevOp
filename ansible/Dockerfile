FROM alpine:latest

RUN apk add --no-cache ansible openssh-client py3-pip sshpass

COPY ansible.cfg /etc/ansible/ansible.cfg
COPY inventory.ini /etc/ansible/hosts
COPY setup-laravel.yml /etc/ansible/setup-laravel.yml

WORKDIR /etc/ansible

CMD ["ansible-playbook", "-i", "/etc/ansible/hosts", "/etc/ansible/setup-laravel.yml"]