# Red Hat Satellite 6.XX - Deployment

Ansible automation for Red Hat Satellite and Capsule deployment and configuration on RHEL 9.

## **WARNING - PREREQUISITES**

**MANDATORY:** RHEL must be at the latest patch level before installation  

## Overview

This repository contains **2 specialized Ansible roles** and **2 playbooks** to fully automate:

- **rhel_satellite_deploy.yml => rhel_satellite_deploy** : Installation, configuration, content management and lifecycle environments
- **rhel_capsule_deploy.yml => rhel_capsule_deploy**      : Installation, registration, PKI certificate generation/transfer

### Architecture

```bash
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   SATELLITE     │────│   CONTROLLER    │────│    CAPSULE      │
│   (Central      │    │   (Ansible)     │    │    (Proxy)      │
│    Server)      │    │                 │    │                 │
└─────────────────┘    └─────────────────┘    └─────────────────┘
│ Content Management      | Automation           │ Content Proxy          
│ Lifecycle Environments  │ Certificate Mgmt     │ Client Registration    
│ Subscription Management │                      │ Repository Sync 
│                         │                      │ SSL capsule-satellite cert
```

---

## Repository Components

### Structure

```bash
rhel_satellite/
├── README.md                           # This file - Main documentation
├── rhel_satellite_deploy.yml           # Satellite deployment playbook
├── rhel_capsule_deploy.yml             # Capsule deployment playbook
├── collections/requirements.yml        # Required Ansible collections
├── roles/    
│   ├── rhel_satellite_deploy/          # Complete Satellite role
│   │   ├── README.md                   # Satellite role documentation
│   │   ├── defaults/main.yml           # Optimized variables (219 lines)
│   │   ├── tasks/main.yml              # Main entry point
│   │   ├── tasks/satellite_pre.yml     # System preparation
│   │   ├── tasks/satellite_install.yml # Installation
│   │   ├── tasks/satellite_config.yml  # Advanced configuration
│   │   ├── templates/rhsm.conf.j2      # Subscription manager template
│   │   └── meta/main.yml               # Galaxy metadata
│   └── rhel_capsule_deploy/            # Complete Capsule role
│       ├── README.md                   # Capsule role documentation
│       ├── defaults/main.yml           # Capsule variables
│       ├── tasks/main.yml              # Main entry point
│       ├── tasks/capsule_pre.yml       # System preparation
│       ├── tasks/capsule_install.yml   # Installation & registration
│       ├── tasks/capsule_config.yml    # Configuration & certificates
│       └── meta/main.yml               # Galaxy metadata
```

---

## Quick Usage

### 1. **Dependencies**

```bash
# Ansible Collections
  - community.general
  - redhat.satellite_operations
  - redhat.satellite
```

### 2. **Satellite Server Deployment Playbook**

```bash
# rhel_satellite_deploy.yml
```

### 3. **Capsule Server Deployment Playbook**

```bash
# rhel_capsule_deploy.yml
# variable:              
  # sat_server: "" # FQDN.   
```

### 4. **Minimum Recommended Resources for Capsule or Satellite Deployment**

```bash
# RAM    : 16 GB minimum (depending on chosen profile)
# CPU    : 8 cores minimum
# Disk   : 20 GB minimum for `/var` (5GB sufficient during installation)
# Disk   : 5 GB minimum for `/usr`
```

---

## Variables

- Capsule   : See roles/rhel_capsule_deploy/defaults/main.yml
- Satellite : See roles/rhel_satellite_deploy/defaults/main.yml

## Variables provided by the client for capsule deployment only

- Capsule : sat_server: "" `Satellite server FQDN`

---

## Detailed Documentation

- **[Satellite Role](roles/rhel_satellite_deploy/README.md)** - Satellite Deployment
- **[Capsule Role](roles/rhel_capsule_deploy/README.md)**     - Capsule Deployment

---

### **Support**

- **dapiced Team**                 : Development, maintenance and documentation
- **Red Hat Customer Portal**   : Product support

---
