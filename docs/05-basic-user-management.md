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

- Use method

```type ~\.ssh\(userfolder)\(userkey).pub | ssh (chosen username)@(ip address) "mkdir -p ~/.ssh && cat >> ~/.ssh/authorized_keys"```

from original host to transfer pubkey for new user

- Configure ssh for user in /etc/ssh via

```sudo nano sshd_config```

and set PasswordAuthentication to 'no', set usePAM to 'yes and set PubKeyAuthentication to 'yes'

- Restart ssh via

```sudo systemctl restart ssh```

- Add the new ssh user config to config file of original host
! Add ssh config inside the file itself, do not copy original file

### Verification

- Verify if new user is able to connect without password


