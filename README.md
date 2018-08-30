Ansible Satellite 6 Install
===========================

Role to install and do basic configuration of Red Hat Satellite 6.X.

INFORMATION
-----------

This playbook will take a while to run depending the number of repositories to
sync.

Requirements
------------

You will need ansible and all the required subscriptions for RHEL 7 and
Satellite 6. Also please use some role for set NTP on your server. We recommend
you use ansible-galaxy and install role for NTP **bennojoy.ntp** like we do.

Role Variables
--------------

All variables are in files located in ./vars and are imported with specifics
tasks.
But to be open for others we decided specify only related variables there and
all mandatory variables you have to specify in playbook vars or pass in extra
vars parameter.

You can check default vars located in ./defaults/main.yml, where we specify
these variables you have to specify in your var file and overwrite them,
otherwise this role won't work properly.


Dependencies
------------

There is no role dependency for this role.

Inventory File
----------

The example of inventory file for this role is in  hosts.target.

How to run the playbook
------------------------

* To run the playbook first you need to create and download the manifest:

Go to <http://rhn.redhat.com>.
- Click "Satellite"
- Click "Register a Satellite"
- Set a Name, select a version and Click "Register"
After this we are going to  attach a subscription.
- Click "Attach Subscription" and select the subscription to attach and click
"Attach Selected"
After this we will download the manifest.
- Click "Download manifest"
After this copy the download file inside the /files directory on the role and
name it "satellite_manifest.zip"

** Then create the variable file in vars/your_name.yml in your playbook and
set all mandatory variables for role. You can inspire in vars/example-vars.yml.
And include this variable file in playbook as variable_files:

You can see example of playbook in playbook_example/config.yml

* Run the playbook, see README of example playbook

[playbook readme](./playbook_example/README.rst)


License
-------

MIT

Author Information
------------------

Julio Villarreal Pelegrino <julio@linux.com> more at: http://wwww.juliovillarreal.com

**Contributors:**

Petr Balogh - <petr.balogh@gmail.com>

Joe Pisciotta - <josephpisciott@mac.com>

Nick Poyant - <npoyant@redhat.com>
