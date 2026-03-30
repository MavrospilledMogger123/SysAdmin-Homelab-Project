## Installation

### Goal
Ensure a clear and simple installation setup to support further configuration.

### Setup

- Boot VM after hardware setup
- Choose 'Try or Install Ubuntu server'
- Select preferred language
- Select preferred keyboard layout
- Base installation type 'Ubuntu server'
- Network config remains default
- Proxy adress remains empty
- Mirror adress remains default
- Choose 'Entire disk' and 'Set up disk as an LVM group' for storage config
- Storage config remains default
- Confirm destructive action
- 'Your name' is only cosmetic, no technical relevance

Server name: (chosen hostname)

User name: (chosen username)

Password: (chosen password)

- Skip Ubuntu Pro
- Install OpenSSH server for remote access after installation
- Server snaps remain empty, unless specified
- Reboot after installation completion
- Press enter to eject medium
- Login with password
- Update system with

```sudo apt update && sudo apt upgrade```
