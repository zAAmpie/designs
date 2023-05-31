# Hostnames

## Hostname allocation and naming best practices

When naming hosts, the convention is to name them by type or function (if possible), e.g.

Networking equipment by type
- `rtr` - router
- `swt` - switch
- `mod` - modem
- `fwl` - firewall
- `wap` - wireless access point

Servers by function (unless they have an apparent type):
- `dns` - DNS server
- `vmm` - virtual machine manager (proxmox)
- `app` - application server
- `prx` - proxy/load balancer
- `nas` - storage
- `web` - web server
- `mon` - monitoring
- `lap` - laptop
- `dsk` - desktop
- `sen` - sensor
- `tab` - tablet
- `cel` - cellphone/smartphone

Add suffix of `00` padded number.

Examples:
- `rtr01.mgmt.drsam.cc`, `nas01.trust.drsam.cc`, `dsk01.trust.drsam.cc`, `app02.insec.drsam.cc`
