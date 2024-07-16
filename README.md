# Ansible JWS demo

This playbook demonstrate how to install and upgrade Apache Tomcat (or JBoss Web Server) and also deploy and update a webapp using Ansible.

## How to use devfile to setup your dev environment

To use the `devfile.yaml` and set up your development environment with OpenShift Dev Spaces or Visual Studio Code, follow these steps:

1. **Clone the Repository**

    ```sh
    git clone https://github.com/ansible-middleware/jws-app-update-demo.git
    cd jws-app-update-demo
    ```
2. **Install OpenShift Dev Spaces or Visual Studio Code**

    - Download and install [OpenShift Dev Spaces](https://access.redhat.com/products/red-hat-openshift-dev-spaces), else you can directly use Dev Spaces from [Red Hat Developer Snadbox](https://console.redhat.com/openshift/sandbox) as well.
    - Download and install [Visual Studio Code](https://code.visualstudio.com/).

3. 1. **Open the Red Hat Dev Spaces(If you Red Hat subscription use this)**

    - Select `Red Hat Dev Spaces` option from above provided Red hat Developer Sandbox link.
    - Put [jws-app-update-demo](https://github.com/ansible-middleware/jws-app-update-demo.git) Git repo URL in the `Import from Git` option and click on `Create & Open`.

    2. **Open the Project in Visual Studio Code**

    - Open Visual Studio Code.
    - Open the project folder you cloned: `File > Open Folder...` and select the project directory.
    - Once the folder is open, click on the green button in the bottom-left corner (`><`) and select `New Dev Container`.

Both options will use the `devfile.yaml` to configure and start the development container. You can then start coding and run the playbook within this environment, without worrying about the prerequisite setup.

## Requirements

This demo has been tested on a RHEL 8.4 system using Ansible 2.9.22 (as provided by Red Hat) running wit Python3.

    $ ansible-galaxy collection install middleware_automation.jws

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
