## SSH

### Goal

Ensure quick and safe access to server

### SSH Key

- Create SSH key via 'ssh-keygen -t ed25519 -C user -f userkey'
- Transfer public key to server via

```type ~\.ssh\(userfolder)\(userkey).pub | ssh (chosen username)@(ip address) "mkdir -p ~/.ssh && cat >> ~/.ssh/authorized_keys"```

! Note difference in PowerShell and Bash synthax

- Create 'config' file on original host under the directory '~\.ssh'  ! Delete .txt suffix
- Enter the following:

Host (Chosen hostname)

    HostName (IP address)
    
    User (Chosen username)
    
    IdentityFile ~/.ssh/(userfolder)/(userkey)
    
! Center via 4 spaces each
