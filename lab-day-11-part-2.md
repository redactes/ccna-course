# Find the misconfigurations on each routers
```
show ip int brief
show ip route
```

Interfaces are set up correctly.
Static route to 192.168.3.0/24 has a faulty next hop.

Fix:
```
no ip route 192.168.3.0 255.255.255.0 192.168.12.3
ip route 192.168.3.0 255.255.255.0 192.168.12.2
```

Verify:
```
show ip route
```