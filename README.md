This Ansible Playbook can be used to install JBoss EAP 7 along with deploying applications to the server

Prerequisites for EAP 7 
-----------------------------

- Since for legal reasons, I cannot add the JBoss EAP binaries to this application, you need to download JBoss EAP 7.x from either of the following locations:
For Red Hat Customers:
https://access.redhat.com/jbossnetwork/restricted/listSoftware.html?product=appplatform&downloadType=distributions
For Non Red Hat Customers:
http://developers.redhat.com/products/eap/download/

Once JBoss EAP 7 is downloaded copy the zip file to roles/jboss-standalone/files/

- Only tested with Ansible 1.9+ 
- This ansible_playbook uses the Python Jinja2 library. This is most likely install for you by default, but in case it is not you can install it with:
sudo pip install Jinja2 
- Expected CentOS/RHEL 7.x hosts

Usage
-----------------------------

These playbooks deploy a very basic implementation of JBoss EAP 7,
To use them, first edit the "hosts" inventory file to contain the
hostnames of the machines on which you want JBoss deployed, and edit the 
group_vars/all file to set any JBoss configuration parameters you need.

To run the playbook to deploy JBoss EAP 7 without apps run:
	ansible-playbook -e file_name=<EAP_ZIP_FILE> -i hosts deploy-jboss.yml

To run the playbook to deploy JBoss EAP 7 with apps run:
	ansible-playbook -e deploy_apps=true,file_name=<EAP_ZIP_FILE> -i hosts deploy-jboss.yml

To run the playbook to deploy JBoss and apps run:
	ansible-playbook -i hosts deploy-jboss-and-apps.xml

When the playbook run completes, you should be able to see the JBoss Server running on the ports you chose, on the target machines.

This is a very simple playbook and could serve as a starting point for more complex JBoss-based projects. 
