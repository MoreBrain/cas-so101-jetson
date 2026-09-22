# Network
Wifi: PhysicalAI
pw: given by tutor

or faster via cable to the physical ai router

# updates
sudo apt update


# Installation

- git
- docker
- uv


# create ssh-keys so you can login from other laptop without typing password each time
```
ssh-keygen -t ed25519
```

## ssh to jetson
- over wifi: 
  - get IP address on the jetson -> portable screen- run ifconfig on jetson -> see IP address (ssh ema-student@IP-ADDRESS)
  - ssh ema-student@IP-ADDRESS (pw provided by tutor)

-over connected ethernet cable:
  - TODO

