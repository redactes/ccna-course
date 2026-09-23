# Show R1's interfaces
show ip interface brief

# Configure interfaces
configure terminal

interface g0/0
ip address 15.255.255.254 255.0.0.0

interface g0/1
ip address 182.98.255.254 255.255.0.0

interface g0/2
ip address 201.191.20.254 255.255.255.0

# Confirm changes and save
show running-config
copy running-config startup-config