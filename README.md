# Freeradius-playbook

This is an ansible Playbook that will configure freeradius on a linux server 

It requires a couple of inputs to run successfully

This was designed with the specific purpose of intregrating with Azure AD Domain Services and auththenicaing against Azure AD

You have to have Azure AD DS setup first along with a Linux VM created in that Azure Domain before you run this playbook.

Freeradius is configured in this instance to use a combination of Samba and WinBind to establish a connection to Azure AD to pull and verify the correct
credinitals when trying to Auth. 

Once Azure ADDS is setup Run this playbook it will need the following items

1. The password to connect to the Linux VM to run the playbook
2. Since this is a radius server it will need the Client IP address that will be connecting to it
3. A bind user (This is a user that is already setup with Admin permissions in Azure AD)
4. A bind password
5. Name of your Azure Domain Services Domain (in all caps)
6. Name of the realm to be configured ( IE testdomain.com)

After the above inputs are provided the runbook will configure the linux vm install freeradius and configure it to use the above setup. 

Note** This setup uses the default Snake oil certs that free radius provides! To secure your auth connection you will need to configure This setup with a proper
cert!! 

