---
layout: post
title: edX Install Fix Script
---

* Git clone config: 

````
git clone https://github.com/edx/configuration
````

* Install Ubuntu package 

````
sudo apt-get install python-software-properties pkg-config gfortran libatlas-dev libblas-dev liblapack-dev liblapack3gf curl git python-virtualenv python-scipy python-numpy build-essential python-dev gfortran libfreetype6-dev libpng12-dev libjpeg-dev libtiff4-dev zlib1g-dev libxml2-dev libxslt-dev yui-compressor graphviz libgraphviz-dev graphviz-dev mysql-server libmysqlclient-dev libgeos-dev libreadline6 libreadline6-dev mongodb nodejs coffeescript mysql-client virtualenvwrapper libgeos-ruby1.8 lynx-cur libxmlsec1-dev swig
````

* Fix script 

Open: **roles/edxapp/tasks/deploy.yml**

Edit line 286: 
````
shell: "{{ edxapp_venv_bin }}/python -m compileall -x .git/.* {{ edxapp_code_dir }}"
````
to 
````
shell: "{{ edxapp_venv_bin }}/python -m compileall -x \".git/*|src/zendesk*\" {{ edxapp_code_dir }}"
````
