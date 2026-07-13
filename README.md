# Ansible Role: virtualbox

[![CI](https://github.com/pluggero/ansible-role-virtualbox/actions/workflows/ci.yml/badge.svg)](https://github.com/pluggero/ansible-role-virtualbox/actions/workflows/ci.yml) [![Ansible Galaxy downloads](https://img.shields.io/ansible/role/d/pluggero/virtualbox?label=Galaxy%20downloads&logo=ansible&color=%23096598)](https://galaxy.ansible.com/ui/standalone/roles/pluggero/virtualbox)

An Ansible Role that installs a basic configuration of virtualbox.

## Requirements

None.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

```yaml
virtualbox_version: "x.x"
```

The version of virtualbox to install can be defined in the variable `virtualbox_version`.

```yaml
virtualbox_install_method: "dynamic"
```

The method used to install virtualbox can be defined in the variable `virtualbox_install_method`.
The following methods are available:

- `source`: Installs virtualbox from source
- `package`: Installs virtualbox from the package manager of the distribution
  - **NOTE**: This method installs the latest version available in the package manager and not the version defined in `virtualbox_version`.
- `dynamic`: Installs virtualbox from package manager if available in the correct version, otherwise installs from source

## Dependencies

None.

## Notes for Arch Linux

Arch ships several parallel-installable kernel variants (`linux`, `linux-lts`,
`linux-zen`, `linux-hardened`, ...), each with its own headers package (e.g.
`linux-lts-headers`). This role detects the kernel variant actually running on the
target host and installs the matching headers package automatically, so the
VirtualBox kernel module (`vboxhost`) can be built correctly by DKMS regardless of
which kernel variant is in use.

## Example Playbook

```yaml
- hosts: all
  roles:
    - pluggero.virtualbox
```

## License

MIT / BSD

## Author Information

This role was created in 2025 by Robin Plugge.
