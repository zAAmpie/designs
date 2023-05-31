# IP

## Allocated ranges per network

Supernet allocation

- `10.0.0.0/8` - LAN IPs
- `192.168.0.0/16` - WAN/DMZ IPs
- `172.16.0.0/12` - PtP interface IPs or virtual/overlay networks

Each network subdomain has its own /16 network range. Refer to VLAN allocation for description per network.

- `10.10.0.0/16` - trusted.drsam.cc
- `10.11.0.0/16` - insec.drsam.cc
- `10.30.0.0/16` - lab.drsam.cc
- `10.40.0.0/16` - iot.drsam.cc
- `10.41.0.0/16` - not.drsam.cc
- `10.50.0.0/16` - cam.drsam.cc
- `10.99.0.0/16` - mgmt.drsam.cc

If you're allocating IPs to the same host in multiple network, use the same IP allocation in the different subnets, e.g. assign `10.10.12.1/16` and `10.11.12.1/16` to the same physical server that has access to both trusted and insecure networks.

## IP outline per subdomain

- `x.x.0.0/16`
  - `x.x.0.0/24` - reserved (252 hosts)
    - `x.x.0.1/32` - gateway (1 host)
  - `x.x.4.0/22` - DHCP clients (1022 hosts)
    - `x.x.4.1` -> `x.x.7.254` (all /16 subnet)
  - `x.x.8.0/22` - static clients (1022 hosts)
  - `x.x.12.0/22` - static servers (1022 hosts)
    - `x.x.12.0/24` - physical (252 hosts)
    - `x.x.13.0/24` - virtual machines (252 hosts)
    - `x.x.14.0/24` - lxc containers (252 hosts)
  - `x.x.16.0/20` - static services (4094 hosts)
  - `x.x.32.0/20` - docker network (4094 hosts)
    - `x.x.32.0/24` - per network size (252 hosts) **ENSURE THIS RANGE DOES NOT OVERLAP WITH /16 ON THE SAME HOST!**
  - `x.x.64.0/20` -> `x.x.224.0/20` - available /20s
  - `x.x.240.0/24` -> `x.x.254.0/24` - available /24s
  - `x.x.255.0/24` - reserved (252 hosts)
    - `x.x.255.254/32` - broadcast (1 host)

## Docker considerations

When allocating a docker subnet, ensure it does not overlap with the parent /16 supernet, as it WILL cause routing issues. Recommendation is to use the `172.16.32.0/20` network.

## Management network outline per subdomain

- `10.99.0.0/16`
  - `10.99.0.0/24` - firewalls
  - `10.99.1.0/24` - routers
  - `10.99.2.0/24` - switches
  - `10.99.3.0/24` - wireless APs
  - `10.99.12.0/22` - ilo/server dedicated management
    - This should match the server static IP above to make it easier to recall
