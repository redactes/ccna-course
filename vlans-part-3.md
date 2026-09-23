# Remove existing dot1q configs
no interface g0/0.10
no interface g0/0.20
no interface g0/0.30

# Reset g0/0 to default config
default interface g0/0

# Set IP of G0/0
interface g0/0
ip add 10.0.0.194 255.255.255.252
no shutdown

# Enable routing on switch
ip routing

# Set IP of G1/0/2
interface g1/0/2
no switchport
ip add 10.0.0.193 255.255.255.252
no shutdown

# Default route
ip route 0.0.0.0 0.0.0.0 10.0.0.194

# SVI's
interface vlan 10
ip add 10.0.0.62 255.255.255.192

interface vlan 20
ip add 10.0.0.126 255.255.255.192

interface vlan 30
ip add 10.0.0.190 255.255.255.192

# Show and verify
show run
show ip route
show ip int brief
show vlan brief


