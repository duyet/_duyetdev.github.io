---
layout: post
title: edX Install Fix Script
---

* Git clone config: 

````
git clone https://github.com/edx/configuration
````

## Install Ubuntu package 

````
sudo apt-get install python-software-properties pkg-config gfortran libatlas-dev libblas-dev liblapack-dev\
liblapack3gf curl git python-virtualenv python-scipy python-numpy build-essential python-dev gfortran libfreetype6-dev\
libpng12-dev libjpeg-dev libtiff4-dev zlib1g-dev libxml2-dev libxslt-dev yui-compressor graphviz libgraphviz-dev\
graphviz-dev mysql-server libmysqlclient-dev libgeos-dev libreadline6 libreadline6-dev mongodb nodejs coffeescript\
mysql-client virtualenvwrapper libgeos-ruby1.8 lynx-cur libxmlsec1-dev swig
````

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

