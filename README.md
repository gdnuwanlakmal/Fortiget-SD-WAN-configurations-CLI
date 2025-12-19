<p align="center">
  <img
    src="https://github.com/user-attachments/assets/2717e193-16a6-4886-b904-aa4f038a5d08"
    width="300"
  />
  <br />
</p>

# FortiGate-SD-WAN-configurations-CLI

## How to Configure FortiGate SD-WAN and Add ISP Interfaces

This guide provides CLI commands to configure SD-WAN on a FortiGate device, including adding ISP interfaces to WAN links.

### 1. Configure the WAN1 and WAN2 Interfaces

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
```

### 2. Enable SD-WAN and Add the Interfaces as Members

```shell
config system sdwan
    set status enable   
    config members
    
    edit 1
        set interface "wan1"
    next
    edit 2
        set interface "wan2"
        set gateway 10.100.20.2
    next
end
```

### 3. Create a Static Route for SD-WAN

```shell
config router static
    edit 1
        set sdwan-zone "virtual-wan-link"
    next
end
```
