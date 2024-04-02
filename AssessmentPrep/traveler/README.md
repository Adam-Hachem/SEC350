# TRAVELER

## Set adapters
| INTERFACE | NETWORK | ADDRESS         |
|-----------|---------|-----------------|
| 1         | WAN     | 10.0.17.24      |

## Named user account, network config, computer name
```bash
net user /add adam [password]
net localgroup administrators adam /add
ncpa.cpl
sysdm.cpl
```
### Restart traveler
## Set up passwordless ssh
```
ssh-keygen
type C:\Users\adam\.ssh\id_rsa.pub | ssh adam@10.0.17.124 "cat >> key"
ssh 10.0.17.124
sudo -i
cat /home/adam/key >> /home/adam-jump/.ssh/authorized_keys
chown -R adam-jump:adam-jump /home/adam-jump/.ssh
chmod 600 /home/adam-jump/.ssh/authorized_keys
chmod 700 /home/adam-jump/.ssh
```
