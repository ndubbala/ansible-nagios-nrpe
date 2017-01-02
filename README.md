Ansible Nagios NRPE Role
========================

This [Ansible](http://www.ansible.com/home) role supports the deployment and configuration of the Nagios NRPE agent where the agent will be built from source.

## Table of Contents

* [Supported Platforms](#supported-platforms)
* [User Manual](#user-manual)
  * [Basic usage](#basic-usage)
  * [Alternative source download location](#alternative-source-download-location)
  * [NRPE version management](#nrpe-version-management)
* [Configuration](#configuration)
  * [Configurable variables](#configurable-variables)

## Supported Platforms

See [meta info](meta/main.yml).

## User Manual

### Basic usage

* Configure this role as ansible-galaxy dependency (e.g. requirements.yml)
* Add the following lines to your Ansible playbook's role section (sample):
```
roles:
  - role: "ansible-nagios-nrpe"
    ansible_nagios_nrpe_version: "3.0.1"
    ansible_nagios_nrpe_source_hosts: "localhost,nagios-server.example.com"
```
* This will instruct the role to install the Nagios NRPE agent and configure the source hosts being allowed to connect to the agent
* Please note: The command argument feature (dont_blame_nrpe) is being enabled automatically by this role on install

### Alternative source download location

* By default, this role will try to download the needed NRPE sources from the official [Nagios Github repo](https://github.com/NagiosEnterprises/nrpe)
* In case you need to provide the sources on an internal repo server, this is doable by simply overriding the following variable:
```
roles:
  - role: "ansible-nagios-nrpe"
    ansible_nagios_nrpe_version: "3.0.1"
    ansible_nagios_nrpe_download_url: "https://repo.example.com/path/to/nrpe/sources"
```
* Where the implementation will expect the download file to be in the following format:
```
https://repo.example.com/path/to/nrpe/sources/nrpe-{{ ansible_nagios_nrpe_version }}.tar.gz
```

### NRPE version management

* Being executed for the first time, this role will create a self managed version file on each target host:
```
{{ ansible_nagios_nrpe_nagios_path }}/nagios-nrpe.version
```
* Next time the role will be executed, the currently installed version will be fetched and compared against the value being defined by the variable {{ ansible_nagios_nrpe_version }}
* In case of a mismatch, the role will try to install the version as defined by the variable {{ ansible_nagios_nrpe_version }}

## Configuration

### Configurable variables

See [defaults](defaults/main.yml).
