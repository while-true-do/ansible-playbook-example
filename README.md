# Ansible Playbook: Example
| An example playbook to show the usage of while-true-do roles.

## Requirements

- You need ansible installed.
- You need at least one test machine with CentOS installed.

## Installation

git clone

## Examples

### Install the needed roles from <galaxy.ansible.com/while-true-do/>

```
# Install into the roles path
ansible-galaxy install -p ./roles/ -r requirements.yml
# Or, if you want to use the default roles path
ansible-galaxy install -r requirements.yml
```

### Edit the inventory to your needs

```
vi inventory/servers
```

A minimal example can look like:

```
[servers]
server1
server2
```

or

```
[servers]
192.168.0.202
192.168.0.203
```

### Call the playbook with you inventory file

```
ansible-playbook -i inventory/servers
```

If you are in the need of sudo add "-K" or for a password auth add "-k" like:

```
ansible-playbook -k -K -i inventory/servers
```

## License

This work is licensed under a [BSD License](https://opensource.org/licenses/BSD-3-Clause).

## Contribute / Bugs

**bug reports:** <https://github.com/while-true-do/ansible-playbook-example/issues>

**contributers:** <https://github.com/while-true-do/ansible-playbook-example/graphs/contributors>

## Author Information

**blog:** <https://blog.while-true-do.org>

**github:** <https://github.com/daniel-wtd>

**contact:** [mail@while-true-do.org](mailto:mail@while-true-do.org)

