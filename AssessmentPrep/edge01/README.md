# EDGE01

## Set adapters
| INTERFACE | NETWORK | ADDRESS (later) |
|-----------|---------|-----------------|
| 1         | WAN     | 10.0.17.124/24  |
| 2         | DMZ     | 172.16.50.2/29  |
| 3         | LAN     | 172.16.150.2/24 |

### Make sure you are in configure mode

## Restore internet and SSH 
```
set interfaces ethernet eth2 address '172.16.150.2/24'
set interfaces ethernet eth0 address '10.0.17.124/24'
set nat source rule 11 description 'NAT FROM LAN to WAN'
set nat source rule 11 outbound-interface 'eth0'
set nat source rule 11 source address '172.16.150.0/24'
set nat source rule 11 translation address 'masquerade'
set protocols static route 0.0.0.0/0 next-hop 10.0.17.2
set service dns forwarding allow-from '172.16.150.0/24'
set service dns forwarding listen-address '172.16.150.2'
set service dns forwarding system
set system name-server '10.0.17.2'
set service ssh listen-address '0.0.0.0'

```
### Paste the rest from [config file in this repo](https://github.com/Adam-Hachem/SEC350/blob/main/AssessmentPrep/edge01/config) over SSH. VMWare clipboard size is limited.

### This should be all for setup
