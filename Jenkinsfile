library('oasis-pipeline')

oasisMultistreamMoleculePipeline {
  upstream_git_url = 'https://github.com/oasis-roles/ansible-role-redhat_satellite6_installation.git'
  molecule_role_name = 'ansible-role-redhat_satellite6_installation'
  molecule_scenarios = ['openstack']
  properties = [pipelineTriggers([cron('H H * * *')])]
}