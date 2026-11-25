# Cisco IOS configs

Baseline configs I reuse for Cisco switches and routers. They match the gear I work with, Cisco 2960 and 3850 series switches and 1900 and 4300 series routers. Paste them in global config mode and change the interface names and addresses to match your own setup. Test every change in a lab first, and take a backup before you touch a live device.

## Files

- switch-baseline.txt - VLANs, trunk and access ports, management VLAN, and a default gateway for a Layer 2 access switch
- router-baseline.txt - WAN and LAN interfaces, NAT direction, and a default route for an edge router
- port-security.txt - port security on access ports, sticky MAC addresses, and unused ports shut down
- stp-etherchannel.txt - rapid STP with a root bridge, and an LACP EtherChannel to the core
- acl-nat.txt - standard and extended ACLs, and NAT overload for inside hosts
- dhcp.txt - two DHCP pools with excluded addresses, default routers, and DNS servers
- ios-backup-restore.txt - how to back up and restore IOS config files with TFTP

## How to use a config

1. Open the file and read the description lines first
2. Change interface names like GigabitEthernet0/0 to match your device
3. Change addresses like 192.168.10.0 to match your own subnets
4. Paste the file into global config mode, a few lines at a time, and watch for errors
5. Run copy running-config startup-config when you are happy with the result

## Notes

- Interface names here follow GNS3 IOSvL2 and IOSv naming. A real 2960 numbers its ports differently, so check show ip interface brief on your own switch first
- Port security needs the port in access mode before you turn it on
- The ACL file blocks Telnet and SMB from outside, then permits everything else, so read it before you apply it on a live edge router
- The DHCP pools hand out 7 day leases
