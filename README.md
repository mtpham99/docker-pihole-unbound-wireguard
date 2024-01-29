# Docker-Pihole-Unbound-Wireguard

My homelab's docker for running Pihole with Unbound DNS.

All docker services are run using a "macvlan" network providing each service with a unique ip address on the LAN avoiding port clashes with the host running the docker containers.

A macvlan bridge to the host's primary network interface is used to allow host-container (and vice-versa) communication. See "Macvlan Networking" below for more info.

## Scheduled Updates

Scheduled updates can be made by adding the line below to one's crontab:

```
# Weekly updates at 5am on Sunday
0 5 * * 1 cd pihole-unbound-wireguard && docker compose pull && docker compose down && docker compose up -d
```

## Resources

Some informative resources/links that helped set this up:

### Macvlan Networking
1. [Pihole Macvlan](https://tonylawrence.com/posts/unix/synology/free-your-synology-ports/)
2. [Docker Macvlan](https://blog.oddbit.com/post/2018-03-12-using-docker-macvlan-networks/)
3. [Macvlan-Host Communication](https://kcore.org/2020/08/18/macvlan-host-access/)
4. [Pihole Docker](https://github.com/pi-hole/docker-pi-hole)

### Unbound DNS
1. [Pihole Unbound DNS](https://docs.pi-hole.net/guides/dns/unbound/)
2. [Unbound Docker](https://github.com/MatthewVance/unbound-docker)

### Wireguard
1. [Wireguard Docker](https://github.com/linuxserver/docker-wireguard)
2. [Duckdns](https://www.duckdns.org/about.jsp)

### Misc.
1. [IP Calculator](https://jodies.de/ipcalc?host=192.168.0.64&mask1=26&mask2=)
