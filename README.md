# Ansible JWS demo

This playbook demonstrate how to install and upgrade Apache Tomcat (or JBoss Web Server) and also deploy and update a webapp using Ansible.

## Requirements

This demo has been tested on a RHEL 8.4 system using Ansible 2.9.22 (as provided by Red Hat) running wit Python3.

    $ ansible-galaxy collection install redhat.jws

This collection is available on Automation Hub. For Ansible Galaxy to be able to download, the ansible.cfg needs to be configured to use it:

TODO

Alternatively, you can use the upstream version of this collection (you'll need to adapt the provided playbooks):

    $ ansible-galaxy collection install middleware_automation-jws-0.0.1.tar.gz
    Process install dependency map
    Starting collection install process
    Installing 'middleware_automation.jws:0.0.1' to '/root/.ansible/collections/ansible_collections/middleware_automation/jws'
    Installing 'middleware_automation.redhat_csp_download:1.1.1' to '/root/.ansible/collections/ansible_collections/middleware_automation/redhat_csp_download

## Run the demo

Then run Ansible to install JWS and the demo app:

    $ ansible-playbook install_jws_and_webapp.yml

To update the application, run again Ansible:

    $ ansible-playbook -e app_version=1.1 install_jws_and_webapp.yml

To downgrade the application, run again Ansible:

    $ ansible-playbook -e app_version=1.0 install_jws_and_webapp.yml
