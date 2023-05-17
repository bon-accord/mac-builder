# Mac Builder

## Summary

- This repo is designed as a self-contained set of Ansible playbooks and roles to let you manage your MacOS developer tooling
- It is intended to be run on a new or existing MacOS developer laptop
- It assumes the OS is installed and configured

## Prerequisites

- Optional: Install Apple command-line tools (takes a long time and lots of disk space): `xcode-select --install`
- Add Python3 & Homebrew to your path: `export PATH=“$HOME/Library/Python/3.8/bin:/opt/homebrew/bin:$PATH"`
- Upgrade pip: `sudo pip3 install --upgrade pip`
- Install Ansible: `pip3 install ansible`

Note that after upgrading to macOS Ventura, you may need to reinstall XCode CLI tools which can upgrade your Python version to 3.11. So, you may need to do the following:

``` bash
xcode-select --install          # Reinstall XCode CLI tools
vi ~/.zshrc                     # Remove Python 3.8 or older versions from your PATH in .zshrc or similar
sudo pip3 install --upgrade pip # Upgrade pip
pip3 install ansible            # Reinstall Ansible
```

## Setup

The following setup tasks should be performed or borne in mind before running the playbook(s):

- Ansible Vault should be used to create and encrypt the following file: `ansible/group_vars/all/vault.yml`
- The Ansible Vault password should be stored in `~/.vaultpass.txt` or similar
- The structure of `vault.yml` is shown below:

``` yaml
# Local sudo
vault_sudo_passwd: <sudo passwd on your laptop>
vault_ansible_become_pass: <sudo passwd on your laptop>

# Git
vault_git_username: <your Git username>
vault_git_useremail: <your Git email address>

# Mac App Store
vault_mas_email: <Apple ID email used for Mac App Store>
vault_mas_password: <Apple ID password used for Mac App Store>

# Folders to Create Under $HOME
vault_dirs_under_homedir:
  - bin

# Folders to Create Under ~/Documents
vault_dirs_under_documents:
  - tmpdocs
```

## How to Use

- Clone this repo
- Change into ansible dir: `cd ansible`
- Run the playbook: `ansible-playbook --vault-password-file ~/.vaultpass.txt install.yml`

If you want to run only certain roles, use tags:

- `ansible-playbook --vault-password-file ~/.vaultpass.txt install.yml --tags "homebrew"`
- `ansible-playbook --vault-password-file ~/.vaultpass.txt install.yml --tags "shell"`

## Manual Tasks Not Automated

The following tasks are not automated and still need to be done manually:

### Chrome Extensions

Chrome extensions: [see here](https://developer.chrome.com/docs/extensions/mv3/external_extensions/).
For reasons of simplicity and maintenance, this is better done manually.

### MacOS Preference Settings

Coming soon hopefully!

## References

- Big thanks for inspiration to [@geerlingguy](https://github.com/geerlingguy)