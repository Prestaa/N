# 🌐 Network cheatsheet

<ul>
    <ul>
        <a href="#IP">IP</a>
        <ul>
             <li>
                <a href="#Utils">Utils</a>
            </li>
        </ul>
    </li>
    <ul>
        <a href="#Cisco">CISCO</a>
         <ul>
            <li>
                <a href="#Utils">Utils</a>
            </li>
            <li>
                <a href="#General-security">Security</a>
            </li>
            <li>
                <a href="#Enable-SSH">SSH</a>
            </li>
        </ul>
    </ul>
</ul>

## IP
#### IP Address
**Set an ip address**
```bash
ip addr add ip/mask dev INAME
```

To unset an ip address, simply replace "add" by "delete".
#### Routes
**Set a route**
```bash
ip route add ip/mask via gw
```

**Set the default gw**
```bash
ip route add default via gw
```

To unset an route or the default gateway, simply replace "add" by "delete".


## Cisco

### Configuration

#### IP Address
**Set an ip address**
```bash
interface X
ip add ip/mask
```

To unset an ip address, simply add "no" before the "ip" command.
#### Routes
**Set a route**
```bash
ip route ip mask gw
```

**Set the default gw**
```bash
ip default-gateway gw
```

To unset an ip address, simply add "no" before the "ip" command.

### Utils

#### Section
```bash
show running-config | section line vty
```
Output
```bash
line vty 0 4
  password 7 094F471A1A0A
  exec-timeout 5 30
  login
  transport input ssh
```

#### Include
```bash
show running-config | include line 192
```

Output
```bash
ip address 192.168.1.1 255.255.255.0
```

### Security
#### General security
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

#### Enable SSH

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

