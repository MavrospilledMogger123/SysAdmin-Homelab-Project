## Basic Hardening/Security

### Goal

Ensure basic security via deactivating PermitRootLogin, deactivating passwordauthentication, activating usePAM as well as pubkeyauthentication, installing/configuring fail2ban and enabling ufw with change of rules.

### SSH Hardening

#### Setup

- Configure sshd via 'sudo nano /etc/ssh/sshd_config
- Switch PasswordAuthentication and PermitRootLogin to 'no'
- Switch (if not enabled) usePAM to yes
- Switch (if not enabled) pubkeyauthentication to yes
- Install fail2ban via 'sudo apt update && sudo apt install fail2ban -y'
- Enable via 'sudo systemctl enable fail2ban' and start via 'sudo systemctl start fail2ban'
- Check for status via 'sudo systemctl status fail2ban'

#### Configuration of Fail2Ban

- Copy default file of jail.conf to custom file via 'sudo cp /etc/fail2ban/jail.conf /etc/fail2ban/jail.local' !If not working outright, change directories until fail2ban
- Find [sshd] and configure

```ini
[sshd]
enabled = true
maxretry = 5
findtime = 10m
bantime = 1h
```

#### Logs Monitoring

- Check ssh static logs via 'sudo journalctl -u ssh'
- Check ssh live logs via 'sudo journalctl -u ssh -f'
- Check finite amount of static logs 'sudo journalctl -u ssh -n x (-f for continuing live logs)'
- Same process for fail2ban logs

### UFW Configuration

- Install ufw via 'sudo apt update && sudo apt install ufw'
- Change ruleset with 'sudo ufw default deny incoming && sudo ufw default allow outgoing'
- Ensure allowed connection via SSH with 'sudo ufw allow ssh'
- Check status via 'sudo ufw status verbose'
- If ssh allowed, enable with 'sudo ufw enable'
- Improve security against bruteforce with 'sudo ufw limit ssh'

## Verification

- Verify if SSH key works without password prompt
- Verify if fail2ban monitors SSH with 'sudo fail2ban-client status' and 'sudo fail2ban-client status sshd'
- Verify if journalctl ssh outputs SSH logs
- Verify ufw logs with 'journalctl -u ufw -f'

