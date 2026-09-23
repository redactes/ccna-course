# Find the misconfigurations on each routers

## R1
```
show ip int brief
show ip route
```

Interfaces are set up correctly.  
Static route to 192.168.3.0/24 has a faulty next hop.

#### Fix:
```
no ip route 192.168.3.0 255.255.255.0 192.168.12.3
ip route 192.168.3.0 255.255.255.0 192.168.12.2
```

#### Verify:
```
show ip route
```

## R2
```
show ip int brief
show ip route
```

Both routes are set but the route to 192.168.3.0/24 is exiting out of the wrong interface.

#### Fix:
```
no ip route 192.168.3.0 255.255.255.0 G0/0
ip route 192.168.3.0 255.255.255.0 G0/1
```

#### Verify:
```
show ip route
```

## R3
```
show ip int brief
show ip route
```

There is a typo in the ip address of interface G0/0.  
192.168.23.3 instead of 192.168.13.3.

#### Fix:
```
conf t
int g0/0
ip add 192.168.13.3 255.255.255.0
```

#### Verify
```
show ip int brief
```