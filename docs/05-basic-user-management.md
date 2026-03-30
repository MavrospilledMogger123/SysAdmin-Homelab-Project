## Basic User Management

### Goal
Add a second user with his own sudo rights, as well as transfer a SSH key to ensure access to the server.

### Setup

- Add a second user with 'sudo adduser (username)' and add password
- If needed, give user sudo rights with 'sudo usermod -aG sudo (username)'
- Switch to user via 'su (username)' and create directory for .ssh via 'mkdir ~/.ssh'
- Create file for pubkey via 'touch authorized_keys' while in directory '.ssh'
- 
