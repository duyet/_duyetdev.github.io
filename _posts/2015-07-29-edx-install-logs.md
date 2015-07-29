---
layout: post
title: edX Installion Logs.
---

````
ubuntu@ptnmaster:~/edx_configuration/playbooks$ nano roles/edxapp/tasks/deploy.yml 
ubuntu@ptnmaster:~/edx_configuration/playbooks$ sudo ansible-playbook -c local ./edx_sandbox.yml -i "localhost,"
[sudo] password for ubuntu: 
ERROR: Syntax Error while loading YAML script, /home/ubuntu/edx_configuration/playbooks/roles/edxapp/tasks/deploy.yml
Note: The error may actually appear before this position: line 348, column 58

- name: compiling all py files in the edx-platform repo
  shell: "{{ edxapp_venv_bin }}/python -m compileall -x ".git/.*|src/zendesk*" {{ edxapp_code_dir }}"
                                                         ^
We could be wrong, but this one looks like it might be an issue with
missing quotes.  Always quote template expression brackets when they 
start a value. For instance:            

    with_items:
      - {{ foo }}

Should be written as:

    with_items:
      - "{{ foo }}"      


ubuntu@ptnmaster:~/edx_configuration/playbooks$ nano roles/edxapp/tasks/deploy.yml 
ubuntu@ptnmaster:~/edx_configuration/playbooks$ sudo ansible-playbook -c local ./edx_sandbox.yml -i "localhost,"

PLAY [Configure instance(s)] ************************************************** 

GATHERING FACTS *************************************************************** 
ok: [localhost]

TASK: [user | debug var=user_info] ******************************************** 
ok: [localhost] => {
    "item": "", 
    "user_info": []
}

TASK: [user | create the edxadmin group] ************************************** 
ok: [localhost]

TASK: [user | ensure sudoers.d is read] *************************************** 
ok: [localhost]

TASK: [user | grant full sudo access to the edxadmin group] ******************* 
ok: [localhost]

TASK: [user | create the users] *********************************************** 
skipping: [localhost]

TASK: [user | create .ssh directory] ****************************************** 
skipping: [localhost]

TASK: [user | assign admin role to admin users] ******************************* 
skipping: [localhost]

TASK: [user | copy github key[s] to .ssh/authorized_keys2] ******************** 
skipping: [localhost]

TASK: [user | set permissions on .ssh/authorized_keys2] *********************** 
skipping: [localhost]

TASK: [user | copy additional authorized keys] ******************************** 
skipping: [localhost]

TASK: [user | create bashrc file for normal users] **************************** 
skipping: [localhost]

TASK: [user | create .profile for all users] ********************************** 
skipping: [localhost]

TASK: [user | modify shell for restricted users] ****************************** 
skipping: [localhost]

TASK: [user | create bashrc file for restricted users] ************************ 
skipping: [localhost]

TASK: [user | create sudoers file from template] ****************************** 
ok: [localhost]

TASK: [user | change home directory ownership to root for restricted users] *** 
skipping: [localhost]

TASK: [user | create ~/bin directory] ***************************************** 
skipping: [localhost]

TASK: [user | create allowed command links] *********************************** 
skipping: [localhost]

TASK: [security | install security packages] ********************************** 
skipping: [localhost]

TASK: [security | update all system packages] ********************************* 
skipping: [localhost]

TASK: [security | configure periodic unattended-upgrades] ********************* 
skipping: [localhost]

TASK: [security | disable unattended-upgrades] ******************************** 
skipping: [localhost]

TASK: [security | only unattended-upgrade from security repo] ***************** 
skipping: [localhost]

TASK: [security | disable security only updates on unattended-upgrades] ******* 
skipping: [localhost]

TASK: [security | Check if we are vulnerable] ********************************* 
skipping: [localhost]

TASK: [security | Apply bash security update if we are vulnerable] ************ 
skipping: [localhost]

TASK: [security | Check again and fail if we are still vulnerable] ************ 
skipping: [localhost]

TASK: [common | Update CA Certificates] *************************************** 
changed: [localhost]

TASK: [common | Add user www-data] ******************************************** 
ok: [localhost]

TASK: [common | Create common directories] ************************************ 
ok: [localhost] => (item=/edx/var)
ok: [localhost] => (item=/edx/app)
ok: [localhost] => (item=/edx/bin)
ok: [localhost] => (item=/edx/etc)

TASK: [common | check if instance is vagrant] ********************************* 
ok: [localhost]

TASK: [common | Install python-pycurl] **************************************** 
ok: [localhost]

TASK: [common | Add git apt repository] *************************************** 
ok: [localhost]

TASK: [common | Install role-independent useful system packages] ************** 
ok: [localhost]

TASK: [common | Create common log directory] ********************************** 
ok: [localhost]

TASK: [common | upload sudo config for key forwarding as root] **************** 
ok: [localhost]

TASK: [common | pip install virtualenv] *************************************** 
ok: [localhost] => (item=pip==1.5.6)
ok: [localhost] => (item=setuptools==3.6)
ok: [localhost] => (item=virtualenv==1.11.6)
ok: [localhost] => (item=virtualenvwrapper)

TASK: [common | Install rsyslog configuration for edX] ************************ 
ok: [localhost]

TASK: [common | Remove the default rsyslog configuration] ********************* 
ok: [localhost]

TASK: [common | Create hourly subdirectory in logrotate.d] ******************** 
ok: [localhost]

TASK: [common | Install logrotate configuration for edX] ********************** 
ok: [localhost]

TASK: [common | Install logrotate configuration for tracking file] ************ 
ok: [localhost]

TASK: [common | Add logrotate for tracking.log to cron.hourly] **************** 
ok: [localhost]

TASK: [common | update /etc/hosts] ******************************************** 
skipping: [localhost]

TASK: [common | update /etc/hostname] ***************************************** 
skipping: [localhost]

TASK: [common | run hostname] ************************************************* 
skipping: [localhost]

TASK: [common | update /etc/dhcp/dhclient.conf] ******************************* 
skipping: [localhost]

TASK: [common | update the ssh motd on Ubuntu] ******************************** 
ok: [localhost] => (item=/etc/update-motd.d/10-help-text)
ok: [localhost] => (item=/usr/share/landscape/landscape-sysinfo.wrapper)
ok: [localhost] => (item=/etc/update-motd.d/51-cloudguest)
ok: [localhost] => (item=/etc/update-motd.d/91-release-upgrade)

TASK: [common | add ssh-warning banner motd] ********************************** 
ok: [localhost]

TASK: [common | update ssh config] ******************************************** 
ok: [localhost]

TASK: [nginx | create nginx app dirs] ***************************************** 
ok: [localhost] => (item=/edx/app/nginx)
ok: [localhost] => (item=/edx/app/nginx/sites-available)
ok: [localhost] => (item=/edx/app/nginx/sites-enabled)
ok: [localhost] => (item=/edx/app/nginx/conf.d)

TASK: [nginx | create nginx data dirs] **************************************** 
ok: [localhost] => (item=/edx/var/nginx)
changed: [localhost] => (item=/edx/var/log/nginx)
ok: [localhost] => (item=/edx/var/nginx/server-static)

TASK: [nginx | Install nginx packages] **************************************** 
ok: [localhost]

TASK: [nginx | Server configuration file] ************************************* 
ok: [localhost]

TASK: [nginx | Creating common nginx configuration] *************************** 
ok: [localhost]

TASK: [nginx | Create robot rules] ******************************************** 
skipping: [localhost]

TASK: [nginx | Creating link for common nginx configuration] ****************** 
ok: [localhost]

TASK: [nginx | Copying nginx configs for ['cms', 'lms', 'forum', 'ora', 'xqueue']] *** 
ok: [localhost] => (item=cms)
ok: [localhost] => (item=lms)
ok: [localhost] => (item=forum)
ok: [localhost] => (item=ora)
ok: [localhost] => (item=xqueue)

TASK: [nginx | Creating nginx config links for ['cms', 'lms', 'forum', 'ora', 'xqueue']] *** 
ok: [localhost] => (item=cms)
ok: [localhost] => (item=lms)
ok: [localhost] => (item=forum)
ok: [localhost] => (item=ora)
ok: [localhost] => (item=xqueue)

TASK: [nginx | Copying nginx extra configs] *********************************** 
skipping: [localhost]

TASK: [nginx | Creating links for nginx extra configs] ************************ 
skipping: [localhost]

TASK: [nginx | Copying custom nginx config] *********************************** 
skipping: [localhost]

TASK: [nginx | Copying nginx redirect configs for {{nginx_redirects}}] ******** 
skipping: [localhost]

TASK: [nginx | Creating nginx redirect links for {{nginx_redirects}}] ********* 
skipping: [localhost]

TASK: [nginx | Create NGINX server templates] ********************************* 
ok: [localhost] => (item={'msg': u'If think you have encountered this message in error please let us know at <a href="mailto:technical@example.com">technical@example.com</a>', 'file': 'rate-limit.html', 'heading': 'Uh oh, we are having some server issues..', 'img': u'https://upload.wikimedia.org/wikipedia/commons/thumb/1/11/Pendleton_Sinking_Ship.jpg/640px-Pendleton_Sinking_Ship.jpg', 'title': 'Rate limit exceeded'})
ok: [localhost] => (item={'msg': u'We have been notified of the error, if it persists please let us know at <a href="mailto:technical@example.com">technical@example.com</a>', 'file': 'server-error.html', 'heading': 'Uh oh, we are having some server issues..', 'img': u'https://upload.wikimedia.org/wikipedia/commons/thumb/1/11/Pendleton_Sinking_Ship.jpg/640px-Pendleton_Sinking_Ship.jpg', 'title': 'Server error'})

TASK: [nginx | Write out htpasswd file] *************************************** 
skipping: [localhost]

TASK: [nginx | Create nginx log file location (just in case)] ***************** 
changed: [localhost]

TASK: [nginx | stat] ********************************************************** 
ok: [localhost]

TASK: [nginx | stat] ********************************************************** 
ok: [localhost]

TASK: [nginx | copy ssl cert] ************************************************* 
skipping: [localhost]

TASK: [nginx | copy ssl key] ************************************************** 
skipping: [localhost]

TASK: [nginx | Removing default nginx config and restart (enabled)] *********** 
ok: [localhost]

TASK: [nginx | Set up nginx access log rotation] ****************************** 
ok: [localhost]

TASK: [nginx | Set up nginx access log rotation] ****************************** 
ok: [localhost]

TASK: [nginx | make sure nginx has started] *********************************** 
ok: [localhost]

TASK: [edxlocal | install packages needed for single server] ****************** 
ok: [localhost]

TASK: [edxlocal | setup the edxapp db user] *********************************** 
ok: [localhost]

TASK: [edxlocal | create a database for edxapp] ******************************* 
ok: [localhost]

TASK: [edxlocal | setup the xqueue db user] *********************************** 
ok: [localhost]

TASK: [edxlocal | create a database for xqueue] ******************************* 
ok: [localhost]

TASK: [edxlocal | setup the ora db user] ************************************** 
ok: [localhost]

TASK: [edxlocal | create a database for ora] ********************************** 
ok: [localhost]

TASK: [edxlocal | create databases for analytics api] ************************* 
skipping: [localhost] => (item={{ANALYTICS_API_CONFIG['DATABASES']['default']['NAME']}})
skipping: [localhost] => (item={{ANALYTICS_API_CONFIG['DATABASES']['reports']['NAME']}})

TASK: [edxlocal | create api user for the analytics api] ********************** 
skipping: [localhost]

TASK: [edxlocal | create read-only reports user for the analytics-api] ******** 
skipping: [localhost]

TASK: [edxlocal | setup the migration db user] ******************************** 
ok: [localhost] => (item=edxapp)
ok: [localhost] => (item=xqueue)
ok: [localhost] => (item=ora)

TASK: [edxlocal | setup the migration db user for analytics] ****************** 
skipping: [localhost] => (item={{ANALYTICS_API_CONFIG['DATABASES']['default']['NAME']}})
skipping: [localhost] => (item={{ANALYTICS_API_CONFIG['DATABASES']['reports']['NAME']}})

TASK: [edxlocal | setup the read-only db user] ******************************** 
ok: [localhost]

TASK: [edxlocal | setup the admin db user] ************************************ 
ok: [localhost]

TASK: [edxlocal | install memcached] ****************************************** 
ok: [localhost]

TASK: [mongo | check to see that MongoDB 2.4 is not installed] **************** 
ok: [localhost]

TASK: [mongo | verify 2.4 not installed] ************************************** 
skipping: [localhost]

TASK: [mongo | remove mongo 2.4 if present] *********************************** 
skipping: [localhost]

TASK: [mongo | install python pymongo for mongo_user ansible module] ********** 
ok: [localhost]

TASK: [mongo | add the mongodb signing key] *********************************** 
ok: [localhost]

TASK: [mongo | add the mongodb repo to the sources list] ********************** 
ok: [localhost]

TASK: [mongo | install mongo server and recommends] *************************** 
ok: [localhost]

TASK: [mongo | create mongo dirs] ********************************************* 
ok: [localhost] => (item=/edx/var/mongo)
ok: [localhost] => (item=/edx/var/mongo/mongodb)
ok: [localhost] => (item=/edx/var/log/mongo)

TASK: [mongo | stop mongod service] ******************************************* 
changed: [localhost]

TASK: [mongo | move mongodb to {{mongo_data_dir}}] **************************** 
skipping: [localhost]

TASK: [mongo | copy mongodb key file] ***************************************** 
skipping: [localhost]

TASK: [mongo | copy configuration template] *********************************** 
ok: [localhost]

TASK: [mongo | start mongo service] ******************************************* 
changed: [localhost]

TASK: [mongo | wait for mongo server to start] ******************************** 
ok: [localhost]

TASK: [mongo | drop super user script] **************************************** 
changed: [localhost]

TASK: [mongo | create super user with js] ************************************* 
changed: [localhost]

TASK: [mongo | delete super user script] ************************************** 
changed: [localhost]

TASK: [mongo | Create the file to initialize the mongod replica set] ********** 
skipping: [localhost]

TASK: [mongo | Initialize the replication set] ******************************** 
skipping: [localhost]

TASK: [mongo | create a mongodb user] ***************************************** 
ok: [localhost] => (item={'password': 'password', 'user': 'cs_comments_service', 'roles': 'readWrite', 'database': 'cs_comments_service'})
ok: [localhost] => (item={'password': 'password', 'user': 'edxapp', 'roles': 'readWrite', 'database': 'edxapp'})

TASK: [mongo | create a mongodb user] ***************************************** 
skipping: [localhost] => (item={'password': 'password', 'user': 'cs_comments_service', 'roles': 'readWrite', 'database': 'cs_comments_service'})
skipping: [localhost] => (item={'password': 'password', 'user': 'edxapp', 'roles': 'readWrite', 'database': 'edxapp'})

TASK: [mongo | install s3cmd] ************************************************* 
skipping: [localhost]

TASK: [mongo | configure s3cmd] *********************************************** 
skipping: [localhost]

TASK: [mongo | install backup-mongo-to-s3 script] ***************************** 
skipping: [localhost]

TASK: [mongo | schedule backup-mongo-to-3s crontab] *************************** 
ok: [localhost]

TASK: [supervisor | create application user] ********************************** 
ok: [localhost]

TASK: [supervisor | create supervisor service user] *************************** 
ok: [localhost]

TASK: [supervisor | create supervisor directories] **************************** 
ok: [localhost] => (item=/edx/app/supervisor)
ok: [localhost] => (item=/edx/app/supervisor/venvs/supervisor)

TASK: [supervisor | create service user accessible dirs] ********************** 
ok: [localhost] => (item=/edx/app/supervisor/conf.d)
ok: [localhost] => (item=/edx/app/supervisor/conf.available.d)

TASK: [supervisor | create supervisor directories] **************************** 
ok: [localhost] => (item=/edx/var/supervisor)
ok: [localhost] => (item=/edx/var/log/supervisor)

TASK: [supervisor | install supervisor in its venv] *************************** 
ok: [localhost]

TASK: [supervisor | install supervisor in its venv] *************************** 
ok: [localhost] => (item=boto)
ok: [localhost] => (item=python-simple-hipchat)

TASK: [supervisor | create supervisor upstart job] **************************** 
ok: [localhost]

TASK: [supervisor | create pre_supervisor upstart job] ************************ 
skipping: [localhost]

TASK: [supervisor | write the pre_suprevisor python script] ******************* 
skipping: [localhost]

TASK: [supervisor | create supervisor master config] ************************** 
ok: [localhost]

TASK: [supervisor | create a symlink for supervisortctl] ********************** 
ok: [localhost]

TASK: [supervisor | create a symlink for supervisor cfg] ********************** 
ok: [localhost] => (item=/edx/app/supervisor/supervisord.conf)
ok: [localhost] => (item=/edx/app/supervisor/conf.d)

TASK: [supervisor | start supervisor] ***************************************** 
ok: [localhost]

TASK: [supervisor | wait for web port to be available] ************************ 
skipping: [localhost]

TASK: [supervisor | update supervisor configuration] ************************** 
ok: [localhost]

TASK: [rbenv | fail rbenv_user required for role] ***************************** 
skipping: [localhost]

TASK: [rbenv | fail rbenv_dir required for role] ****************************** 
skipping: [localhost]

TASK: [rbenv | fail rbenv_ruby_version required for role] ********************* 
skipping: [localhost]

TASK: [rbenv | create rbenv user {{edxapp_user}}] ***************************** 
ok: [localhost]

TASK: [rbenv | create rbenv dir if it does not exist] ************************* 
ok: [localhost]

TASK: [rbenv | install build depends] ***************************************** 
ok: [localhost] => (item=curl,build-essential,libcurl4-openssl-dev,libreadline-dev,libssl-dev,libxml2-dev,libxslt1-dev,zlib1g-dev)

TASK: [rbenv | update rbenv repo] ********************************************* 
changed: [localhost]

TASK: [rbenv | ensure ruby_env exists] **************************************** 
ok: [localhost]

TASK: [rbenv | check ruby-build installed] ************************************ 
changed: [localhost]

TASK: [rbenv | if ruby-build exists, which versions we can install] *********** 
changed: [localhost]

TASK: [rbenv | create temporary directory] ************************************ 
changed: [localhost]

TASK: [rbenv | clone ruby-build repo] ***************************************** 
changed: [localhost]

TASK: [rbenv | install ruby-build] ******************************************** 
changed: [localhost]

TASK: [rbenv | remove temporary directory] ************************************ 
changed: [localhost]

TASK: [rbenv | check ruby {{edxapp_ruby_version}} installed] ****************** 
changed: [localhost]

TASK: [rbenv | install ruby {{edxapp_ruby_version}}] ************************** 
skipping: [localhost]

TASK: [rbenv | set global ruby {{edxapp_ruby_version}}] *********************** 
changed: [localhost]

TASK: [rbenv | install bundler] *********************************************** 
changed: [localhost]

TASK: [rbenv | remove rbenv version of rake] ********************************** 
ok: [localhost]

TASK: [rbenv | install rake gem] ********************************************** 
changed: [localhost]

TASK: [rbenv | rehash] ******************************************************** 
changed: [localhost]

TASK: [supervisor | create application user] ********************************** 
ok: [localhost]

TASK: [supervisor | create supervisor service user] *************************** 
ok: [localhost]

TASK: [supervisor | create supervisor directories] **************************** 
ok: [localhost] => (item=/edx/app/devpi/supervisor)
ok: [localhost] => (item=/edx/app/devpi/venvs/supervisor)

TASK: [supervisor | create service user accessible dirs] ********************** 
ok: [localhost] => (item=/edx/app/devpi/supervisor/conf.d)
ok: [localhost] => (item=/edx/app/devpi/supervisor/conf.available.d)

TASK: [supervisor | create supervisor directories] **************************** 
ok: [localhost] => (item=/edx/var/devpi/supervisor)
ok: [localhost] => (item=/edx/var/log/devpi/supervisor)

TASK: [supervisor | install supervisor in its venv] *************************** 
ok: [localhost]

TASK: [supervisor | install supervisor in its venv] *************************** 
ok: [localhost] => (item=boto)
ok: [localhost] => (item=python-simple-hipchat)

TASK: [supervisor | create supervisor upstart job] **************************** 
ok: [localhost]

TASK: [supervisor | create pre_supervisor upstart job] ************************ 
skipping: [localhost]

TASK: [supervisor | write the pre_suprevisor python script] ******************* 
skipping: [localhost]

TASK: [supervisor | create supervisor master config] ************************** 
ok: [localhost]

TASK: [supervisor | create a symlink for supervisortctl] ********************** 
skipping: [localhost]

TASK: [supervisor | create a symlink for supervisor cfg] ********************** 
skipping: [localhost] => (item=/edx/app/devpi/supervisor/supervisord.conf)
skipping: [localhost] => (item=/edx/app/devpi/supervisor/conf.d)

TASK: [supervisor | start supervisor] ***************************************** 
ok: [localhost]

TASK: [supervisor | wait for web port to be available] ************************ 
skipping: [localhost]

TASK: [supervisor | update supervisor configuration] ************************** 
ok: [localhost]

TASK: [devpi | create devpi user] ********************************************* 
ok: [localhost]

TASK: [devpi | create devpi application directories] ************************** 
ok: [localhost] => (item=/edx/app/devpi)
ok: [localhost] => (item=/edx/app/devpi/venvs/devpi)

TASK: [devpi | create the devpi data directory, needs write access by the service user] *** 
ok: [localhost] => (item=/edx/var/devpi)
ok: [localhost] => (item=/edx/var/devpi/data)

TASK: [devpi | install devpi pip pkgs] **************************************** 
ok: [localhost] => (item=devpi-server)
ok: [localhost] => (item=eventlet)

TASK: [devpi | writing supervisor script] ************************************* 
ok: [localhost]

TASK: [devpi | create a symlink for venv python, pip] ************************* 
ok: [localhost] => (item=python)
ok: [localhost] => (item=pip)

TASK: [devpi | create a symlink for venv supervisor] ************************** 
ok: [localhost]

TASK: [devpi | create a symlink for supervisor config] ************************ 
ok: [localhost]

TASK: [devpi | update devpi supervisor configuration] ************************* 
ok: [localhost]

TASK: [devpi | ensure devpi is started] *************************************** 
ok: [localhost]

TASK: [nltk | Install unzip] ************************************************** 
ok: [localhost]

TASK: [nltk | create the nltk data directory and subdirectories] ************** 
ok: [localhost] => (item={'url': 'http://nltk.github.com/nltk_data/packages/taggers/maxent_treebank_pos_tagger.zip', 'path': 'taggers/maxent_treebank_pos_tagger'})
ok: [localhost] => (item={'url': 'http://nltk.github.com/nltk_data/packages/corpora/stopwords.zip', 'path': 'corpora/stopwords'})
ok: [localhost] => (item={'url': 'http://nltk.github.com/nltk_data/packages/corpora/wordnet.zip', 'path': 'corpora/wordnet'})

TASK: [nltk | download nltk data] ********************************************* 
ok: [localhost] => (item={'url': 'http://nltk.github.com/nltk_data/packages/taggers/maxent_treebank_pos_tagger.zip', 'path': 'taggers/maxent_treebank_pos_tagger'})
ok: [localhost] => (item={'url': 'http://nltk.github.com/nltk_data/packages/corpora/stopwords.zip', 'path': 'corpora/stopwords'})
ok: [localhost] => (item={'url': 'http://nltk.github.com/nltk_data/packages/corpora/wordnet.zip', 'path': 'corpora/wordnet'})

TASK: [nltk | unarchive nltk data] ******************************************** 
skipping: [localhost] => (item={'url': 'http://nltk.github.com/nltk_data/packages/taggers/maxent_treebank_pos_tagger.zip', 'path': 'taggers/maxent_treebank_pos_tagger'})
skipping: [localhost] => (item={'url': 'http://nltk.github.com/nltk_data/packages/corpora/stopwords.zip', 'path': 'corpora/stopwords'})
skipping: [localhost] => (item={'url': 'http://nltk.github.com/nltk_data/packages/corpora/wordnet.zip', 'path': 'corpora/wordnet'})

TASK: [user | debug var=user_info] ******************************************** 
skipping: [localhost]

TASK: [user | create the edxadmin group] ************************************** 
skipping: [localhost]

TASK: [user | ensure sudoers.d is read] *************************************** 
skipping: [localhost]

TASK: [user | grant full sudo access to the edxadmin group] ******************* 
skipping: [localhost]

TASK: [user | create the users] *********************************************** 
skipping: [localhost] => (item={'sudo_cmds': [u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp lms migrate *', u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp cms migrate *', u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp lms syncdb *', u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp cms syncdb *', u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp lms seed_permissions_roles *', u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp lms set_staff *', u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp lms transfer_students *'], 'type': 'restricted', 'name': u'automator', 'authorized_keys': []})

TASK: [user | create .ssh directory] ****************************************** 
skipping: [localhost] => (item={'sudo_cmds': [u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp lms migrate *', u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp cms migrate *', u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp lms syncdb *', u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp cms syncdb *', u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp lms seed_permissions_roles *', u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp lms set_staff *', u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp lms transfer_students *'], 'type': 'restricted', 'name': u'automator', 'authorized_keys': []})

TASK: [user | assign admin role to admin users] ******************************* 
skipping: [localhost] => (item={'sudo_cmds': [u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp lms migrate *', u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp cms migrate *', u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp lms syncdb *', u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp cms syncdb *', u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp lms seed_permissions_roles *', u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp lms set_staff *', u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp lms transfer_students *'], 'type': 'restricted', 'name': u'automator', 'authorized_keys': []})

TASK: [user | copy github key[s] to .ssh/authorized_keys2] ******************** 
skipping: [localhost] => (item={'sudo_cmds': [u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp lms migrate *', u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp cms migrate *', u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp lms syncdb *', u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp cms syncdb *', u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp lms seed_permissions_roles *', u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp lms set_staff *', u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp lms transfer_students *'], 'type': 'restricted', 'name': u'automator', 'authorized_keys': []})

TASK: [user | set permissions on .ssh/authorized_keys2] *********************** 
skipping: [localhost] => (item={'sudo_cmds': [u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp lms migrate *', u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp cms migrate *', u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp lms syncdb *', u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp cms syncdb *', u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp lms seed_permissions_roles *', u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp lms set_staff *', u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp lms transfer_students *'], 'type': 'restricted', 'name': u'automator', 'authorized_keys': []})

TASK: [user | copy additional authorized keys] ******************************** 
skipping: [localhost] => (item={'sudo_cmds': [u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp lms migrate *', u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp cms migrate *', u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp lms syncdb *', u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp cms syncdb *', u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp lms seed_permissions_roles *', u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp lms set_staff *', u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp lms transfer_students *'], 'type': 'restricted', 'name': u'automator', 'authorized_keys': []})

TASK: [user | create bashrc file for normal users] **************************** 
skipping: [localhost] => (item={'sudo_cmds': [u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp lms migrate *', u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp cms migrate *', u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp lms syncdb *', u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp cms syncdb *', u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp lms seed_permissions_roles *', u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp lms set_staff *', u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp lms transfer_students *'], 'type': 'restricted', 'name': u'automator', 'authorized_keys': []})

TASK: [user | create .profile for all users] ********************************** 
skipping: [localhost] => (item={'sudo_cmds': [u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp lms migrate *', u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp cms migrate *', u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp lms syncdb *', u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp cms syncdb *', u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp lms seed_permissions_roles *', u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp lms set_staff *', u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp lms transfer_students *'], 'type': 'restricted', 'name': u'automator', 'authorized_keys': []})

TASK: [user | modify shell for restricted users] ****************************** 
skipping: [localhost] => (item={'sudo_cmds': [u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp lms migrate *', u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp cms migrate *', u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp lms syncdb *', u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp cms syncdb *', u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp lms seed_permissions_roles *', u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp lms set_staff *', u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp lms transfer_students *'], 'type': 'restricted', 'name': u'automator', 'authorized_keys': []})

TASK: [user | create bashrc file for restricted users] ************************ 
skipping: [localhost] => (item={'sudo_cmds': [u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp lms migrate *', u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp cms migrate *', u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp lms syncdb *', u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp cms syncdb *', u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp lms seed_permissions_roles *', u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp lms set_staff *', u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp lms transfer_students *'], 'type': 'restricted', 'name': u'automator', 'authorized_keys': []})

TASK: [user | create sudoers file from template] ****************************** 
skipping: [localhost]

TASK: [user | change home directory ownership to root for restricted users] *** 
skipping: [localhost] => (item={'sudo_cmds': [u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp lms migrate *', u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp cms migrate *', u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp lms syncdb *', u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp cms syncdb *', u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp lms seed_permissions_roles *', u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp lms set_staff *', u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp lms transfer_students *'], 'type': 'restricted', 'name': u'automator', 'authorized_keys': []})

TASK: [user | create ~/bin directory] ***************************************** 
skipping: [localhost] => (item={'sudo_cmds': [u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp lms migrate *', u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp cms migrate *', u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp lms syncdb *', u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp cms syncdb *', u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp lms seed_permissions_roles *', u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp lms set_staff *', u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp lms transfer_students *'], 'type': 'restricted', 'name': u'automator', 'authorized_keys': []})

TASK: [user | create allowed command links] *********************************** 
skipping: [localhost] => (item=[{'sudo_cmds': [u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp lms migrate *', u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp cms migrate *', u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp lms syncdb *', u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp cms syncdb *', u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp lms seed_permissions_roles *', u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp lms set_staff *', u'ALL=(www-data)  NOPASSWD:SETENV:/edx/bin/python.edxapp /edx/bin/manage.edxapp lms transfer_students *'], 'type': 'restricted', 'name': u'automator', 'authorized_keys': []}, '/usr/bin/sudo'])

TASK: [edxapp | create application user] ************************************** 
ok: [localhost]

TASK: [edxapp | create edxapp user dirs] ************************************** 
ok: [localhost] => (item=/edx/app/edxapp)
ok: [localhost] => (item=/edx/app/edxapp/.ssh)
ok: [localhost] => (item=/edx/var/edxapp)
ok: [localhost] => (item=/edx/app/edxapp/venvs)
ok: [localhost] => (item=/edx/var/edxapp/themes)
ok: [localhost] => (item=/edx/var/edxapp/staticfiles)
ok: [localhost] => (item=/edx/var/edxapp/course_static)
changed: [localhost] => (item=/edx/var/edxapp/data)

TASK: [edxapp | make the course data dir] ************************************* 
ok: [localhost]

TASK: [edxapp | create edxapp log dir] **************************************** 
ok: [localhost]

TASK: [edxapp | create web-writable edxapp data dirs] ************************* 
changed: [localhost] => (item=/edx/var/edxapp/data)
ok: [localhost] => (item=/edx/var/edxapp/uploads)

TASK: [edxapp | add ppas for current versions of nodejs] ********************** 
ok: [localhost]

TASK: [edxapp | install system packages on which LMS and CMS rely] ************ 
ok: [localhost]

TASK: [edxapp | set up edxapp .npmrc] ***************************************** 
changed: [localhost]

TASK: [edxapp | create log directories for service variants] ****************** 
ok: [localhost] => (item=lms)
ok: [localhost] => (item=cms)

TASK: [edxapp | code sandbox | Use libblas for 3gf] *************************** 
changed: [localhost]

TASK: [edxapp | code sandbox | Use liblapac for 3gf] ************************** 
changed: [localhost]

TASK: [edxapp | code sandbox | Create edxapp sandbox user] ******************** 
ok: [localhost]

TASK: [edxapp | code sandbox | Install apparmor utils system pkg] ************* 
ok: [localhost]

TASK: [edxapp | code sandbox | write out apparmor code sandbox config] ******** 
ok: [localhost]

TASK: [edxapp | code sandbox | write out sandbox user sudoers config] ********* 
ok: [localhost]

TASK: [edxapp | code sandbox | start apparmor service] ************************ 
ok: [localhost]

TASK: [edxapp | code sandbox | (bootstrap) load code sandbox profile] ********* 
changed: [localhost]

TASK: [edxapp | code sandbox | (bootstrap) put code sandbox into aa-enforce or aa-complain mode depending on EDXAPP_SANDBOX_ENFORCE] *** 
changed: [localhost]

TASK: [edxapp | setup the edxapp env] ***************************************** 
ok: [localhost]

TASK: [edxapp | create ssh script for git (not authenticated)] **************** 
ok: [localhost]

TASK: [edxapp | create ssh script for git (authenticated)] ******************** 
skipping: [localhost]

TASK: [edxapp | install read-only ssh key] ************************************ 
skipping: [localhost]

TASK: [edxapp | checkout edx-platform repo into {{edxapp_code_dir}}] ********** 
ok: [localhost]

TASK: [edxapp | git clean after checking out edx-platform] ******************** 
changed: [localhost]

TASK: [edxapp | checkout theme] *********************************************** 
skipping: [localhost]

TASK: [edxapp | create checksum for requirements, package.json and Gemfile] *** 
failed: [localhost] => {"changed": true, "cmd": "/usr/bin/md5sum /edx/app/edxapp/edx-platform/requirements/edx/pre.txt /edx/app/edxapp/edx-platform/requirements/edx/post.txt /edx/app/edxapp/edx-platform/requirements/edx/base.txt /edx/app/edxapp/edx-platform/requirements/edx/custom.txt /edx/app/edxapp/edx-platform/requirements/edx/paver.txt /edx/app/edxapp/edx-platform/requirements/edx-sandbox/post.txt /edx/app/edxapp/edx-platform/requirements/edx-sandbox/base.txt 2>/dev/null > /var/tmp/edxapp.req.new ", "delta": "0:00:00.002390", "end": "2015-07-29 22:20:31.635074", "item": "", "rc": 1, "start": "2015-07-29 22:20:31.632684"}
...ignoring

TASK: [edxapp | stat path=/var/tmp/edxapp.req.new] **************************** 
ok: [localhost]

TASK: [edxapp | stat path=/var/tmp/edxapp.req.installed] ********************** 
ok: [localhost]

TASK: [edxapp | Updating requirement files for git mirror] ******************** 
changed: [localhost]

TASK: [edxapp | gem install bundler] ****************************************** 
changed: [localhost]

TASK: [edxapp | bundle install] *********************************************** 
changed: [localhost]

TASK: [edxapp | Set the npm registry] ***************************************** 
skipping: [localhost]

TASK: [edxapp | Set the npm registry permissions] ***************************** 
changed: [localhost]

TASK: [edxapp | Install edx-platform npm dependencies] ************************ 
changed: [localhost]

TASK: [edxapp | install python pre-requirements] ****************************** 
ok: [localhost]

TASK: [edxapp | install python base-requirements] ***************************** 
changed: [localhost]

TASK: [edxapp | install python post-requirements] ***************************** 
ok: [localhost]

TASK: [edxapp | install python paver-requirements] **************************** 
changed: [localhost]

TASK: [edxapp | stat path="{{custom_requirements_file}}"] ********************* 
ok: [localhost]

TASK: [edxapp | install python custom-requirements] *************************** 
skipping: [localhost]

TASK: [edxapp | install python post-post requirements] ************************ 
changed: [localhost] => (item=/edx/app/edxapp/edx-platform/requirements/edx/github.txt)
changed: [localhost] => (item=/edx/app/edxapp/edx-platform/requirements/edx/local.txt)

TASK: [edxapp | install python private requirements] ************************** 
skipping: [localhost] => (item=/edx/app/edxapp/edx-platform/requirements/edx/edx-private.txt)

TASK: [edxapp | install python extra requirements] **************************** 
skipping: [localhost]

TASK: [edxapp | install CAS attribute module] ********************************* 
skipping: [localhost]

TASK: [edxapp | install sandbox requirements into regular venv] *************** 
skipping: [localhost] => (item=/edx/app/edxapp/edx-platform/requirements/edx-sandbox/base.txt)
skipping: [localhost] => (item=/edx/app/edxapp/edx-platform/requirements/edx-sandbox/local.txt)
skipping: [localhost] => (item=/edx/app/edxapp/edx-platform/requirements/edx-sandbox/post.txt)

TASK: [edxapp | code sandbox | put sandbox apparmor profile in complain mode] *** 
changed: [localhost]

TASK: [edxapp | code sandbox | Install base sandbox requirements and create sandbox virtualenv] *** 
ok: [localhost]

TASK: [edxapp | code sandbox | Install sandbox requirements into sandbox venv] *** 
ok: [localhost] => (item=/edx/app/edxapp/edx-platform/requirements/edx-sandbox/local.txt)
ok: [localhost] => (item=/edx/app/edxapp/edx-platform/requirements/edx-sandbox/post.txt)

TASK: [edxapp | code sandbox | put code sandbox into aa-enforce or aa-complain mode, depending on EDXAPP_SANDBOX_ENFORCE] *** 
changed: [localhost]

TASK: [edxapp | compiling all py files in the edx-platform repo] ************** 
changed: [localhost]

TASK: [edxapp | give other read permissions to the virtualenv] **************** 
changed: [localhost]

TASK: [edxapp | create checksum for installed requirements] ******************* 
changed: [localhost]

TASK: [edxapp | openid workaround] ******************************************** 
changed: [localhost]

TASK: [edxapp | get s3 one time url] ****************************************** 
skipping: [localhost]

TASK: [edxapp | download from one time url] *********************************** 
skipping: [localhost]

TASK: [edxapp | unzip the data to the data dir] ******************************* 
skipping: [localhost]

TASK: [edxapp | make the course data web user writable] *********************** 
ok: [localhost]

TASK: [edxapp | create  application config] *********************************** 
changed: [localhost] => (item=lms)
changed: [localhost] => (item=cms)

TASK: [edxapp | create  auth file] ******************************************** 
changed: [localhost] => (item=lms)
changed: [localhost] => (item=cms)

TASK: [edxapp | writing  supervisor script] *********************************** 
changed: [localhost] => (item=lms)
changed: [localhost] => (item=cms)

TASK: [edxapp | writing edxapp supervisor script] ***************************** 
changed: [localhost]

TASK: [edxapp | writing celery worker supervisor script] ********************** 
changed: [localhost]

TASK: [edxapp | enable  supervisor script] ************************************ 
skipping: [localhost] => (item=lms)
skipping: [localhost] => (item=cms)

TASK: [edxapp | enable edxapp supervisor script] ****************************** 
skipping: [localhost]

TASK: [edxapp | enable celery worker supervisor script] *********************** 
changed: [localhost]

TASK: [edxapp | syncdb and migrate] ******************************************* 
changed: [localhost] => (item=lms)
changed: [localhost] => (item=cms)

TASK: [edxapp | gather  static assets with paver] ***************************** 
skipping: [localhost] => (item=lms)
skipping: [localhost] => (item=cms)

TASK: [edxapp | make the course data updatable by the edxapp user] ************ 
skipping: [localhost]

TASK: [edxapp | clone the xml course repo] ************************************ 
skipping: [localhost] => (item=EDXAPP_XML_COURSES)

TASK: [edxapp | update course.xml] ******************************************** 
skipping: [localhost] => (item=EDXAPP_XML_COURSES)

TASK: [edxapp | make symlinks for the static data] **************************** 
skipping: [localhost] => (item=EDXAPP_XML_COURSES)

TASK: [edxapp | make symlinks so code works] ********************************** 
skipping: [localhost] => (item=EDXAPP_XML_COURSES)

TASK: [edxapp | import courses with nostatic flag] **************************** 
skipping: [localhost] => (item=EDXAPP_XML_COURSES)

TASK: [edxapp | import courses including static data] ************************* 
skipping: [localhost] => (item=EDXAPP_XML_COURSES)

TASK: [edxapp | delete courses that were fully imported] ********************** 
skipping: [localhost] => (item=EDXAPP_XML_COURSES)

TASK: [edxapp | create an archive of course data and course static dirs] ****** 
skipping: [localhost]

TASK: [edxapp | upload archive to s3] ***************************************** 
skipping: [localhost]

TASK: [edxapp | remove archive from disk] ************************************* 
skipping: [localhost]

TASK: [edxapp | update supervisor configuration] ****************************** 
changed: [localhost]

TASK: [edxapp | ensure edxapp has started] ************************************ 
skipping: [localhost] => (item=lms)
skipping: [localhost] => (item=cms)

TASK: [edxapp | ensure edxapp_workers has started] **************************** 
ok: [localhost] => (item={'queue': 'low', 'service_variant': 'cms', 'concurrency': 3})
ok: [localhost] => (item={'queue': 'default', 'service_variant': 'cms', 'concurrency': 4})
ok: [localhost] => (item={'queue': 'high', 'service_variant': 'cms', 'concurrency': 1})
ok: [localhost] => (item={'queue': 'low', 'service_variant': 'lms', 'concurrency': 1})
ok: [localhost] => (item={'queue': 'default', 'service_variant': 'lms', 'concurrency': 3})
ok: [localhost] => (item={'queue': 'high', 'service_variant': 'lms', 'concurrency': 4})
ok: [localhost] => (item={'queue': 'high_mem', 'service_variant': 'lms', 'concurrency': 2})

TASK: [edxapp | create symlinks from the venv bin dir] ************************ 
changed: [localhost] => (item=python)
changed: [localhost] => (item=pip)
changed: [localhost] => (item=django-admin.py)

TASK: [edxapp | create symlinks from the repo dir] **************************** 
changed: [localhost] => (item=manage.py)

TASK: [edxapp | remove read-only ssh key] ************************************* 
skipping: [localhost]

TASK: [edxapp | get instance information] ************************************* 
skipping: [localhost]

TASK: [edxapp | tag instance with edx_platform version] *********************** 
skipping: [localhost]

TASK: [edxapp | tag instance  with edxapp theme version] ********************** 
skipping: [localhost]

TASK: [edxapp | set_fact edxapp_installed=true] ******************************* 
ok: [localhost]

TASK: [edxapp | create application user] ************************************** 
ok: [localhost]

TASK: [edxapp | create edxapp user dirs] ************************************** 
ok: [localhost] => (item=/edx/app/edxapp)
ok: [localhost] => (item=/edx/app/edxapp/.ssh)
ok: [localhost] => (item=/edx/var/edxapp)
ok: [localhost] => (item=/edx/app/edxapp/venvs)
ok: [localhost] => (item=/edx/var/edxapp/themes)
ok: [localhost] => (item=/edx/var/edxapp/staticfiles)
ok: [localhost] => (item=/edx/var/edxapp/course_static)
changed: [localhost] => (item=/edx/var/edxapp/data)

TASK: [edxapp | make the course data dir] ************************************* 
ok: [localhost]

TASK: [edxapp | create edxapp log dir] **************************************** 
ok: [localhost]

TASK: [edxapp | create web-writable edxapp data dirs] ************************* 
changed: [localhost] => (item=/edx/var/edxapp/data)
ok: [localhost] => (item=/edx/var/edxapp/uploads)

TASK: [edxapp | add ppas for current versions of nodejs] ********************** 
ok: [localhost]

TASK: [edxapp | install system packages on which LMS and CMS rely] ************ 
ok: [localhost]

TASK: [edxapp | set up edxapp .npmrc] ***************************************** 
changed: [localhost]

TASK: [edxapp | create log directories for service variants] ****************** 
ok: [localhost] => (item=lms)
ok: [localhost] => (item=cms)

TASK: [edxapp | code sandbox | Use libblas for 3gf] *************************** 
changed: [localhost]

TASK: [edxapp | code sandbox | Use liblapac for 3gf] ************************** 
changed: [localhost]

TASK: [edxapp | code sandbox | Create edxapp sandbox user] ******************** 
ok: [localhost]

TASK: [edxapp | code sandbox | Install apparmor utils system pkg] ************* 
ok: [localhost]

TASK: [edxapp | code sandbox | write out apparmor code sandbox config] ******** 
ok: [localhost]

TASK: [edxapp | code sandbox | write out sandbox user sudoers config] ********* 
ok: [localhost]

TASK: [edxapp | code sandbox | start apparmor service] ************************ 
ok: [localhost]

TASK: [edxapp | code sandbox | (bootstrap) load code sandbox profile] ********* 
changed: [localhost]

TASK: [edxapp | code sandbox | (bootstrap) put code sandbox into aa-enforce or aa-complain mode depending on EDXAPP_SANDBOX_ENFORCE] *** 
changed: [localhost]

TASK: [edxapp | setup the edxapp env] ***************************************** 
ok: [localhost]

TASK: [edxapp | create ssh script for git (not authenticated)] **************** 
ok: [localhost]

TASK: [edxapp | create ssh script for git (authenticated)] ******************** 
skipping: [localhost]

TASK: [edxapp | install read-only ssh key] ************************************ 
skipping: [localhost]

TASK: [edxapp | checkout edx-platform repo into {{edxapp_code_dir}}] ********** 
ok: [localhost]

TASK: [edxapp | git clean after checking out edx-platform] ******************** 
changed: [localhost]

TASK: [edxapp | checkout theme] *********************************************** 
skipping: [localhost]

TASK: [edxapp | create checksum for requirements, package.json and Gemfile] *** 
failed: [localhost] => {"changed": true, "cmd": "/usr/bin/md5sum /edx/app/edxapp/edx-platform/requirements/edx/pre.txt /edx/app/edxapp/edx-platform/requirements/edx/post.txt /edx/app/edxapp/edx-platform/requirements/edx/base.txt /edx/app/edxapp/edx-platform/requirements/edx/custom.txt /edx/app/edxapp/edx-platform/requirements/edx/paver.txt /edx/app/edxapp/edx-platform/requirements/edx-sandbox/post.txt /edx/app/edxapp/edx-platform/requirements/edx-sandbox/base.txt 2>/dev/null > /var/tmp/edxapp.req.new ", "delta": "0:00:00.004302", "end": "2015-07-29 22:23:54.981352", "item": "", "rc": 1, "start": "2015-07-29 22:23:54.977050"}
...ignoring

TASK: [edxapp | stat path=/var/tmp/edxapp.req.new] **************************** 
ok: [localhost]

TASK: [edxapp | stat path=/var/tmp/edxapp.req.installed] ********************** 
ok: [localhost]

TASK: [edxapp | Updating requirement files for git mirror] ******************** 
changed: [localhost]

TASK: [edxapp | gem install bundler] ****************************************** 
changed: [localhost]

TASK: [edxapp | bundle install] *********************************************** 
changed: [localhost]

TASK: [edxapp | Set the npm registry] ***************************************** 
skipping: [localhost]

TASK: [edxapp | Set the npm registry permissions] ***************************** 
changed: [localhost]

TASK: [edxapp | Install edx-platform npm dependencies] ************************ 
changed: [localhost]

TASK: [edxapp | install python pre-requirements] ****************************** 
skipping: [localhost]

TASK: [edxapp | install python base-requirements] ***************************** 
skipping: [localhost]

TASK: [edxapp | install python post-requirements] ***************************** 
skipping: [localhost]

TASK: [edxapp | install python paver-requirements] **************************** 
skipping: [localhost]

TASK: [edxapp | stat path="{{custom_requirements_file}}"] ********************* 
ok: [localhost]

TASK: [edxapp | install python custom-requirements] *************************** 
skipping: [localhost]

TASK: [edxapp | install python post-post requirements] ************************ 
changed: [localhost] => (item=/edx/app/edxapp/edx-platform/requirements/edx/github.txt)
changed: [localhost] => (item=/edx/app/edxapp/edx-platform/requirements/edx/local.txt)

TASK: [edxapp | install python private requirements] ************************** 
skipping: [localhost] => (item=/edx/app/edxapp/edx-platform/requirements/edx/edx-private.txt)

TASK: [edxapp | install python extra requirements] **************************** 
skipping: [localhost]

TASK: [edxapp | install CAS attribute module] ********************************* 
skipping: [localhost]

TASK: [edxapp | install sandbox requirements into regular venv] *************** 
skipping: [localhost] => (item=/edx/app/edxapp/edx-platform/requirements/edx-sandbox/base.txt)
skipping: [localhost] => (item=/edx/app/edxapp/edx-platform/requirements/edx-sandbox/local.txt)
skipping: [localhost] => (item=/edx/app/edxapp/edx-platform/requirements/edx-sandbox/post.txt)

TASK: [edxapp | code sandbox | put sandbox apparmor profile in complain mode] *** 
changed: [localhost]

TASK: [edxapp | code sandbox | Install base sandbox requirements and create sandbox virtualenv] *** 
ok: [localhost]

TASK: [edxapp | code sandbox | Install sandbox requirements into sandbox venv] *** 
ok: [localhost] => (item=/edx/app/edxapp/edx-platform/requirements/edx-sandbox/local.txt)
ok: [localhost] => (item=/edx/app/edxapp/edx-platform/requirements/edx-sandbox/post.txt)

TASK: [edxapp | code sandbox | put code sandbox into aa-enforce or aa-complain mode, depending on EDXAPP_SANDBOX_ENFORCE] *** 
changed: [localhost]

TASK: [edxapp | compiling all py files in the edx-platform repo] ************** 
changed: [localhost]

TASK: [edxapp | give other read permissions to the virtualenv] **************** 
changed: [localhost]

TASK: [edxapp | create checksum for installed requirements] ******************* 
changed: [localhost]

TASK: [edxapp | openid workaround] ******************************************** 
changed: [localhost]

TASK: [edxapp | get s3 one time url] ****************************************** 
skipping: [localhost]

TASK: [edxapp | download from one time url] *********************************** 
skipping: [localhost]

TASK: [edxapp | unzip the data to the data dir] ******************************* 
skipping: [localhost]

TASK: [edxapp | make the course data web user writable] *********************** 
ok: [localhost]

TASK: [edxapp | create  application config] *********************************** 
ok: [localhost] => (item=lms)
ok: [localhost] => (item=cms)

TASK: [edxapp | create  auth file] ******************************************** 
ok: [localhost] => (item=lms)
ok: [localhost] => (item=cms)

TASK: [edxapp | writing  supervisor script] *********************************** 
ok: [localhost] => (item=lms)
ok: [localhost] => (item=cms)

TASK: [edxapp | writing edxapp supervisor script] ***************************** 
ok: [localhost]

TASK: [edxapp | writing celery worker supervisor script] ********************** 
ok: [localhost]

TASK: [edxapp | enable  supervisor script] ************************************ 
changed: [localhost] => (item=lms)
changed: [localhost] => (item=cms)

TASK: [edxapp | enable edxapp supervisor script] ****************************** 
changed: [localhost]

TASK: [edxapp | enable celery worker supervisor script] *********************** 
skipping: [localhost]

TASK: [edxapp | syncdb and migrate] ******************************************* 
changed: [localhost] => (item=lms)
changed: [localhost] => (item=cms)

TASK: [edxapp | gather  static assets with paver] ***************************** 
changed: [localhost] => (item=lms)
	changed: [localhost] => (item=cms)

TASK: [edxapp | make the course data updatable by the edxapp user] ************ 
skipping: [localhost]

TASK: [edxapp | clone the xml course repo] ************************************ 
skipping: [localhost] => (item=EDXAPP_XML_COURSES)

TASK: [edxapp | update course.xml] ******************************************** 
skipping: [localhost] => (item=EDXAPP_XML_COURSES)

TASK: [edxapp | make symlinks for the static data] **************************** 
skipping: [localhost] => (item=EDXAPP_XML_COURSES)

TASK: [edxapp | make symlinks so code works] ********************************** 
skipping: [localhost] => (item=EDXAPP_XML_COURSES)

TASK: [edxapp | import courses with nostatic flag] **************************** 
skipping: [localhost] => (item=EDXAPP_XML_COURSES)

TASK: [edxapp | import courses including static data] ************************* 
skipping: [localhost] => (item=EDXAPP_XML_COURSES)

TASK: [edxapp | delete courses that were fully imported] ********************** 
skipping: [localhost] => (item=EDXAPP_XML_COURSES)

TASK: [edxapp | create an archive of course data and course static dirs] ****** 
skipping: [localhost]

TASK: [edxapp | upload archive to s3] ***************************************** 
skipping: [localhost]

TASK: [edxapp | remove archive from disk] ************************************* 
skipping: [localhost]

TASK: [edxapp | update supervisor configuration] ****************************** 
changed: [localhost]

TASK: [edxapp | ensure edxapp has started] ************************************ 
ok: [localhost] => (item=lms)
ok: [localhost] => (item=cms)

TASK: [edxapp | ensure edxapp_workers has started] **************************** 
skipping: [localhost] => (item={'queue': 'low', 'service_variant': 'cms', 'concurrency': 3})
skipping: [localhost] => (item={'queue': 'default', 'service_variant': 'cms', 'concurrency': 4})
skipping: [localhost] => (item={'queue': 'high', 'service_variant': 'cms', 'concurrency': 1})
skipping: [localhost] => (item={'queue': 'low', 'service_variant': 'lms', 'concurrency': 1})
skipping: [localhost] => (item={'queue': 'default', 'service_variant': 'lms', 'concurrency': 3})
skipping: [localhost] => (item={'queue': 'high', 'service_variant': 'lms', 'concurrency': 4})
skipping: [localhost] => (item={'queue': 'high_mem', 'service_variant': 'lms', 'concurrency': 2})

TASK: [edxapp | create symlinks from the venv bin dir] ************************ 
ok: [localhost] => (item=python)
ok: [localhost] => (item=pip)
ok: [localhost] => (item=django-admin.py)

TASK: [edxapp | create symlinks from the repo dir] **************************** 
ok: [localhost] => (item=manage.py)

TASK: [edxapp | remove read-only ssh key] ************************************* 
skipping: [localhost]

TASK: [edxapp | get instance information] ************************************* 
skipping: [localhost]

TASK: [edxapp | tag instance with edx_platform version] *********************** 
skipping: [localhost]

TASK: [edxapp | tag instance  with edxapp theme version] ********************** 
skipping: [localhost]

TASK: [edxapp | set_fact edxapp_installed=true] ******************************* 
ok: [localhost]

TASK: [demo | create demo app and data dirs] ********************************** 
changed: [localhost]

TASK: [demo | check out the demo course] ************************************** 
changed: [localhost]

TASK: [demo | import demo course] ********************************************* 
changed: [localhost]

TASK: [demo | create some test users and enroll them in the course] *********** 
changed: [localhost] => (item={'password': 'edx', 'email': 'honor@example.com', 'mode': 'honor'})
changed: [localhost] => (item={'password': 'edx', 'email': 'audit@example.com', 'mode': 'audit'})
changed: [localhost] => (item={'password': 'edx', 'email': 'verified@example.com', 'mode': 'verified'})

TASK: [demo | create staff user] ********************************************** 
changed: [localhost]

TASK: [demo | add test users to the certificate whitelist] ******************** 
changed: [localhost] => (item={'password': 'edx', 'email': 'honor@example.com', 'mode': 'honor'})
changed: [localhost] => (item={'password': 'edx', 'email': 'audit@example.com', 'mode': 'audit'})
changed: [localhost] => (item={'password': 'edx', 'email': 'verified@example.com', 'mode': 'verified'})

TASK: [demo | seed the forums for the demo course] **************************** 
changed: [localhost] => (item={'password': 'edx', 'email': 'honor@example.com', 'mode': 'honor'})
changed: [localhost] => (item={'password': 'edx', 'email': 'audit@example.com', 'mode': 'audit'})
changed: [localhost] => (item={'password': 'edx', 'email': 'verified@example.com', 'mode': 'verified'})

TASK: [rabbitmq | trust rabbit repository] ************************************ 
changed: [localhost]

TASK: [rabbitmq | install python-software-properties if debian] *************** 
changed: [localhost]

TASK: [rabbitmq | add rabbit repository] ************************************** 
changed: [localhost]

TASK: [rabbitmq | fetch the rabbitmq server deb] ****************************** 
changed: [localhost]

TASK: [rabbitmq | check if rabbit is installed] ******************************* 
changed: [localhost]

TASK: [rabbitmq | install rabbit package using gdebi] ************************* 
changed: [localhost]

TASK: [rabbitmq | stop rabbit cluster] **************************************** 
changed: [localhost]

TASK: [rabbitmq | send sigterm to any running rabbitmq processes] ************* 
changed: [localhost]

TASK: [rabbitmq | create rabbitmq edx directories] **************************** 
changed: [localhost] => (item=/edx/app/rabbitmq)
changed: [localhost] => (item=/edx/var/log/rabbitmq)

TASK: [rabbitmq | add queue monitoring script] ******************************** 
changed: [localhost]

TASK: [rabbitmq | set up a cron job to run the script] ************************ 
changed: [localhost]

TASK: [rabbitmq | create cookie directory] ************************************ 
ok: [localhost]

TASK: [rabbitmq | add rabbitmq erlang cookie] ********************************* 
changed: [localhost]

TASK: [rabbitmq | create rabbitmq config directory] *************************** 
ok: [localhost]

TASK: [rabbitmq | add rabbitmq environment configuration] ********************* 
changed: [localhost]

TASK: [rabbitmq | add rabbitmq cluster configuration] ************************* 
changed: [localhost]

TASK: [rabbitmq | install plugins] ******************************************** 
changed: [localhost]

TASK: [rabbitmq | remove mnesia configuration] ******************************** 
changed: [localhost]

TASK: [rabbitmq | start rabbit nodes] ***************************************** 
changed: [localhost]

TASK: [rabbitmq | wait for rabbit to start] *********************************** 
ok: [localhost]

TASK: [rabbitmq | remove guest user] ****************************************** 
changed: [localhost]

TASK: [rabbitmq | add vhosts] ************************************************* 
ok: [localhost] => (item=/)

TASK: [rabbitmq | add admin users] ******************************************** 
changed: [localhost] => (item=[{'password': 'the example admin password', 'name': 'admin'}, '/'])
changed: [localhost] => (item=[{'password': 'edx', 'name': 'edx'}, '/'])
changed: [localhost] => (item=[{'password': 'celery', 'name': 'celery'}, '/'])

TASK: [rabbitmq | make queues mirrored] *************************************** 
skipping: [localhost]

TASK: [rabbitmq | install admin tools] **************************************** 
changed: [localhost]

TASK: [rabbitmq | ensure rabbitmqadmin attributes] **************************** 
changed: [localhost]

TASK: [oraclejdk | download Oracle Java] ************************************** 


````
