# Docker port allocations

## Standardised list

Each docker container has an allocated port the host listens on. Here are the allocations:

- 10000 - portainer
- 10001 - cadvisor
- 10002 - watchtower
- 10003 - prometheus
- 10004 - node-exporter
- 10005 - blackbox-exporter
- 10006 - snmp-exporter
- 10007 - heimdall
- 10008 - wikijs
- 10009 - guacamole
- 10010 - duplicati
- 10011 - grafana
- 10012 - home assistant
- 10013 - mosquitto mqtt
- 10014 - paperless
- 10015 - netbox
- 10016 - uptime kuma
- 10017 - nginx proxy manager (npm)
- 10018 - bitwarden
- 10019 - nextcloud
- 10020 - jackett
- 10021 - transmission
- 10022 - nzbhydra2
- 10023 - nzbget
- 10024 - sonarr
- 10025 - radarr
- 10026 - wordpress (Sam's Brain Dump)
- 10027 - plex

Where multiple instances of a container lives on the same docker instance, add `1000`, `2000` etc.

## Fixed port forwarded

These are special ports listening on the public IP

- 80 - npm - docker.dmz.drsam.cc:80
- 443 - npm - docker.dmz.drsam.cc:443
- 27333 - vrising - win.dmz.drsam.cc:27333
- 32400 - plex - docker.dmz.drsam.cc:32400
