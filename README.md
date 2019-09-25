Ansible Satellite 6 Install
===========================

Role to install and do basic configuration of Red Hat Satellite 6.x on RHEL 7.x

INFORMATION
-----------

This playbook will take a while to run depending on the number of repositories to sync.

Requirements
------------

You will need ansible and all the required subscriptions for RHEL 7 and Satellite 6.

* Disk Partitioning to support Satellite Directories. Refer to installation guide.
* DNS
* NTP
* satellite_deployment_manifest_path variable defined 
* Satellite Manifest file hosted in the Ansible Bastion or available via HTTP or FTP somewhere in the environment.

Role Variables
--------------

All variables are in files located in defaults/main.yml


Dependencies
------------

There is no role dependency for this role.

Inventory File
----------

The example of inventory file for this role is in `hosts.target`.

How to run the playbook
------------------------

1. To run the playbook first you need to create and download the manifest:
   * Go to the [Subscriptions Allocations](https://access.redhat.com/management/subscription_allocations) section in the Red Hat Customer Portal.
   * Click the Create "New Subscription Allocation" button.
   * Name field: Enter the name for this allocation (using a reference to the Satellite host for later identification is recommended, for ex. organization-satellite-01).
   * Type field: Select the Satellite version (this playbook supports from Satellite 6.1 to 6.4)
   * Click the "Create" button.
2. Now we are going to attach a subscription.
   * Click the "Subscriptions" tab for the created allocation
   * Click the "Add Subscriptions" button.
   * Select the subscriptions you want to add to this Satellite's manifest.
   * Click the "Submit" button   
3. After attaching the subscriptions to the allocation we have to download the manifest file:
   * Click "Download manifest"
4. Copy the downloaded file inside the `/files` directory on the role and name it `satellite_manifest.zip`
5. Then update the variable file in `defaults/main.yml` in your playbook and set all mandatory variables for the role.

You can see an [example of the playbook config here](./playbook_example/config.yml)

```
cd playbook_example
ansible-playbook -i hosts.target -e '{satellite_deployment_vars: ./vars/main.yml}' config.yml
```

Run the playbook, see [README of example playbook](./playbook_example/README.md).


License
-------

MIT

Author Information
------------------

Julio Villarreal Pelegrino <julio@linux.com> more at: http://wwww.juliovillarreal.com

**Contributors:**

* Petr Balogh - <petr.balogh@gmail.com>
* Joe Pisciotta - <josephpisciott@mac.com>
* Nick Poyant - <npoyant@redhat.com>
* Cameron Wyatt - <cwyatt@redhat.com>
