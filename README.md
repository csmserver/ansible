# Ansible Playbook for CSM Server

## Install Ansible

```
  pip install ansible
```

## Clone this repository

```
  git clone https://github.com/csmserver/ansible.git
  cd ansible
```

## Edit update the production file
The example file with the list of production servers is included in the repo: `production`. The file needs to be updated accordingly. Here is the example:

```csm ansible_host=172.28.22.62 ansible_user=administrator```

It defines host `csm` with ip `172.28.22.62` and username `administrator`

# Play the playbook to install CSM Server

```
  ansible-playbook -i production site.yml --ask-become-pass --ask-pass
```

# The following steps will be done automatically

1. Installation of MySQL Server
2. Installation of supervisord module
3. Installation of CMS Server with all the required packages
4. Installation of CSM Plugin Engine


The default configuration variables are in group_vars/all file.

```
  # default root password for mysql 
  mysql_root_pass: root
  # default DB user for CSM Server
  dbuser: csm
  # default DB password for CSM Server
  dbpass: csm
  # default DB name for CSM Server
  dbname: csmdb

  # default installation path
  csm_path: /opt/csm

  # git repo for CSM Server file
  git_repo: https://github.com/csm-aut/csm.git

  # http proxy if needed ( could be removed )
  http_proxy: https://proxy-rtp-1.cisco.com:8080

  # supervisor user and password for http interface
  supervisor_webuser: supervisor
  supervisor_webpass: supervisor

  # Optional installation of CSM Plugin Engine
  install_csmpe: true
```


# Supervisord Web GUI
The CSM Server can be controlled by supervisord Web GUI.
The WebGUI is running on port 5001.

![Alt text](/Screenshots/supervisord.png) "Supervisord WebGUI Screenshot")


