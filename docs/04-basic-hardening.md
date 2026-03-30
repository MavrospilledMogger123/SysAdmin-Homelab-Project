## Basic Hardening/Security

### Goal

Ensure basic security via deactivating PermitRootLogin, deactivating passwordauthentication, activating usePAM as well as pubkeyauthentication, installing/configuring fail2ban and enabling ufw with change of rules

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
- Find [sshd] and write 'enabled = true', 'maxretry = 5', 'findtime = 10m', 'bantime = 1h'
- Restart to use configuration via 'sudo systemctl restart fail2ban'
- Check status of jails 'sudo fail2ban-client status'
- Check SSH jail 'sudo fail2ban-client status sshd'

#### Logs Monitoring

- Check ssh static logs via 'sudo journalctl -u ssh'
- Check ssh live logs via 'sudo journalctl -u ssh -f'
- Check finite amount of static logs 'sudo journalctl -u ssh -n x (-f for continuing live logs)'
- Same process for fail2ban logs

## Verification

- Verify if SSH key works without password prompt
- Verify if fail2ban monitors SSH
- Verify if journalctl ssh outputs SSH logs


This concludes the basic server setup.
