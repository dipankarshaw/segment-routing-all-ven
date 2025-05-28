## Arista
```

interface Loopback0
   node-segment ipv4 index 45
   node-segment ipv6 index 65
!
mpls ip
!
router isis 1
   segment-routing mpls
      no shutdown
!
```

## Juniper
```
set chassis network-services enhanced-ip
set interfaces ge-0/0/2 unit 0 family inet address 10.68.0.8/24
set interfaces ge-0/0/2 unit 0 family iso
set interfaces ge-0/0/2 unit 0 family inet6 address 2000:abcd:68::8/64
set interfaces ge-0/0/2 unit 0 family mpls
set interfaces ge-0/0/3 unit 0 family inet address 10.58.0.8/24
set interfaces ge-0/0/3 unit 0 family iso
set interfaces ge-0/0/3 unit 0 family inet6 address 2000:abcd:58::8/64
set interfaces ge-0/0/3 unit 0 family mpls
set interfaces lo0 unit 0 family inet address 172.0.0.8/32
set interfaces lo0 unit 0 family inet6 address abcd::8/128
set routing-options router-id 172.0.0.8
set protocols isis interface ge-0/0/2.0 point-to-point
set protocols isis interface ge-0/0/3.0 point-to-point
set protocols isis interface lo0.0 level 2 metric 1
set protocols isis source-packet-routing srgb start-label 16000
set protocols isis source-packet-routing srgb index-range 8000
set protocols isis source-packet-routing node-segment ipv4-index 48
set protocols isis source-packet-routing node-segment ipv6-index 68
set protocols isis level 1 disable
set protocols isis net 49.0001.0000.0000.0008.00
set protocols mpls interface ge-0/0/2.0
set protocols mpls interface ge-0/0/3.0

```
