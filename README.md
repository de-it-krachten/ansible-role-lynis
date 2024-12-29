[![CI](https://github.com/de-it-krachten/ansible-role-lynis/workflows/CI/badge.svg?event=push)](https://github.com/de-it-krachten/ansible-role-lynis/actions?query=workflow%3ACI)


# ansible-role-lynis

Installs lynis om a variety of platforms
https://cisofy.com 



## Dependencies

#### Roles
- deitkrachten.cron

#### Collections
None

## Platforms

Supported platforms

- Red Hat Enterprise Linux 8<sup>1</sup>
- Red Hat Enterprise Linux 9<sup>1</sup>
- RockyLinux 8
- RockyLinux 9
- OracleLinux 8
- OracleLinux 9
- AlmaLinux 8
- AlmaLinux 9
- SUSE Linux Enterprise 15<sup>1</sup>
- openSUSE Leap 15
- Debian 11 (Bullseye)
- Debian 12 (Bookworm)
- Ubuntu 20.04 LTS
- Ubuntu 22.04 LTS
- Ubuntu 24.04 LTS
- Fedora 40
- Fedora 41

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

# Wrapper script
lynis_wrapper_script: /usr/local/bin/lynis.sh

# Execute lynis immediately
lynis_immediate: false

# Lynis schedule defaults
lynis_execution_user: root
lynis_execution_group: root
lynis_schedule: false
lynis_schedule_command: "{{ lynis_wrapper_script }}"
lynis_schedule_times:
  weekday: '*'
  hour: '02'
  minute: '00'

# Location for centralized output
lynis_central_path: /var/log/lynis_central

# Lynix log file
lynis_log: "/var/log/lynis.log"

# Lynis html report
lynis_html: "/var/log/lynis.html"
</pre></code>




## Example Playbook
### molecule/default/converge.yml
<pre><code>
- name: sample playbook for role 'lynis'
  hosts: all
  become: 'yes'
  vars:
    lynis_execute: true
  tasks:
    - name: Include role 'lynis'
      ansible.builtin.include_role:
        name: lynis
</pre></code>
