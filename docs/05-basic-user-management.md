## Basic User Management

### Goal
Add a second user with his own sudo rights, as well as transfer a SSH key to ensure access to the server.

### Setup

- Add a second user with

```sudo adduser (username)```

- Add password
- If needed, give user sudo rights with

```sudo usermod -aG sudo (username)```

- Switch to user and create directory for .ssh via

```su (username) && mkdir ~/.ssh```

- Create file for pubkey while in directory ssh via

```touch authorized_keys```

- Use identical method
