# Inviqa Ansible Provision

## Prerequisites

You must have a Python > 2.6 (not system Python on Mac OSX) with pip:

```bash
brew install python
```
## Installation
Clone this repo to your local machine:

```bash
git clone https://github.com/inviqa/ansible-provision.git
cd ansible-provision
```
place or link the `ansible-provision` directory in your `/opt/` system directory
add `/opt/ansible-provision` your $PATH env

## Configuration
ansbile-provision makes use of the [ansible-seed-inviqa] repo to seed a default set of roles, tasks, vars and playbook to be used within a project

- seed the Ansible Provision directory (usaully `tools/ansible`) into a project using the ansible-provision script option  `--seed-dir <project_tools_path>/ansible`
```
ansible-provision --seed-dir ~/sites/some_project_dir/tools/ansible
```
- Create your `inventory`, `host_vars` and `group_vars` files according to the [ansible-seed-inviqa] documentation
- run the Ansible Provision script
i.e.
```
#if no `-p <playbook>` option is specified the main 'provision.yml' playbook will be run
~/Development/ansible-provision/ansible-provision
```
## Allowed parameters
```
Specify the PIP Requireents file (usually stored in the same dir as the ansible-provision script)
--pfile <pip_requirements_file>

Specify the command or a pathname to the command to create the virtual environment with.
For example pyvenv, virtualenv, virtualenv2, ~/bin/virtualenv, /usr/local/bin/virtualenv.
--venv <ansible_virtual_environement>

Choose which Ansible version to install in the VirtualEnv
--ansible-version <ansible_version>

Trigger the Ansible seeding into aproject
-s|--seed

Choose the destination where to install the seed within your project, usually `tools/ansible`
--seed-dir <seed_destionation_dir>

Choose which Seed you want to use
--seed-url <git_url_to_seed>

Choose which Ansible tags to be run
-t|--tags <tags>

Needed if you are provisioning using an Admin user (enabled to run `sudo`), especially useful when root ssh access is disallowed
-u|--user <remote_user_id>

This will make ansible to ask for the `become` password, which is needed if you are provisioning using an Admin user (enabled to run `sudo`)
-K|--ask-become-pass

Specify the Inventory file to use
-i|--inventory <inventory_file>

Limiti the provisioning to specific host(s) or group(s)
-l|--limit <hosts,groups>

Specify the Playbook file to use
-p|--playbook <playbook_file>

Specify the Galaxy roles file to be installed
--rfile <ansible_roles_file>

Specify the Galaxy roles destination (usuall `tools/ansible/.galaxy/)
--rpath <ansible_role_path>

Specify the Ansible Vault Password file (should be saved with `600` permissions)
--vfile <ansible_vault_password_file>

Specify the verbosity level
Value 1-5 depending on the the number of `v` (default 0)
-v|-vv*
```
## Exaples
# provision localhost for tasks tagged 'developers'
```
ansible-provision -p playbook.yml -l localhost -t developers
```

## License
[MIT][license]

## Author Information
------------------
Authors Felicity Ratcliffe, Hardik Gajjarat, Marco Massari Calderone - Inviqa UK Ltd

Based on Barney Hanlon's work on the original [ansible-provisioning][ansible-provisioning] project for [Inviqa][inviqa]

[github] https://github.com/inviqa/ansible-provision "Github location of this role"
[ansible-seed-inviqa]]: https://github.com/inviqa/ansible-seed-inviqa "Inviqa's Ansible Seed"

[inviqa]: https://www.inviqa.com "Inviqa UK Ltd"

[license]: https://raw.githubusercontent.com/inviqa/ansible-jumpcloud/master/LICENSE
