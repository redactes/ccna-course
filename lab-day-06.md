# Generate traffic to fill up mac tables of switches
ping pc1
ping pc2
ping pc3
ping pc4

# Show mac table
show mac-address-table

# Clear mac table entirely
clear mac-address-table 

# Clear dynamic macs
clear mac-address-table dynamic