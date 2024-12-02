# Ansible Collection - local.go

  * This installs the [Go Language](https://go.dev/) tools on Linux and macOS systems

## General information
  * In 'roles/install_go/defaults/main.yml' you can specify the Go version you would like to download and install (See: [Go versions](https://go.dev/dl/))
  * In 'test/group_vars/all/vars.yml' you can overwrite variables set in 'roles/install_go/defaults/main.yml'
  * Adjust the 'test/inventory' file to your needs.

### Run the Ansible playbook:
```zsh
ansible-galaxy install -r requirements.yml && ansible-playbook -i test/inventory test/main.yml -K
```
  * Ansible will ask for the 'BECOME password', this is your sudo password
  * After the installation a reboot is needed, to ensure that the new environment variables are loaded correctly

See: [Ansible documentation](https://docs.ansible.com/)
