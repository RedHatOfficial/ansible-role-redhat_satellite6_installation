Ansible Satellite 6 Install
===========================

Role to install and do basic configuration of Red Hat Satellite 6.X.

Information
-----------

This playbook will take a while to run depending the number of repositories to sync.

Requirements
------------

You will need Ansible and all the required subscriptions for Red Hat Enterprise Linux 7 and Satellite 6.

* Proper disk partitioning to support Satellite Directories. Refer to the [offical installation guide](https://access.redhat.com/documentation/en-us/red_hat_satellite/6.5/html/installing_satellite_server_from_a_connected_network/preparing_your_environment_for_installation#hardware_storage_prerequisites) - there is also an [Ansible role available](https://github.com/RedHatOfficial/ansible-redhat-satellite6/tree/master/roles/redhat_satellite6_storage).
* DNS
* NTP
* ``satellite_deployment_manifest_path`` variable defined 
* Satellite Manifest file is hosted on the Ansible Bastion or available via HTTP or FTP somewhere in the environment.

Role Variables
--------------

All variables are in files located in ``defaults/main.yml``.


Dependencies
------------

There are no role dependencies for this role.

Inventory File
----------

The example of inventory file for this role is in [``hosts.target``](playbook_example/hosts.target).

How to run the playbook
------------------------

* To run the playbook first you need to create and download the manifest:

Go to <http://rhn.redhat.com>.
- Click "Subscription Allocations"
- Click "New Subscriptoin Allocation"
- Set a Name, select a Satellite version next to **Type** and click "Create"
After this we are going to  attach a subscription.
- Click "Subscriptions" and "Attach Subscription" and select the subscription to attach and click "Attach Selected"
After this we will download the manifest.
- Click "Details" and "Export manifest"
After this copy the download file inside the /files directory on the role and
name it "satellite_manifest.zip"

** Then update the variable file in ``defaults/main.yml`` in your playbook and
set all mandatory variables for role: **

You can see example of playbook in [``playbook_example/config.yml``](playbook_example/config.yml).

* ``cd playbook_example``
* ``ansible-playbook -i hosts.target -e '{satellite_deployment_vars: ./vars/main.yml}' config.yml``
* Run the playbook, see [``README.md`` of example playbook](playbook_example/README.md)

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

Christian Stankowic - <info@cstan.io>
