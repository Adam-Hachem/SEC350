# DHCP01

## Set adapters
| INTERFACE | NETWORK | ADDRESS         |
|-----------|---------|-----------------|
| 1         | LAN     | 172.16.150.99   |

## Set up internet and SSH
`sudo nano /etc/netplan/00-intstaller-config.yaml`
### Paste from [matching file in this repo](https://github.com/Adam-Hachem/SEC350/blob/main/AssessmentPrep/dhcp/etc/netplan/00-installer-config.yaml)
```
sudo netplan apply
sudo hostname dhcp01-adam
sudo useradd adam -m -G sudo -s /bin/bash
sudo passwd adam
```
### Continue on mgmt01, use `ssh-copy-id` to move key, you may have to remove the old host key.
## isc-dhcp-server configuration
```
sudo apt update
sudo apt install isc-dhcp-server
sudo nano /etc/dhcp/dhcpd.conf
```
### Add all contents of the [matching file in this repo](https://github.com/Adam-Hachem/SEC350/blob/main/AssessmentPrep/dhcp/etc/dhcp/dhcpd.conf) to the file
```
sudo systemctl enable --now isc-dhcp-server
sudo systemctl status isc-dhcp-server
```
## Wazuh instructions
In the Wazuh GUI, click the dropdown arrow next to the big logo. Navigate to `Agent > Deploy new agent`.

You will need to choose OS type, architecture, the wazuh server address(172.16.200.10), the name of the agent, and the desired group(linux, ubuntu=os, x86_64).

You will get a one-liner command generated to automatically install/set up the agent. If the agent doesn't have internet access, just do the wget half on a different machine and use scp to send the binary to the agent, execute the second half of the command (to install the package) there.

### Now on dhcp01, run:
```
sudo systemctl daemon-reload
sudo systemctl enable --now wazuh-agent
```
