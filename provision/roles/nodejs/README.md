# Node.js role for Ansible

Installs either a specific version of NodeJS specified, or it will default version 5.x.

## Requirements

Tested on Ubuntu 12.04 Server.

## Role Variables

The default variables are as follows:

    nodejs_do_bower_install: false
    nodejs_update_npm: false
    nodejs_global_packages: []
    nodejs_user: '{{ ansible_ssh_user }}'
    nodejs_major_version: 0
    nodejs_minor_version: 10

## Example Playbook

    - hosts: 'servers'
      roles:
        - role: 'ssilab.nodejs'
          nodejs_update_npm: true               # If true, install the latest npm immediately after installing Node.js
          nodejs_major_version: 0
          nodejs_minor_version: 12              # Installs version 0.12.*
          nodejs_user: 'hercules'
          nodejs_global_packages:
          	- 'bower'
          	- 'forever'
          	- 'gulp'
          	- 'nodemon'
          nodejs_app_root: '/path/to/my/app'    # If defined, 'npm install' will be run here
          nodejs_do_bower_install: true         # If true and nodejs_app_home is defined, 'bower install' will be run

# Supported NodeJS versions

| NodeJS Version | `nodejs_major_version` | `nodejs_minor_version` |
| -------------- | ---------------------- | ---------------------- |
| 5.x            | 5                      | 'x'                    |
| 4.x            | 4                      | 'x'                    |
| 0.12           | 0                      | 12                     |
| 0.10           | 0                      | 10                     |

More information on the different supported version can be found on this [Github repo](https://github.com/nodesource/distributions).

# License

This playbook is provided 'as-is' under the conditions of the BSD license. No fitness for purpose is guaranteed or implied.
