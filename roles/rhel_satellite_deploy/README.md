# Ansible Role: rhel_satellite_deploy

This Ansible role automates the complete installation and configuration of Red Hat Satellite.

## **WARNING - PREREQUISITES**

**MANDATORY:** RHEL must be at the latest patch level before installation

## Description

The `rhel_satellite_deploy` role performs a complete installation and configuration of Red Hat Satellite by automating all necessary steps:

- Satellite server installation
- Post-installation configuration with products and repositories
- Lifecycle environment creation
- Content views configuration
- Activation keys management

## Features

### Global Installation

- System prerequisites verification (RHEL 9)
- RHSM subscription management
- Satellite package installation
- Configuration with performance profiles

### Post-Installation Configuration

- HTTP proxy configuration
- Manifest import and management
- Products and repositories configuration
- Repository synchronization
- Lifecycle environment creation
- Content views management
- Content views publication and promotion
- Activation keys configuration

## Variables

- Satellite : roles/rhel_satellite_deploy/defaults/main.yml

## Prerequisites

### System

- RHEL 9.x
- x86_64 Architecture
- Root privileges

### Minimum Resources

- RAM    : 16 GB minimum (depending on chosen profile)
- CPU    : 8 cores minimum
- Disk   : 20 GB minimum for `/var` (5GB sufficient during installation)
- Disk   : 5 GB minimum for `/usr`

### Network

- Access to Red Hat Subscription Management
- Access to corporate proxy if configured
- Open ports: 80, 443, 5647, 8140, 8443, 9090

## Usage

- See the rhel_satellite_deploy.yml playbook

## Dependencies

### Collections

- `community.general`
- `redhat.satellite`
- `redhat.satellite_operations`

## Author

**dapiced Team** - Development, maintenance and documentation

## License

MIT

## Support

- dapiced Team
- Red Hat Customer Portal for Satellite
