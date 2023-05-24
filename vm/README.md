# Virtual machine best practices

## Sizing

### Docker hosts

To create a host running docker, we use the following minimum specifications

- Debian stable O/S
- 4 vCPUs (host type)
- 2 GiB RAM (balloon to 8 GiB)
- 32 GiB VirtIO storage on redundant
- Display SPICE
- Only connected to specific VLAN for isolation
- Add qemu agent
