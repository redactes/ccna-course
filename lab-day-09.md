# Configure hostnames
```
hostname SW1
```

```
hostname SW2
```

```
hostname R1
```

# Configure interface R1
```
int g0/0
ip address 172.16.255.254 255.255.0.0
speed 1000
duplex full
description ## Connection to SW1 ##
no shutdown
```

# Show and verify
```
show ip interface brief
```

# Configure interfaces not in use
```
int g0/1 - 2
description ## Not in use ##
```

# Configure interfaces on switch 1
```
int g0/1
speed 1000
duplex full
description ## Connection to R1 ##
```

```
int g0/2
speed 1000
duplex full
description ## Connection to SW2 ##
```

```
int range f0/1 - 2
description ## To end devices ##
```

```
int range f0/3 - 24
description ## Not in use ##
shutdown
```

# Save configurations
```
write memory
```

# Configure interfaces on switch 2
```
int g0/1
speed 1000
duplex full
description ## Connection to SW1 ##
```

```
int range f0/1 - 2
description ## To end devices ##
```

```
int range f0/3 - 24
description ## Not in use ##
shutdown
```