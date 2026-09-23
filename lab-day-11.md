# R1
```
enable
configure terminal
hostname R1
interface g0/1
ip address 192.168.1.254 255.255.255.0
description ## To SW1 ##
no shutdown
```

```
interface g0/0
ip add 192.168.12.1 255.255.255.0
description ## To R2 ##
```

# Show and verify
show ip interface brief

# R2
```
enable
configure terminal
hostname R2
interface g0/0
ip add 192.168.12.2 255.255.255.0
description ## To R1 ##
no shutdown
```

```
interface G0/1
ip add 192.168.13.2 255.255.255.0
desc ## To R3 ##
no shutdown
```

# R3
```
enable
configure terminal
hostname R3
int g0/0
ip add 192.168.13.3 255.255.255.0
desc ## To R2 ##
no shutdown
```

```
int g0/1
ip add 192.168.3.254 255.255.255.0
desc ## To SW2 ##
no shut
```

# Static route @ R1
```
enable
conf t
ip route 192.168.3.0 255.255.255.0 192.168.12.2
```

# Show and verify
```
show ip route
```

# Static routes @ R2
```
enable
conf t
ip route 192.168.1.0 255.255.255.0 192.168.12.1
ip route 192.168.3.0 255.255.255.0 G0/1
```

# Static route @ R3
```
enable
conf t
ip route 192.168.1.0 255.255.255.0 192.168.13.2
```