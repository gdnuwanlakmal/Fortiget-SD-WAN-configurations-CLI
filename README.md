# FortiGate SD-WAN Configuration Guide

A quick guide on configuring FortiGate SD-WAN and adding ISP interfaces using CLI commands.

## Step 1: Configure WAN1 and WAN2 Interfaces

To set up the WAN interfaces with different ISPs, use the following commands:

```shell
config system interface 
    edit "wan1"
        set alias to_ISP1
        set mode dhcp
        set distance 10
    next
    edit "wan2"
        set alias to_ISP2
        set ip 10.100.20.1 255.255.255.0
    next
end
