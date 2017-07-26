# network-manager-l2tp

[![Build Status](https://travis-ci.org/Temelio/ansible-role-network-manager-l2tp.svg?branch=master)](https://travis-ci.org/Temelio/ansible-role-network-manager-l2tp)

Install network-manager-l2tp package.

## Requirements

This role requires Ansible 2.1 or higher,
and platform requirements are listed in the metadata file.

## Testing

This role use [Molecule](https://github.com/metacloud/molecule/) to run tests.

Locally, you can run tests on Docker (default driver) or Vagrant.
Travis run tests using Docker driver only.

Currently, tests are done on:
- Ubuntu Trusty
- Ubuntu Xenial

and use:
- Ansible 2.1.x
- Ansible 2.2.x
- Ansible 2.3.x

### Running tests

#### Using Docker driver

```
$ tox
```

#### Using Vagrant driver

```
$ MOLECULE_DRIVER=vagrant tox
```

## Role Variables

### Default role variables

``` yaml
# Installation mode
nm_l2tp_install_from_repository: "{{ _nm_l2tp_install_from_repository }}"

# Repository management
nm_l2tp_apt_cache_valid_time: 3600
nm_l2tp_repositories: "{{ _nm_l2tp_repositories }}"

# Packages
nm_l2tp_packages: "{{ _nm_l2tp_packages }}"
nm_l2tp_system_dependencies: "{{ _nm_l2tp_system_dependencies }}"
```

### Ubuntu distributions variables

``` yaml
# Installation mode
_nm_l2tp_install_from_repository: True

# Repository management
_nm_l2tp_repositories:
  - repo: 'ppa:nm-l2tp/network-manager-l2tp'
    filename: 'network-manager-l2tp'

# Packages
_nm_l2tp_packages:
  - name: 'network-manager-l2tp'
  - name: 'network-manager-l2tp-gnome'
_nm_l2tp_system_dependencies:
  - name: 'ca-certificates'
```

## Dependencies

None

## Example Playbook

``` yaml
- hosts: servers
  roles:
    - { role: Temelio.network-manager-l2tp }
```

## License

MIT

## Author Information

Alexandre Chaussier (for Temelio company)
- http://www.temelio.com
- alexandre.chaussier [at] temelio.com
