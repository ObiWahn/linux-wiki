# Netfiler

Page about netfilter and iptables

## Links

- https://www.kernel.org/doc/Documentation/networking/ip-sysctl.txt
- http://linux-ip.net/nf/nfk-traversal.pdf
- http://developer.gauner.org/doc/iptables/images/nfk-traversal.png (same as above but png)
- https://wiki.nftables.org/wiki-nftables/index.php/Main_Page
- ipsec
  - https://thermalcircle.de/doku.php?id=blog:linux:nftables_ipsec_packet_flow
  - https://thermalcircle.de/lib/exe/fetch.php?media=linux:packet-flow-ipsec-tunnel.png


## Iptables

### Examples

#### DNAT

```sh
iptables -t nat -D PREROUTING -i "$interface" -d "$sip1" -p udp --dport "$sport1" -j DNAT --to-destination "$dip1:$dport1"
iptables -t nat -A PREROUTING -i "$interface" -d "$sip1" -p udp --dport "$sport1" -j DNAT --to-destination "$dip1:$dport1"
```

## Pitfalls

### `route_localnet`

You may not reroute pacakges from some other device to lo (127/8). If you do that the packages
are martian and dropped by the kernel if you do not turn `route_localnet` on. What you should
not do!

### tcpdump

`tcpdump` sees data before it enters the prerouting chain. So do not try to use it
to verigy your netfilter configuration. Mark packages with `-j NFLOG` instead and
use `tcpdump -i nflog`

