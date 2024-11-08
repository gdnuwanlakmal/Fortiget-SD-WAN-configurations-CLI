# FortiGate SD-WAN Configurations CLI

## How to Configure FortiGate SD-WAN and Add ISP Interfaces

### Configure the WAN1 and WAN2 Interfaces

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
