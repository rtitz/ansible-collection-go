# Ansible Collection - local.go

Installs and configures the Go Programming Language ([https://go.dev/](https://go.dev/)) on Linux and macOS systems with full cross-platform architecture support (x86_64, aarch64/arm64, i386, armv6l, armv7l).

## Requirements

* **Ansible Core:** 2.12 or higher
* **Target Systems:**
  * **macOS:** macOS 11+ (Intel & Apple Silicon) (**brew install gnu-tar** maybe required for macOS!)
  * **Linux:** Debian, Ubuntu, RHEL, CentOS, Fedora, Arch, Raspberry Pi OS

## Features

* **Cross-Platform:** Automatically detects OS and CPU architecture to download the matching Go binary.
* **Idempotent:** Safe to run repeatedly; cleans up stale builds and verifies full executable integrity.
* **macOS Fixes:** Automatically strips macOS Gatekeeper quarantine flags (com.apple.quarantine) and heals root-owned Go build cache permissions (~/Library/Caches/go-build).
* **Environment Setup:** Configures GOPATH and updates PATH persistently across system reboots.

## Configuration

* **Default Version & URLs:** Defined in roles/install_go/defaults/main.yml.
* **Custom Overrides:** Override default variables in test/group_vars/all/vars.yml or directly within your playbook.
* **Inventory:** Customize test/inventory to target localhost (local Mac setup) or remote Linux servers.

## Quick Start

### 1. Install Collection Dependencies
```
ansible-galaxy collection install -r requirements.yml --force
```

### 2. Execute the Playbook
```
ansible-playbook -i test/inventory test/main.yml -K
```

> **Note:** The -K (--ask-become-pass) flag prompts for your local sudo password. This is required for installing Go to /usr/local/go on Linux systems.

### 3. Apply Shell Environment
No reboot is required. To start using go in your current terminal session, reload your shell configuration:

* **macOS (Zsh):**
  source ~/.zshrc

* **Linux (Bash/Zsh):**
  source /etc/profile

### Quick Start (One-Liner)

To install dependencies and run the setup in a single step:
```
ansible-galaxy collection install -r requirements.yml --force && ansible-playbook -i test/inventory test/main.yml -K
```
## Verification

To confirm that Go has been successfully installed and configured, run:
```
go version
go env GOROOT GOPATH
```

## Directory Structure Overview
```
.
├── LICENSE
├── README.md
├── ansible.cfg
├── galaxy.yml
├── meta
│   └── runtime.yml
├── plugins
│   └── README.md
├── requirements.yml
├── roles
│   └── install_go
│       ├── README.md
│       ├── defaults
│       │   └── main.yml
│       └── tasks
│           ├── go_linux.yml
│           ├── go_macos.yml
│           └── main.yml
└── test
    ├── group_vars
    │   └── all
    │       └── vars.yml
    ├── inventory
    └── main.yml
```

## Author Information

Created and maintained for modular Go environment automation.  
For further details on Ansible collections, visit the Ansible Documentation ([https://docs.ansible.com/](https://docs.ansible.com/)).