splunk-ansible-advance
======================

Advance Ansible configuration to deploy Splunk. Implements dynamic inventory under the AWS platform. See [Managing Splunk with Ansible Part #2](http://blogs.splunk.com/2015/02/09/deploying-splunk-securely-with-ansible-config-management-part-2) for more information.

*part 2 of:* [Managing Splunk with Ansible Part #1](http://blogs.splunk.com/2014/07/12/deploying-splunk-securely-with-ansible-config-management-part-1/)  

## Installation
0. `apt-get install python-pip python-dev` install git/pip for your distribution 
1. `cd /opt/`
2. `sudo git clone https://github.com/ansible/ansible.git`
3. `sudo git submodule update --init --recursive`
4. `cd /etc/`
5. `sudo git clone https://github.com/divious1/splunk-ansible-advance.git ansible`
6. `pip install boto jinja2` (or install it from your distro package manager)
7. Configure AWS credentials for Ansible (Remember to use IAM to create the API user): 
```
$cat ~/.boto 
[Credentials]
aws_access_key_id = XXXXXXXXXXXXXXXX
aws_secret_access_key = xxxxxxxxxxxxxxxxxxxxxxxxxx
```
8. Test your dynamic script: `/etc/ansible/ec2.py --list`
9. configure splunk-ansible-advance via editing `/etc/ansible/group_vars/all.yml`
10. Setup your credentials `/etc/ansible/playbooks/splunk_creds/`
11. Copy the credentials just generated into a amazon key pair.
12. Configure Key Pair under `/etc/ansible/customer/[customer_name].yml`

## New Features
* common role now also installs is configure for automatic security updates (debian/ubuntu only)
* common role install ntp configuration
* made Splunk installation distro agnostic (Debian base or Redhat base). If you are going to use Debian base remember to configure sudoers under `/etc/ansible/roles/common/files/etc/sudoers`
* Splunk runs as splunk user and not root
* Multiple SSL Vulnerabilities addressed under web.conf
* Updated package to new Splunk binaries.
* Indexer/Universal Forwarder role have been completed!

## TODO
* Docs
* add CM role 


