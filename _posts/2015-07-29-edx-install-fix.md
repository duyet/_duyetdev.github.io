---
layout: post
title: edX Install
---

Hệ thống cài đặt sẽ gồm: mysql, memcache, mongo, và các edX services (lms, studio, forums, ora/discern).

## Hardware requirements

* **Ubuntu 12.04 amd64** (oraclejdk required)
* **Minimum 2GB of memory, 4GB recommended for production servers ** (with only 2GB some swap space is required, at least during installation)
* **At least one 2.00GHz CPU or EC2 compute unit**
* **Minimum 25GB of free disk**, 50GB recommended for production servers

Cấu hình Amazone: m1.large type with EBS and allocate ~50 GB to the root user.

# Install 

### 1. Install Ubuntu package 

````
sudo apt-get install -y python-software-properties pkg-config gfortran libatlas-dev libblas-dev liblapack-dev\
liblapack3gf curl git python-virtualenv python-scipy python-numpy build-essential python-dev gfortran libfreetype6-dev\
libpng12-dev libjpeg-dev libtiff4-dev zlib1g-dev libxml2-dev libxslt-dev yui-compressor graphviz libgraphviz-dev\
graphviz-dev mysql-server libmysqlclient-dev libgeos-dev libreadline6 libreadline6-dev mongodb nodejs coffeescript\
mysql-client virtualenvwrapper libgeos-ruby1.8 lynx-cur libxmlsec1-dev swig build-essential\
software-properties-common python-software-properties curl git-core libxml2-dev\
libxslt1-dev python-pip python-apt python-dev
````

### 2. Install system pre-requisites
````
sudo pip install --upgrade pip
sudo pip install --upgrade virtualenv
````

### 3. Clone the configuration repository and run Ansible

````
export OPENEDX_RELEASE=named-release/birch
cd /var/tmp
git clone https://github.com/edx/configuration
git checkout $OPENEDX_RELEASE
````

### 4. Install the ansible requirements

````
cd /var/tmp/configuration
sudo pip install -r requirements.txt
````

### 5. Run the edx_sandbox.yml playbook in the configuration/playbooks directory

````
cd /var/tmp/configuration/playbooks && sudo ansible-playbook -c local ./edx_sandbox.yml -i "localhost,"
````

-------------------

## Fix Compile Zendesk

Open: **roles/edxapp/tasks/deploy.yml**

Edit line 286: 
````
shell: "{{ edxapp_venv_bin }}/python -m compileall -x .git/.* {{ edxapp_code_dir }}"
````

to 

````
shell: "{{ edxapp_venv_bin }}/python -m compileall -x \".git/*|src/zendesk*\" {{ edxapp_code_dir }}"
````

## Fix download **elasticsearch**

````
TASK: [elasticsearch | download elasticsearch] ******************************** 
failed: [localhost] => {"failed": true, "item": ""}
msg: Failed to validate the SSL certificate for download.elasticsearch.org:443. Use validate_certs=no or make sure your managed systems have a valid CA certificate installed. Paths checked for this platform: /etc/ssl/certs, /etc/pki/ca-trust/extracted/pelasticsearchem, /etc/pki/tls/certs, /usr/share/ca-certificates/cacert.org, /etc/ansible
````

Open **roles/elasticsearch/tasks/main.yml** 

After line 36 (https://github.com/edx/configuration/blob/096196a21441a8ba5342dd63588df6e8e3708e0a/playbooks/roles/elasticsearch/tasks/main.yml#L36)

Add
````
validate_certs=no
````

And run: 

````
sudo /usr/sbin/update-ca-certificates
````

## edX Staff Docs 

http://edx-partner-course-staff.readthedocs.org/en/latest/index.html

