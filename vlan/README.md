# VLANs

VLANs should be assigned by access requirements. So devices with similar needs for routing, isolation etc. should be on separate VLANs.
This includes internet access, via VPN, no internet access, no access or limited access to any other VLANs etc.

## Allocations per network

We're achieving network isolation with multiple VLANs. Each VLAN has its own allocated /16 IP range, which is routed via `fwl01.mgmt.drsam.cc`.
Each also has a separate non-overlapping subdomain on DNS.

- VLAN 10 (trusted devices with direct internet)
  - trust.drsam.cc
  - 10.10.0.0/16
- VLAN 11 (insecure devices with VPN internet)
  - insec.drsam.cc
  - 10.11.0.0/16
- VLAN 20 (WAN point-to-point L2 links)
  - wan.drsam.cc
  - No IP range (L2 only)
- VLAN 21 (Public DMZ - port forwarded network)
  - dmz.drsam.cc
  - 192.168.0.0/16
- VLAN 40 (IoT with internet)
  - iot.drsam.cc
  - 10.40.0.0/16
- VLAN 41 (IoT without internet)
  - not.drsam.cc
  - 10.41.0.0/16
- VLAN 50 (Cameras without internet)
  - cam.drsam.cc
  - 10.50.0.0/16
- VLAN 99 (Management)
  - mgmt.drsam.cc
  - 10.99.0.0/16


