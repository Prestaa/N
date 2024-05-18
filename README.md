# 🌐 Network cheatsheet

<ul>
    <a href="#Cisco"></a>
</ul>

## Cisco

### General securisation
```bash
! Chiffrement des mots de passes locaux cisco
service password-encryption 
security passwords min-length 8 
R1(config)# login block-for 120 attempts 3 within 60
R1(config)# line vty 0 4 
R1(config-line)# password cisco123 
R1(config-line)# exec-timeout 5 30 
R1(config-line)# transport input ssh 
R1(config-line)# end 
R1# 
R1# show running-config | section line vty
line vty 0 4
  password 7 094F471A1A0A
  exec-timeout 5 30
  login
  transport input ssh
R1#
```
