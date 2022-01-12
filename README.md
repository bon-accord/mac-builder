# Mac Dev Tools

## Summary

- This repo is designed as a self-contained set of Ansible playbooks and roles to let you manage your MacOS developer tooling
- It is intended to be run on a new or existing MacOS developer laptop
- It assumes the OS is installed and configured

## Prerequisites

- Install Apple command-line tools (optional): `xcode-select --install`
- Add Python3 & Homebrew to your path: `export PATH=“$HOME/Library/Python/3.8/bin:/opt/homebrew/bin:$PATH"`
- Upgrade pip: `sudo pip3 install --upgrade pip`
- Install Ansible: `pip3 install ansible`

## Setup

The following setup tasks should be performed or borne in mind before running the playbook(s):

- Ansible Vault should be used to create and encrypt the following file: `ansible/group_vars/all/vault.yml`
- 

## How to Use

- Clone this repo
- Change into ansible dir: `cd ansible`
- Run the playbook: `ansible-playbook --vault-password-file ~/.vaultpass.txt install.yml`

## References

- Big thanks to 