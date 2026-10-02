Office A
├── 10.10.0.0/24     Management
├── 10.10.10.0/24    PCs
├── 10.10.20.0/24    Phones
└── 10.10.40.0/24    Wi-Fi

Office B
├── 10.20.0.0/24     Management
├── 10.20.10.0/24    PCs
├── 10.20.20.0/24    Phones
└── 10.20.30.0/24    Servers

Infrastructure
└── 10.100.0.0/24
    └── multiple /30 routed links

Loopbacks
└── 10.255.255.0/24
    └── individual /32 loopbacks


## WAN / Core Links

|Connection|Device A|Interface|IP Address|Device B|Interface|IP Address|Type|
|---|---|---|---|---|---|---|---|
|ISP-A — R1|R1|G0/0/0|203.0.113.2/30|ISP-A|—|203.0.113.1/30|WAN|
|ISP-B — R1|R1|G0/1/0|203.0.113.6/30|ISP-B|—|203.0.113.5/30|WAN|
|R1 — CSW1|R1|G0/0|10.100.0.1/30|CSW1|G1/0/1|10.100.0.2/30|L3 Transit|
|R1 — CSW2|R1|G0/1|10.100.0.5/30|CSW2|G1/0/1|10.100.0.6/30|L3 Transit|
|CSW1 — CSW2|CSW1|Port-Channel1|10.100.0.9/30|CSW2|Port-Channel1|10.100.0.10/30|L3 EtherChannel|
|CSW1 — DSW-A1|CSW1|G1/0/2|10.100.0.13/30|DSW-A1|G1/0/1|10.100.0.14/30|L3 Transit|
|CSW2 — DSW-A1|CSW2|G1/0/2|10.100.0.17/30|DSW-A1|G1/0/2|10.100.0.18/30|L3 Transit|
|CSW1 — DSW-A2|CSW1|G1/0/3|10.100.0.21/30|DSW-A2|G1/0/1|10.100.0.22/30|L3 Transit|
|CSW2 — DSW-A2|CSW2|G1/0/3|10.100.0.25/30|DSW-A2|G1/0/2|10.100.0.26/30|L3 Transit|
|CSW1 — DSW-B1|CSW1|G1/0/4|10.100.0.29/30|DSW-B1|G1/0/1|10.100.0.30/30|L3 Transit|
|CSW2 — DSW-B1|CSW2|G1/0/4|10.100.0.33/30|DSW-B1|G1/0/2|10.100.0.34/30|L3 Transit|
|CSW1 — DSW-B2|CSW1|G1/0/5|10.100.0.37/30|DSW-B2|G1/0/1|10.100.0.38/30|L3 Transit|
|CSW2 — DSW-B2|CSW2|G1/0/5|10.100.0.41/30|DSW-B2|G1/0/2|10.100.0.42/30|L3 Transit|

## Loopbacks

|Device|Interface|IP Address|Use|
|---|---|---|---|
|R1|Loopback0|10.255.255.1/32|OSPF Router ID|
|CSW1|Loopback0|10.255.255.2/32|OSPF Router ID|
|CSW2|Loopback0|10.255.255.3/32|OSPF Router ID|
|DSW-A1|Loopback0|10.255.255.4/32|OSPF Router ID|
|DSW-A2|Loopback0|10.255.255.5/32|OSPF Router ID|
|DSW-B1|Loopback0|10.255.255.6/32|OSPF Router ID|
|DSW-B2|Loopback0|10.255.255.7/32|OSPF Router ID|


## Office A

### Management — VLAN 99

|Network|Device|Interface|IP Address|Notes|
|---|---|---|---|---|
|10.10.0.0/24|HSRP|VLAN 99|10.10.0.1|Default gateway|
|10.10.0.0/24|DSW-A1|VLAN 99|10.10.0.2|HSRP member|
|10.10.0.0/24|DSW-A2|VLAN 99|10.10.0.3|HSRP member|
|10.10.0.0/24|WLC1|Management|10.10.0.4|Management|
|10.10.0.0/24|ASW-A1|VLAN 99|10.10.0.5|Switch management|
|10.10.0.0/24|ASW-A2|VLAN 99|10.10.0.6|Switch management|
|10.10.0.0/24|ASW-A3|VLAN 99|10.10.0.7|Switch management|

### User VLANs

|Network|VLAN|Device|Interface|IP Address|Notes|
|---|--:|---|---|---|---|
|10.10.10.0/24|10|HSRP|VLAN 10|10.10.10.1|Default gateway|
|10.10.10.0/24|10|DSW-A1|VLAN 10|10.10.10.2|HSRP member|
|10.10.10.0/24|10|DSW-A2|VLAN 10|10.10.10.3|HSRP member|
|10.10.20.0/24|20|HSRP|VLAN 20|10.10.20.1|Default gateway|
|10.10.20.0/24|20|DSW-A1|VLAN 20|10.10.20.2|HSRP member|
|10.10.20.0/24|20|DSW-A2|VLAN 20|10.10.20.3|HSRP member|
|10.10.40.0/24|40|HSRP|VLAN 40|10.10.40.1|Default gateway|
|10.10.40.0/24|40|DSW-A1|VLAN 40|10.10.40.2|HSRP member|
|10.10.40.0/24|40|DSW-A2|VLAN 40|10.10.40.3|HSRP member|
|10.10.40.0/24|40|WLC1|Dynamic Interface|10.10.40.4|Wi-Fi VLAN|

## Office B

### Management — VLAN 99

|Network|Device|Interface|IP Address|Notes|
|---|---|---|---|---|
|10.20.0.0/24|HSRP|VLAN 99|10.20.0.1|Default gateway|
|10.20.0.0/24|DSW-B1|VLAN 99|10.20.0.2|HSRP member|
|10.20.0.0/24|DSW-B2|VLAN 99|10.20.0.3|HSRP member|
|10.20.0.0/24|ASW-B1|VLAN 99|10.20.0.4|Switch management|
|10.20.0.0/24|ASW-B2|VLAN 99|10.20.0.5|Switch management|
|10.20.0.0/24|ASW-B3|VLAN 99|10.20.0.6|Switch management|

### User VLANs

| Network       | VLAN | Device | Interface        | IP Address | Notes           |
| ------------- | ---: | ------ | ---------------- | ---------- | --------------- |
| 10.20.10.0/24 |   10 | HSRP   | VLAN 10          | 10.20.10.1 | Default gateway |
| 10.20.10.0/24 |   10 | DSW-B1 | VLAN 10          | 10.20.10.2 | HSRP member     |
| 10.20.10.0/24 |   10 | DSW-B2 | VLAN 10          | 10.20.10.3 | HSRP member     |
| 10.20.20.0/24 |   20 | HSRP   | VLAN 20          | 10.20.20.1 | Default gateway |
| 10.20.20.0/24 |   20 | DSW-B1 | VLAN 20          | 10.20.20.2 | HSRP member     |
| 10.20.20.0/24 |   20 | DSW-B2 | VLAN 20          | 10.20.20.3 | HSRP member     |
| 10.20.30.0/24 |   30 | HSRP   | VLAN 30          | 10.20.30.1 | Default gateway |
| 10.20.30.0/24 |   30 | DSW-B1 | VLAN 30          | 10.20.30.2 | HSRP member     |
| 10.20.30.0/24 |   30 | DSW-B2 | VLAN 30          | 10.20.30.3 | HSRP member     |
| 10.20.30.0/24 |   30 | Server | F0/24 via ASW-B3 | 10.20.30.4 | Server          |


# Interface Mapping

| Device A | Device A Interface | Device B Interface | Device B |
| -------- | ------------------ | ------------------ | -------- |
| R1       | G0/0               | G1/0/1             | CSW1     |
| R1       | G0/1               | G1/0/1             | CSW2     |
|          |                    |                    |          |
| CSW1     | G1/0/1             | G0/0               | R1       |
| CSW1     | G1/0/2             | G1/0/1             | DSW-A1   |
| CSW1     | G1/0/3             | G1/0/1             | DSW-A2   |
| CSW1     | G1/0/4             | G1/0/1             | DSW-B1   |
| CSW1     | G1/0/5             | G1/0/1             | DSW-B2   |
| CSW1     | G1/0/6             | G1/0/6             | CSW2     |
| CSW1     | G1/0/7             | G1/0/7             | CSW2     |
|          |                    |                    |          |
| CSW2     | G1/0/1             | G0/1               | R1       |
| CSW2     | G1/0/2             | G1/0/2             | DSW-A1   |
| CSW2     | G1/0/3             | G1/0/2             | DSW-A2   |
| CSW2     | G1/0/4             | G1/0/2             | DSW-B1   |
| CSW2     | G1/0/5             | G1/0/2             | DSW-B2   |
| CSW2     | G1/0/6             | G1/0/6             | CSW1     |
| CSW2     | G1/0/7             | G1/0/7             | CSW1     |
|          |                    |                    |          |
| DSW-A1   | G1/0/1             | G1/0/2             | CSW1     |
| DSW-A1   | G1/0/2             | G1/0/2             | CSW2     |
| DSW-A1   | G1/0/10            | G0/1               | ASW-A1   |
| DSW-A1   | G1/0/11            | G0/1               | ASW-A2   |
| DSW-A1   | G1/0/12            | G0/1               | ASW-A3   |
| DSW-A1   | G1/0/23            | G1/0/23            | DSW-A2   |
| DSW-A1   | G1/0/24            | G1/0/24            | DSW-A2   |
|          |                    |                    |          |
| DSW-A2   | G1/0/1             | G1/0/3             | CSW1     |
| DSW-A2   | G1/0/2             | G1/0/3             | CSW2     |
| DSW-A2   | G1/0/10            | G0/2               | ASW-A1   |
| DSW-A2   | G1/0/11            | G0/2               | ASW-A2   |
| DSW-A2   | G1/0/12            | G0/2               | ASW-A3   |
| DSW-A2   | G1/0/23            | G1/0/23            | DSW-A1   |
| DSW-A2   | G1/0/24            | G1/0/24            | DSW-A1   |
|          |                    |                    |          |
| DSW-B1   | G1/0/1             | G1/0/4             | CSW1     |
| DSW-B1   | G1/0/2             | G1/0/4             | CSW2     |
| DSW-B1   | G1/0/10            | G0/1               | ASW-B1   |
| DSW-B1   | G1/0/11            | G0/1               | ASW-B2   |
| DSW-B1   | G1/0/12            | G0/1               | ASW-B3   |
| DSW-B1   | G1/0/23            | G1/0/23            | DSW-B2   |
| DSW-B1   | G1/0/24            | G1/0/24            | DSW-B2   |
|          |                    |                    |          |
| DSW-B2   | G1/0/1             | G1/0/5             | CSW1     |
| DSW-B2   | G1/0/2             | G1/0/5             | CSW2     |
| DSW-B2   | G1/0/10            | G0/2               | ASW-B1   |
| DSW-B2   | G1/0/11            | G0/2               | ASW-B2   |
| DSW-B2   | G1/0/12            | G0/2               | ASW-B3   |
| DSW-B2   | G1/0/23            | G1/0/23            | DSW-B2   |
| DSW-B2   | G1/0/24            | G1/0/24            | DSW-B2   |
|          |                    |                    |          |
| ASW-A1   | G0/1               | G1/0/10            | DSW-A1   |
| ASW-A1   | G0/2               | G1/0/10            | DSW-A2   |
| ASW-A1   | F0/1               | —                  | AP1      |
| ASW-A1   | F0/24              | —                  | WLC      |
|          |                    |                    |          |
| ASW-A2   | G0/1               | G1/0/11            | DSW-A1   |
| ASW-A2   | G0/2               | G1/0/11            | DSW-A2   |
| ASW-A2   | F0/1               | —                  | IP PHONE |
|          |                    |                    |          |
| ASW-A3   | G0/1               | G1/0/12            | DSW-A1   |
| ASW-A3   | G0/2               | G1/0/12            | DSW-A2   |
| ASW-A3   | F0/2               | —                  | IP PHONE |
|          |                    |                    |          |
| ASW-B1   | G0/1               | G1/0/10            | DSW-B1   |
| ASW-B1   | G0/2               | G1/0/10            | DSW-B2   |
| ASW-B1   | F0/1               | —                  | AP2      |
|          |                    |                    |          |
| ASW-B2   | G0/1               | G1/0/11            | DSW-B1   |
| ASW-B2   | G0/2               | G1/0/11            | DSW-B2   |
| ASW-B2   | F0/1               | —                  | IP PHONE |
|          |                    |                    |          |
| ASW-B3   | G0/1               | G1/0/12            | DSW-B1   |
| ASW-B3   | G0/2               | G1/0/12            | DSW-B2   |
| ASW-B3   | F0/1               | —                  | IP PHONE |
| ASW-B3   | F0/24              | —                  | SERVER   |
