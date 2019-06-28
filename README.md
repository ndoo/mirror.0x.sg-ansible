# mirror.0x.sg Ansible Playbooks

A collection of Ansible playbooks used for boring administrative tasks on the bare metal serving mirror.0x.sg.

## prep-hosts.yml

The main playbook used for initial host configuration:

1. Sets timezone to Asia/Singapore
2. Ensures the IPMI watchdog is initialized
3. Set Ceph OSD hosts to power efficient CPU tuning and lock to lowest supported frequency (for power savings)

Todo: Consolidate jumbo frame playbook into OSD host tasks (once it has been refactored to skip hosts that are already running at jumbo MTU, to avoid network disruption)

## ceph-osd-jumbo-frames.yml

Sets active connection to MTU 9000; presently only supports setting the first active connection. Needs refactoring.

## ceph-dashboard-firewalld.yml

Accepts port 8080/tcp on Ceph mgr hosts, to allow Ceph dashboard viewing.

## supermicro-fans.yml

Overrides BMC fan control and sets a fixed fan speed to reduce noise.
