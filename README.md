## Lab Overview & Implementation Notes

![](../z%20image/megalab%20topology.png)

![](../z%20image/topology%20int.png)

![](../z%20image/office%20topo.png)

This lab was planned as a complete enterprise network lab based on the concepts covered in Jeremy's IT Lab Mega Lab.

The main idea was to build the network step by step and cover the major CCNA topics together in one practical topology. The initial plan included a redundant network design, VLANs, EtherChannel, HSRP, OSPF, DHCP, NAT, security features, two ISP connections and wireless using a WLC.

During the actual implementation, most of the planned network was configured and tested. However, a few parts could not be completed exactly as originally planned because of Packet Tracer limitations and some simulator-specific behaviour.

### Main Changes & Limitations

- **Dual ISP connection**  
    The original plan was to have two ISP connections and test Internet failover using a primary and backup path. However, the required additional interface/module setup did not provide a usable second ISP connection in Packet Tracer. Because of this, the complete dual-ISP failover design could not be implemented as originally planned.
    
- **WLC / Wireless**  
    The original design included a working WLC with a separate Wi-Fi VLAN and wireless clients. We configured and checked the related VLAN, trunk and management connectivity, but the WLC was not behaving correctly in Packet Tracer. After troubleshooting the network side, the remaining WLC behaviour appeared to be related to the simulator limitation, so the wireless section was left as a documented limitation instead of changing the whole topology around it.
    
- **Wireless DHCP behaviour**  
    The Wi-Fi network and DHCP design were included in the original plan, but wireless clients could not be tested end-to-end in the same way as normal wired clients. Packet Tracer has limitations in this area, so the expected wireless DHCP behaviour could not be fully demonstrated.
    
- **Some implementation changes during configuration**  
    A few parts of the original design had to be adapted while building the lab because the available Packet Tracer device models and interfaces were not exactly the same as the original reference environment. The logical purpose of the network was kept, while the implementation was adjusted where required.
    
- **Troubleshooting became part of the lab**  
    Some problems were not solved simply by changing a command. We had to check interfaces, VLANs, trunks, connectivity, ARP behaviour and device behaviour to find out whether the problem was in our configuration or in Packet Tracer itself. This investigation is also part of the final project.
    

### Final Status
![](../z%20image/Screenshot%20from%202026-10-01%2009-49-53.png)
Because of these limitations, the final lab is not an exact copy of the original plan.
![](../z%20image/Screenshot%20from%202026-10-01%2009-53-20.png)
==The final topology represents what was actually configured and tested in the Packet Tracer environment. The remaining differences are documented here so that anyone reviewing the project can clearly understand what was planned, what was implemented, and where Packet Tracer prevented the original design from being completed.==

The project is therefore being kept in its final working state rather than making further changes only to force unsupported simulator behaviour.

> **The original design was the target. The final topology is the result of implementing, testing and troubleshooting that design in Packet Tracer.**