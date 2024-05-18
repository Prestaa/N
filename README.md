<ul>
    <div><a href="#IP">🌐</a> <b>IP</b></div>
    <ul>
         <li>
            <a href="#ip-address">IP Address</a>
         </li>
         <li>
            <a href="#routes">Routing</a>
         </li>
    </ul>
    <div><a href="#cisco">📡</a> <b>CISCO</b></div>
     <ul>
        <li>
            <div><a href="#configuration">🛠️</a> <b>CONFIGURATION</b></div>
            <ul>
                <li>
                    <a href="#ip-address-1">IP Address</a>
                </li>
                <li>
                    <a href="#routes-1">Routing</a>
                </li>
            </ul>
        </li>
        <li>
            <div><a href="#utils">📦</a> <b>UTILS</b></div>
            <ul>
                <li>
                    <a href="#section">Section</a>
                </li>
                <li>
                    <a href="#include">Include</a>
                </li>
            </ul>
        </li>
        <li>
            <div><a href="#security">🛡️</a> <b>SECURITY</b></div>
            <ul>
                <li>
                    <a href="#general-security">Good practices</a>
                </li>
                <li>
                    <a href="#enable-ssh">Enable SSH</a>
                </li>
            </ul>
        </li>
    </ul>
    <div><a href="#tools">⚡</a> <b>TOOLS</b></div>
    <ul>
         <li>
            <a target="_blank" href="https://www.site24x7.com/fr/tools/ipv4-sous-reseau-calculatrice.html">Subnet calculator</a>
         </li>
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

