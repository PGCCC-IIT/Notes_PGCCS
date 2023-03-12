## mitm6

### Installation

```bash
sudo pip3 install mitm6
```

### Usage

```bash
mitm6 [-h] [-i INTERFACE] [-l LOCALDOMAIN] [-4 ADDRESS] [-6 ADDRESS] [-m ADDRESS] [-a] [-v] [--debug] [-d DOMAIN] [-b DOMAIN] [-hw DOMAIN] [-hb DOMAIN] [--ignore-nofqdn]
```

### Flags

```
optional arguments:
  -h, --help            show this help message and exit
  -i INTERFACE, --interface INTERFACE
                        Interface to use (default: autodetect)
  -l LOCALDOMAIN, --localdomain LOCALDOMAIN
                        Domain name to use as DNS search domain (default: use first DNS domain)
  -4 ADDRESS, --ipv4 ADDRESS
                        IPv4 address to send packets from (default: autodetect)
  -6 ADDRESS, --ipv6 ADDRESS
                        IPv6 link-local address to send packets from (default: autodetect)
  -m ADDRESS, --mac ADDRESS
                        Custom mac address - probably breaks stuff (default: mac of selected interface)
  -a, --no-ra           Do not advertise ourselves (useful for networks which detect rogue Router Advertisements)
  -v, --verbose         Show verbose information
  --debug               Show debug information

Filtering options:
  -d DOMAIN, --domain DOMAIN
                        Domain name to filter DNS queries on (Whitelist principle, multiple can be specified.)
  -b DOMAIN, --blacklist DOMAIN
                        Domain name to filter DNS queries on (Blacklist principle, multiple can be specified.)
  -hw DOMAIN, --host-whitelist DOMAIN
                        Hostname (FQDN) to filter DHCPv6 queries on (Whitelist principle, multiple can be specified.)
  -hb DOMAIN, --host-blacklist DOMAIN
                        Hostname (FQDN) to filter DHCPv6 queries on (Blacklist principle, multiple can be specified.)
  --ignore-nofqdn       Ignore DHCPv6 queries that do not contain the Fully Qualified Domain Name (FQDN) option.
```

### Examples

{{% notice warning %}}

To run mitm6 without interrupting the use of internet from the clients, you need to forward packets do this by running the following besides mitm6. (need to verify this)

```bash
sudo sysctl -w net.ipv4.ip_forward=1
sudo sysctl -p
```

{{% /notice %}}

#### MITM the whole network

(run in root terminal `sudo zsh`)

```bash
mitm6
```

#### Specific domain

Command below will send out IPv6 RA and catch DNS requests for lab.justin-p.me.

```bash
mitm6 -i eth0 -d lab.justin-p.me
```

#### Specific target

```bash
mitm6 -i eth0 -hw dc01.lab.justin-p.me.
```

### Also see

[Github project](https://github.com/fox-it/mitm6)
