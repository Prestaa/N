# 🌐 Network cheatsheet

<ul>
    <a href="#Utils">Utils</a>
    <a href="#General-security">Security</a>
    <a href="#Enable-SSH">SSH</a>
</ul>

## Cisco

### Utils

#### Section
```
show running-config | section line vty
```
Output
```
line vty 0 4
  password 7 094F471A1A0A
  exec-timeout 5 30
  login
  transport input ssh
```

#### Include
```
show running-config | include line 192
```

Output
```
ip address 192.168.1.1 255.255.255.0
```

### General security
```bash
! Chiffrement des mots de passes locaux cisco
service password-encryption

! Forcer une taille minimale pour les mots de passes
security passwords min-length 8

! Bloquer pendant deux minutes si trois fails en une minutes
login block-for 120 attempts 3 within 60

! Mettre un mot de passe pour le enable
enable secret MY_SECURE_PASSWORD

! Mettre un mot de passe ou terminaux virtuel
line vty 0 4 
password MY_SECURE_PASSWORD
exec-timeout 5 30 
```

### Enable SSH

```bash
configure terminal
hostname R1
ip domain name span.com
crypto key generate rsa general-keys modulus 1024

username USERNAME secret PASSWORD

line vty 0 4
login local
transport input ssh
```

