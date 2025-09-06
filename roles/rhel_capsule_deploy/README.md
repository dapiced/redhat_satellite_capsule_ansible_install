# Ansible Role: rhel_satellite

This Ansible role automates the complete installation and configuration of Red Hat Capsule.

## **WARNING - PREREQUISITES**

**MANDATORY:** RHEL must be at the latest patch level before installation

## Description

The `rhel_capsule` role performs a complete installation and configuration of Red Hat Satellite by automating all necessary steps:

- Capsule server installation
- Post-installation configuration with products and repositories
- Registration and SSL Configuration

## Features

### Global Installation and Configuration

- System prerequisites verification (RHEL 9)
- RHSM subscription management
- Capsule package installation
- Registration and SSL Configuration

## Variables

- Capsule   : roles/rhel_capsule_deploy/defaults/main.yml

## Variables provided by the client for capsule deployment only

- Capsule : sat_server: ""

## Prerequisites

### System

- RHEL 9.x
- x86_64 Architecture
- Root privileges on target system

### Minimum Resources

- RAM    : 16 GB minimum (depending on chosen profile)
- CPU    : 8 cores minimum
- Disk   : 20 GB minimum for `/var` (5GB sufficient during installation)
- Disk   : 5 GB minimum for `/usr`

### Network

- Open ports: 80, 443, 5647, 8140, 8443, 9090

## Usage

- See the rhel_capsule_deploy.yml playbook

## Dependencies

### Collections

- `community.general`
- `redhat.satellite`
- `redhat.satellite_operations`

## Author

**ACME Team** - Development, maintenance and documentation

## License

MIT

## Support

- ACME
- Red Hat Customer Portal for Satellite
