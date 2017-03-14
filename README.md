# derico.deploy_plone_site

This Ansible role can be used to deploy code to a Plone site.
It works well in combination with ansible.plone_server.

## Usage

Create a deploy.yml file:

    ---
    # vim:ft=ansible:
    - name: deploy site
      gather_facts: yes
      serial: 1
      hosts: all
      roles:
        - role: deploy-plone-site

Define some needed vars, for example in host_vars or group_vars:

    $ cat group_vars/plone
    ---
    plone_instance_name: my-plone
    plone_buildout_user: plone_buildout
    plone_major_version: '5.0'

Then deploy with:

    ansible-playbook -i inventory-staging deploy.yml

You can use the following vars on the command line or in the deployment file:

to skip buildout run:

    skip_buildout: yes

to skip the mr.developer update:

    skip_checkout: yes

You can set these vars on the command line::

    ansible-playbook -i inventory-staging deploy.yml -e "skip_buildout=yes"
