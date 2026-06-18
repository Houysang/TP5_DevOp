FROM alpine:latest

# Install required packages
RUN apk add --no-cache \
    ansible \
    openssh-client \
    sshpass \
    git \
    bash \
    curl \
    python3 \
    py3-pip \
    rsync

# Install required Python modules for Ansible
RUN pip3 install --no-cache-dir --break-system-packages \
    requests \
    jinja2 \
    PyYAML

# Copy Ansible config
COPY ansible.cfg /etc/ansible/ansible.cfg
COPY inventory.ini /etc/ansible/hosts
COPY setup-laravel.yml /etc/ansible/setup-laravel.yml

WORKDIR /etc/ansible

# Better to run explicitly instead of auto-run (safer for debugging)
CMD ["ansible-playbook", "-i", "/etc/ansible/hosts", "/etc/ansible/setup-laravel.yml"]