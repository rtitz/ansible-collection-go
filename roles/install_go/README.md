# Go Language installation via Ansible playbook

  * This installs the [Go Language](https://go.dev/) tools on Linux and macOS systems

## General information
  * In 'group_vars/all/vars.yml' you can specify the Go version you would like to download and install (See: [Go versions](https://go.dev/dl/))
  * Adjust the 'inventory' file to your needs.

### Run the Ansible playbook:
```zsh
ansible-playbook -i inventory main.yml -K 
```
  * Ansible will ask for the 'BECOME password', this is your sudo password
  * After the installation a reboot is needed, to ensure that the new environment variables are loaded correctly

See: [Ansible documentation](https://docs.ansible.com/)
