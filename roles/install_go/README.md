# Ansible Role: install_go

An Ansible role to install and configure the Go Programming Language (https://go.dev/) on Linux and macOS systems with cross-platform architecture support.

## Requirements

* **Ansible Core:** 2.12 or higher
* **Target Systems:**
  * **macOS:** Intel (x86_64) & Apple Silicon (arm64)
  * **Linux:** Debian, Ubuntu, RHEL, CentOS, Fedora, Arch, Raspberry Pi OS (x86_64, aarch64, i386, armv6l, armv7l)

## Role Variables

Available variables are listed below, along with default values (see defaults/main.yml):

* **go_version:** "1.22.0"
  The version of Go to download and install.

* **go_install_dir_linux:** "/usr/local/go"
  Installation path for Linux systems (requires root/sudo access).

* **go_install_dir_macos:** "{{ ansible_env.HOME }}/Applications/go"
  Installation path for macOS systems (installed per user).

* **go_gopath:** "{{ ansible_env.HOME }}/go"
  The default GOPATH directory for Go workspace and binaries.

## Dependencies

None.

## Example Playbook

Including the role in your playbook:

```yml
- name: Install Go Programming Language
  hosts: all
  roles:
    - role: local.go.install_go
      vars:
        go_version: "1.22.1"
```

## Author Information

Created for modular Go environment automation.