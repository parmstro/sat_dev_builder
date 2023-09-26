# sat_dev_builder
Created from rhis_builder code, this repo is targeted at building a Satellite and Capsule infrastructure from scratch using the redhat.satellite collection. The primary purpose I created this for was to build out a full infrastructure to develop foreman-ansible-modules and satellite-ansible-modules against. 

The included variables create a fully configured Satellite. 
You can edit the variable files to create whatever configurations you need. 

Part of the goal of this particular adventure is to start building the structure and content to define a bunch of different know configurations for Satellite, with the goal of being able to share them and use them to drive IaC for Satellite configuration and pipelines for testing Standard Operating Environments.

Contributions and Pull Requests welcome. 

### Notes:

At this time, do not run ansible-playbook ... site.yml as the code currently does not build the other elements of the site. See below.

There are a *lot* of variables!
You will need to update them for your environment. Part of this project will be to provide many samples in the directory that supports the target configuration.
e.g. We will put sample manifest configurations in the vars/manifest directory

What you need to get started:
- the requirements file should take care of the ansible dependencies. If you find something missing, please let us know.
- You need:
  - an ansible vault file named 'rhisbuilder_vault.yml' in your home directory. It contains all your secrets. The main variable required here is 'token:' - your refresh token for imagebuilder on console.redhat.com
  - a vault password file to decrypt the above and any other vault files that are present. More on that later.
    
This is a work in progress, so trying to ensure all this is documented will take time.
The big thinks to set up in the variable files.
- your installer config
- your network - domain names, ip ranges, etc..
- your virtual environment / compute resources / compute profiles
- OSCAP files
- many of the other satellite configurations are designed to give you a running satellite environment with a solid starting point for an SOE

Please open issues if you want to request something or find a bug.


### Run the playbook to install and configure a Satellite Server

The following will work for a baremetal deployment (pre-provisioned host) or vmware deployment.

ansible-playbook -i inventory sat/main.yml -e "rhisbuilder_bootstrap_target='vmware'"  


