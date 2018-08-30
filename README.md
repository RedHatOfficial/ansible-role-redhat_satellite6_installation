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
Satellite 6.

* Disk Partitioning to support Satellite Directories. Refer to installation guide.
* DNS
* NTP
* satellite_deployment_manifest_path variable defined 
* Satellite Manifest file is hosted on the Ansible Bastion or available via HTTP or FTP somewhere in the environment.

Role Variables
--------------

All variables are in files located in defaults/main.yml


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

** Then update the variable file in defaults/main.yml in your playbook and
set all mandatory variables for role.:

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

Cameron Wyatt - <cwyatt@redhat.com>
