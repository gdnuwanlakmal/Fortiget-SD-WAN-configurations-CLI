# Fortiget-SD-WAN-configurations-CLI-
How to Configure FortiGate SD-WAN and Add ISP Interfaces

# Configure the WAN1 and WAN2 Interfaces:

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

#Enable SD-WAN and add the interfaces as members:

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
end

Create a static route for SD-WAN:

config router static
    edit 1
        set sdwan-zone "virtual-wan-link"
    next
end

Select the implicit SD-WAN algorithm:

config system sdwan
    set load-balance-mode {source-ip-based | weight-based | source-dest-ip-based | measured-volume-based}
end

