Ansible Nagios NRPE Role
========================

This [Ansible](http://www.ansible.com/home) role supports the deployment and configuration of the Nagios NRPE agent.

## Table of Contents

* [Supported Platforms](#supported-platforms)
* [User Manual](#user-manual)
  * [Basic usage](#basic-usage)
* [Configuration](#configuration)
  * [Configurable variables](#configurable-variables)

## Supported Platforms

See [meta info](meta/main.yml).

## User Manual

### Basic usage

* Configure this role as ansible-galaxy dependency (e.g. requirements.yml)
* Add the following line to your Ansible playbook's role section (sample):
```
roles:
  - role: "ansible-nagios-nrpe"
```

## Configuration

### Configurable variables

See [defaults](defaults/main.yml).
