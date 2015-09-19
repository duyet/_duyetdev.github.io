---
layout: post
title: Install Odoo 8 in Ubuntu 14.04/15.04
---

Install Odoo 8 in Ubuntu 14.04/15.04

**Note:** You can simply [download](https://www.odoo.com/page/download) a .deb (for Debian/Ubuntu type systems) or a. rpm (Redhat/CentOS) package of OpenERP and install that. Unfortunately that approach doesn’t provide us (Libertus Solutions) with enough fine-grained control over where things get installed, and it restricts our flexibility to modify & customise, hence I prefer to do it a slightly more manual way (this install process below should only take about 10-15 minutes once the host machine has been built).

# Step 1. Create the Odoo user that will own and run the application
````bash
sudo adduser --system --home=/opt/odoo --group odoo
````

* This is a **"system"** user. It is there to own and run the application, it isn’t supposed to be a person type user with a login etc.
* I"ve specified a **"home"** of `/opt/odoo`, this is where the OpenERP server code will reside and is created automatically by the command above.

Note: How to run the Odoo server as the odoo system user from the command line if it has no shell. 
````bash
sudo su - odoo -s /bin/bash
````

# Step 2. Install and configure the database server, PostgreSQL
````bash
sudo apt-get install postgresql
````

Then configure the Odoo user on **postgres**:

First change to the postgres user so we have the necessary privileges to configure the database.
````
sudo su - postgres
````

Now create a new database user. This is so Odoo has access rights to connect to PostgreSQL and to create and drop databases. Remember what your choice of password is here; you will need it later on:

````
createuser --createdb --username postgres --no-createrole --no-superuser --pwprompt odoo
Enter password for new role: ********
Enter it again: ********
````

Finally exit from the postgres user account:
````
exit
````

# Step 3. Install the necessary Python libraries for the server
````bash
sudo apt-get install python-cups python-dateutil python-decorator python-docutils python-feedparser \
python-gdata python-geoip python-gevent python-imaging python-jinja2 python-ldap python-libxslt1\
python-lxml python-mako python-mock python-openid python-passlib python-psutil python-psycopg2\
python-pybabel python-pychart python-pydot python-pyparsing python-pypdf python-reportlab python-requests \
python-simplejson python-tz python-unicodecsv python-unittest2 python-vatnumber python-vobject \
python-werkzeug python-xlwt python-yaml wkhtmltopdf
````

# Step 4. Install the Odoo server
Install Git.
````
sudo apt-get install git
````

Switch to the Odoo user:
````
sudo su - odoo -s /bin/bash
````

Grab a copy of the most current Odoo 8 branch (Note the “.” at the end of this command!):
````
git clone https://www.github.com/odoo/odoo --depth 1 --branch 8.0 --single-branch .
````

Step 5. Configuring the OpenERP application
The default configuration file for the server (`/opt/odoo/debian/openerp-server.conf`) is actually very minimal and will, with only a small change work fine so we’ll copy that file to where we need it and change it’s ownership and permissions:

````
sudo cp /opt/odoo/debian/openerp-server.conf /etc/odoo-server.conf
sudo chown odoo: /etc/odoo-server.conf
sudo chmod 640 /etc/odoo-server.conf
````

The above commands make the file owned and writeable only by the odoo user and group and only readable by odoo and root.

To allow the odoo server to run initially, you should only need to change two lines in this file. Toward to the top of the file change the line db_password = False to the same password you used back in step 3. Then modify the line addons_path = /usr/lib/python2.7/dist-packages/openerp/addons so that it reads addons_path = /opt/odoo/addons instead.

One other line we might as well add to the configuration file now, is to tell Odoo where to write its log file. To complement my suggested location below add the following line to the odoo-server.conf file:
````
logfile = /var/log/odoo/odoo-server.log
````
Use your favourite text editor here. I tend to use nano, e.g.
````
sudo nano /etc/odoo-server.conf
````
Once the configuration file is edited and saved, you can start the server just to check if it actually runs.
````
sudo su - odoo -s /bin/bash
/opt/odoo/openerp-server
````
If you end up with a few lines eventually saying OpenERP (Yes. The log still says OpenERP and not Odoo) is running and waiting for connections then you are all set.

If there are errors, you’ll need to go back and find out where the problem is.

Otherwise simply enter CTL+C to stop the server and then exit to leave the openerp user account and go back to your own shell.
