#Satellite deployment

This playbook install all dependencies required by satellite, register RHN (if satellite_connected == true),
install satellite, and create some basic configuration of satellite.

##Configuration

You have to specify a lot of variables for satellite-deployment role.
This playbook assumes that you set all these variables in some variable file
and its path you have to pass as parameter: ``satellite-deployment-vars``

##Parameters

- **satellite-deployment-vars**
    This parameter should contains path to variable file which will describe
    all related variables for your Satellite server.
    For example: ./vars/brq-sat-instance.yml which is relative path from
    playbook.
    You can see examples in [example-vars.yml](./vars/example-vars.yml)

##Execution

- For execute playbook with whole process of deployment run:
  ``ansible-playbook -u root -i host.target -e
  '{satellite_deployment_vars: ./vars/path_to_your_vars.yml}' ./config.yml``

- You can also only update or run specific action with specify appropriate
  tags:
``ansible-playbook -u root -i host.target -e
  '{satellite_deployment_vars: ./vars/path_to_your_vars.yml}'
  --tags=update_satellite ./config.yml``

you can also exclude some tags with ``--skip-tags`` parameter of
ansible-playbook command.

##Tags

- **firewall**: set firewall
- **install_satellite**: install satellite
- **update_satellite**: update satellite
- **satellite_deployment_repositories**: deploy repositories
- **rhn**: register rhn
