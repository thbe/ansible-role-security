# Ansible Role thbe-security

[![Molecule](https://github.com/thbe/ansible-role-security/actions/workflows/molecule.yml/badge.svg)](https://github.com/thbe/ansible-role-security/actions/workflows/molecule.yml)

This role configures and deploys security settings and tools on an RHEL instance or RHEL clone.

## Requirements

This role does not have any requirements.

## Role Variables

* **role_directory** - This variable contains the root path of the directories used by thbe roles (**do not change!**)
* **password_quality_file** - This variable contains the password quality file (**do not change!**)
* **password_login_file** - This variable contains the login file (**do not change!**)
* **minlen** (default: 16)
* **lcredit** (default: -1)
* **ucredit** (default: -1)
* **dcredit** (default: -1)
* **ocredit** (default: -1)
* **pass_max_days** - Maximum days before password change is required (default: 365)
* **pass_min_days** - Minimum days before password could be changed (default: 0)
* **pass_min_len** - Minimum password length (default: 8)
* **pass_warn_age** - Days before warning that password will expire (default: 7)
* **remember** - Number of passwords to remember (default: 24)
* **lynis_enable** - Enable the installation of Lynis (default: false; requires EPEL)
* **rkhunter_enable** - Enable the installation of rkhunter (default: false; requires EPEL)

## Dependencies

This role depends on:

* thbe.common
* thbe.rhel

## Example Playbook

This role can be included in the site.yml like this:

```yaml
- name: Ansible playbooks for all nodes
  hosts: all
  collections:
    - ansible.posix
    - community.general
  gather_facts: true
  vars:
        external_repos_epel: true
        lynis_enable: true
        rkhunter_enable: true

  tasks:
    - name: Role Common
      ansible.builtin.include_role:
        name: thbe.common
    - name: Role rhel
      ansible.builtin.include_role:
        name: thbe.rhel
    - name: Role Security
      ansible.builtin.include_role:
        name: thbe.security
```

## License

GPL-3.0-only

## Author Information

Thomas Bendler - [https://www.thbe.org/](https://www.thbe.org/)
