# Ansible JWS demo

This playbook demonstrate how to install and upgrade Apache Tomcat (or JBoss Web Server) and also deploy and update a webapp using Ansible.

## Requirements

Ansible (2.9) and RHEL 8.4.

The provided role for JWS as also a dependency that needs to be install:

    $ ansible-galaxy install sabre1041.redhat-csp-download

## Run the demo

Add your RHN creds into a YAML file:

    rhn_username: xxxx@redhat.com
    rhn_password: 'PASSWORD!'

Then run Ansible to install JWS and the demo app:

    $ ansible-playbook -e @rhn_creds.yml -e @version_1.0.yml playbook.yml

To update the application, run again Ansible:

    $ ansible-playbook -e @rhn_creds.yml -e @version_1.1.yml  playbook.yml

Note: if you have register the system into RHN, attached the appropriate subscribtion and enable the repo associated to JWS, you can edit the defaults values of the jws role to install the software directly with RPM, without providing your RHN credentials to Ansible:

    ---
    jws:
    #  package: jws5
    # uncommend 'package:' and comment the next line
      rhn_url: 'https://access.redhat.com/jbossnetwork/restricted/softwareDownload.html?softwareId=90361'
      catalina:
        home: /var/opt/rh/scls/jws5


