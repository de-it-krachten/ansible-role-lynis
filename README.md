[![CI](https://github.com/de-it-krachten/ansible-role-lynis/workflows/CI/badge.svg?event=push)](https://github.com/de-it-krachten/ansible-role-lynis/actions?query=workflow%3ACI)


# ansible-role-lynis

Installs lynis om a variety of platforms
https://cisofy.com 



## Dependencies

#### Roles
None

#### Collections
- community.general

## Platforms

Supported platforms

- Red Hat Enterprise Linux 7<sup>1</sup>
- Red Hat Enterprise Linux 8<sup>1</sup>
- Red Hat Enterprise Linux 9<sup>1</sup>
- CentOS 7
- RockyLinux 8
- RockyLinux 9
- OracleLinux 8
- OracleLinux 9
- AlmaLinux 8
- AlmaLinux 9
- Debian 10 (Buster)
- Debian 11 (Bullseye)
- Ubuntu 18.04 LTS
- Ubuntu 20.04 LTS
- Ubuntu 22.04 LTS
- Fedora 35
- Fedora 36

Note:
<sup>1</sup> : no automated testing is performed on these platforms

## Role Variables
### defaults/main.yml
<pre><code>
# Lynis version to be installed
lynis_version: 'latest'

# Should lynis be executed
lynis_execute: false

# root directory where to install the software
lynis_root: /usr/local

# Github API & download urls
lynis_api: https://api.github.com/repos/CISOfy/lynis
lynis_repo: https://github.com/CISOfy/lynis
lynis_url: "{{ lynis_repo }}/archive/refs/tags/{{ lynis_version }}.tar.gz"
</pre></code>




## Example Playbook
### molecule/default/converge.yml
<pre><code>
- name: sample playbook for role 'lynis'
  hosts: all
  become: "yes"
  tasks:
    - name: Include role 'lynis'
      ansible.builtin.include_role:
        name: lynis
</pre></code>
