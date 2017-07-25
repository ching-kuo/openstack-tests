# Ansible Playbooks for Testing OpenStack Cloud

## Status

This playbook will test functionality of main projects in OpenStack including:

- Keystone
- Nova
- Glance
- Cinder
- Neutron

## Requirments 

- [Install Ansible](http://docs.ansible.com/ansible/intro_installation.html)
- [Install openstack shade](http://docs.openstack.org/infra/shade/installation.html)
- Clone this project into a directory.
- [Download Cirros Image](http://download.cirros-cloud.net/0.3.5/cirros-0.3.5-x86_64-disk.img)

## Ansible

Ansible and OpenStack Shade will be used to provision all of the OpenStack
resources required to test basic functions.

### Prepration

#### Create ssh key

If you do not have a ssh key, then you should create one by using a tool.
Example command:

    ssh-keygen -t rsa
    eval $(ssh-agent -s)
    ssh-add ~/.ssh/id_rsa

#### General Openstack Settings

Ansible's OpenStack Cloud Modules is used to test your OpenStack clouds. Before running the script, 
the cloud environment will have to be specified. Sample file have been provided in vars directory.

## Start the Test

With your cloud environment set, you should be able to run the script:

    ansible-playbook -e "action=apply env=test" site.yml

This command will start the playbook on cloud "test" (vars/test.yml)

## Next Step

If there are no errors, there should be a cirros instance running on your cloud and 
a volume attached to it.

## Clean Up

Once you're done with the test, remember to nuke the whole thing by:

    ansible-playbook -e "action=destroy env=test" site.yml

This command will destroy all the resources created.
