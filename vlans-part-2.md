# Configure the switch interfaces as access ports
## SW1
int range f0/1, f0/2
switchport mode access
switchport access vlan 10

int range f0/3, f0/4
switchport mode access
switchport access vlan 30

## SW2
int range f0/2,f0/3
switchport mode access
switchport access vlan 10

int f0/1
switchport mode access
switchport access vlan 20

vlan 30

# Configure line between switches as trunk
interface g0/1
switchport mode trunk
switchport trunk allowed vlan 10,30
switchport trunk native vlan 1001

# Line between R1 and SW2 (switch side)
int g0/2
sw mo tr
sw tr na vlan 1001
sw tr all vlan 10,20,30

# ROAS on R1
int g0/0.10
encapsulation dot1q 10
ip add 10.0.0.62 255.255.255.192

int g0/0.20
encapsulation dot1q 20
ip add 10.0.0.126 255.255.255.192

int g0/0.30
encapsulation dot1q 30
ip add 10.0.0.190 255.255.255.192

# Show and verify
show interfaces trunk
show ip int brief
show vlan