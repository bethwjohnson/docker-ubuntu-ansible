FROM ubuntu:latest
RUN apt-get update && apt-get install -y \ 
    python3 \
    python3-distutils \
    ssh \
    nano \
    curl \
  && rm -rf /var/lib/apt/lists/*
RUN curl https://bootstrap.pypa.io/get-pip.py -o /tmp/get-pip.py
RUN python3 /tmp/get-pip.py
RUN python3 -m pip install ansible
RUN mkdir -p /etc/ansible \
    && mkdir /etc/ansible/roles \
    && curl https://raw.githubusercontent.com/ansible/ansible/devel/examples/ansible.cfg -o /etc/ansible/ansible.cfg \
    && curl https://raw.githubusercontent.com/ansible/ansible/devel/examples/hosts -o /etc/ansible/hosts