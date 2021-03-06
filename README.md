# SAP S4HANA Deployment Demo
This repository is for demoing the deployment of an S4HANA SID using the Red Hat product portfolio, mainly Red Hat Enterprise Linux, Red Hat Ansible Automation Platform, Red Hat Satellite, and Red Hat Insights for Red Hat Enterprise Linux.

## Demo Personas

This demo is given through the lens of three different personas: an infrastructure administrator, an SAP BASIS administrator, and an SAP business analyst. Each persona has a corresponding login and appropriate permissions on Ansible controller.

## Demo Flow
1. Provision the appropriate number of Red Hat Enterprise Linux systems with the appropriate resources, pre-registered to Red Hat Satellite and Red Hat Insights for Red Hat Enterprise Linux
2. Do some base configuration of the systems
3. Prepare systems for SAP installation
4. Prepare HANA systems for SAP HANA installation
5. Install SAP HANA
6. Setup system replication between the SAP HANA systems
7. Install a pacemaker cluster and bring SAP HANA under cluster management
8. Prepare netweaver systems for S4 install
9. Install SAP/S4
10. Reinsate HSR

The automation will be driven by Red Hat Ansible Controller, with Red Hat Satellite doing the provisioning and content management.

## Requirements
- An instance of Red Hat Satellite with the appropriate content for SAP systems (RHEL8.2)
- An instance of Red Hat Ansible Controller where resources can be set up

## Definitions
In the SAP space, we have a few different terms that need to be defined. Note: not all of these are universally agreed upon, replace with what your organization prefers.

- sid: Three-digit unique identification code in a specific server
- cluster: A pair of SAP HANA servers acting as the database for a single sid or multiple sids
- environment: dev, QA, prod, etc. This corresponds to a lifecycle environment in Red Hat Satellite

## The Power of Ansible's Inventory
One of the main intentions of this demo is to highlight how powerful an ansible inventory can be, and how to integrate this with complex environments that need automation.

For this demo, Ansible Controller will be our source of truth, with an inventory containing host_vars and group_vars used to deploy SAP components.

## How to Run
Within the `provisoner` directory is a playbook for configuring Red Hat Ansible Controller, along with an example vars file. The playbooks run by Ansible Controller are located in the `playbooks` directory.

