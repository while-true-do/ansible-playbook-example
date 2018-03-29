# Ansible Playbook: Example
| An example playbook to show the usage of while-true-do roles.


## Motivation

Ansible Playbooks and using Ansible Roles in a defined way are base concepts of Ansible. This repository should show, how you can use roles and what they are doing.

## Installation

Install from [Github](https://github.com/while-true-do/ansible-playbook-example)

```
git clone https://github.com/while-true-do/ansible-playbook-example.git
```

## Requirements

- ansible
- at least one test machine with CentOS/RedHat installed


## Dependencies

This playbook is based on some roles, which must be pulled in.

- [while-true-do.time](https://galaxy.ansible.com/while-true-do/time/)
- [while-true-do.chrony](https://galaxy.ansible.com/while-true-do/chrony/)
- [while-true-do.hostname](https://galaxy.ansible.com/while-true-do/hostname/)
- [while-true-do.yum](https://galaxy.ansible.com/while-true-do/yum/)


## Layout

The layout seems complicated in the beginning. Nevertheless it is mostly from the [Ansible Best Practices](http://docs.ansible.com/ansible/latest/playbooks_best_practices.html#directory-layout) Guide. Some adjustments were done.


```
README.md                 # The file you are currently reading.
LICENSE.md                # This file contains the license.

.editorconfig             # You should consider to use a plugin for editorconfig.
.gitignore                # A file containing stuff, which is not pushed to git.

all.yml                   # There can be an all.yml or site.yml to integrate other.
group1.yml                # Additional plays should be specified per inventory
group2.yml                # group. So, you can trigger all or a group, only.

data/
  file01                  # Here we put files, which may be used in playbooks.
  file02                  # You can think of stuff like public_keys for users.

docs/
  doc01                   # Here you can find documents like our CONTRIBUTING.md.
  doc02                   # Other docs, which can help to maintain the plays are
  doc03                   # welcome, too.

group_vars/
  group1.yml              # Here you can assign variables to particular groups.
  group2.yml              # Groups are defined in your inventory.

host_vars/
  hostname1.yml           # If a host needs specific variables, put them here.
  hostname2.yml           # Hosts are defined in your inventory.

roles/
  role01/                 # Here you will find the roles, which are in use.
  role02/                 # You can install additional ones from ansible galaxy.

    LICENSE               # The LICENSE is a must-check.
    README.md             # And the README for a role must be checked, too.
    requirements.yml      # Sometimes, some other roles are required.
    .editorconfig         # Roles can contain their own editorconfig file.
    .gitignore            # Roles can have their own .gitignore.

    defaults/
      main.yml            # Default variables for the role, which can be overwritten.
    docs/
      document01          # Often you can find some more docs here for the role.
    files/
      file01              # Maybe some files are used in the "tasks"
    handlers/
      main.yml            # Everything which will be triggered via "notify".
    meta/
      main.yml            # A meta file, which is used in ansible galaxy
    tasks/
      main.yml            # Here you will find the tasks, which are in the role.
    templates/
      foo.j2              # Often Templates are needed for config files.
    tests/
      test01              # If you're lucky, the maintainer has prepared some tests.
    vars/
      main.yml            # Even more vars can be specified here. These will overwrite defaults
```

## Usage

Using the example is quite easy. You just need to follow the below steps.

### Install Roles

First you need to install the needed roles from [Ansible Galaxy](galaxy.ansible.com/while-true-do/).

```
# Install into the roles path
ansible-galaxy install -p ./roles/ -r requirements.yml

# Or, if you want to use the default roles path
ansible-galaxy install -r requirements.yml
```

You will see, that there are only 3 requirements defined, but ansible-galaxy will install 4 roles. This is due to dependencies. You should read the `meta/main.yml` or `README.md` to find out, if a role has some dependencies and requirements.

### Edit the inventory to your needs

The exhaustive inventory documentation can be found [here](http://docs.ansible.com/ansible/latest/intro_inventory.html).

```
vi inventory/myInventory
```

A minimal example can look like:

```
[servers]
server01
server02
```

or, if you want to be more explicit

```
[servers]
server01 ansible_host=192.168.0.202 ansible_port=22
server02 ansible_host=192.168.0.203 ansible_port=2020
```

### Test the inventory

```
ansbible -m setup -i inventory/myInventory
```

### Call the playbook with your inventory file

For more documentation regarding playbooks, please have a look [here](http://docs.ansible.com/ansible/latest/playbooks.html)

```
ansible-playbook -i inventory/myInventory all.yml
```

The below parameters can be used:
- sudo password = "-K"
- login password = "-k"

```
ansible-playbook -k -K -i inventory/myInventory all.yml
```

### Next steps

You should consider to have a look at the creation of roles. You can find our community skeleton [here](https://github.com/while-true-do/ansible-galaxy-skeleton).

## Contribute / Bugs

Thank you so much for considering to contribute. Every contribution helps us.
We are really happy, when somebody is joining the hard work. Please have a look
at the links first.

-   [Contribution Guidelines](./docs/CONTRIBUTING.md)
-   [Create an issue or Request](https://github.com/while-true-do/ansible-playbook-example/issues)
-   [See who was contributing already](https://github.com/while-true-do/ansible-playbook-example/graphs/contributors)

## License

This work is licensed under a [BSD License](https://opensource.org/licenses/BSD-3-Clause).

## Author Information

Blog: [blog.while-true-do.org](https://blog.while-true-do.org)

Mail: [hello@while-true-do.org](mailto:hello@while-true-do.org)
