# Jarkom-Modul-5-B03-2021

Anggota Kelompok:
1. Ahmad Syafiq Aqil Wafi (05111940000089)
2. Dewangga Dharmawan (05111940000029)

## Subnetting

Untuk mengerjakan modul 5 ini, kami memilih untuk menggunakan subnetting CIDR karena lebih mudah.

### Proses Subnetting

![image](https://user-images.githubusercontent.com/16128257/145672855-621efa2a-9e12-4dbb-8ad8-decf03a6d40e.png)

![image](https://user-images.githubusercontent.com/16128257/145672867-5a0484fb-a754-4b06-bdf9-2cc540201b56.png)

![image](https://user-images.githubusercontent.com/16128257/145672874-c43cb35b-d801-4cf8-bc83-d8b41a424cb9.png)

![image](https://user-images.githubusercontent.com/16128257/145672880-30a41787-ce7c-4ff0-955c-06775fc8f4b9.png)

![image](https://user-images.githubusercontent.com/16128257/145672886-8155fd79-4c9e-43b5-880c-3b733efb819d.png)

### Hasil Subnetting

![image](https://user-images.githubusercontent.com/16128257/145672910-5d460ad7-3dce-4c82-9b40-70962826c21c.png)

### NID Network

```
A1: 192.178.0.0/29
A2: 192.178.8.0/25
A3: 192.178.16.0/30
A4: 192.178.4.0/22
A5: 192.178.36.0/30
A6: 192.178.34.0/23
A7: 192.178.32.0/24
A8: 192.178.33.0/29
```

### Konfigurasi Network Interface

#### FOOSHA

```
auto eth0
iface eth0 inet dhcp

# A3: 192.178.16.0/30
auto eth1
iface eth1 inet static
	address 192.178.16.1
	netmask 255.255.255.252

# A5: 192.178.36.0/30
auto eth2
iface eth2 inet static
	address 192.178.36.1
	netmask 255.255.255.252
```

#### WATER7

```
# A3: 192.178.16.0/30
auto eth0
iface eth0 inet static
	address 192.178.16.2
	netmask 255.255.255.252
        gateway 192.178.16.1
        up echo nameserver 192.168.122.1 > /etc/resolv.conf

# A2: 192.178.8.0/25
auto eth1
iface eth1 inet static
	address  192.178.8.1
	netmask 255.255.255.128

# A4: 192.178.4.0/22
auto eth2
iface eth2 inet static
	address 192.178.4.1
	netmask 255.255.252.0

# A1: 192.178.0.0/29
auto eth3
iface eth3 inet static
	address 192.178.0.1
	netmask 255.255.255.248
```

#### BLUENO

```
# A2: 192.178.8.0/25
auto eth0
iface eth0 inet static
	address 192.178.8.2
	netmask 255.255.255.128
        gateway 192.178.8.1
        up echo nameserver 192.168.122.1 > /etc/resolv.conf
```

#### CIPHER

```
# A4: 192.178.4.0/22
auto eth0
iface eth0 inet static
	address 192.178.4.2
	netmask 255.255.252.0
        gateway 192.178.4.1
        up echo nameserver 192.168.122.1 > /etc/resolv.conf
```


#### DORIKI

```
# A1: 192.178.0.0/29
auto eth0
iface eth0 inet static
	address 192.178.0.2
	netmask 255.255.255.248
        gateway 192.178.0.1
        up echo nameserver 192.168.122.1 > /etc/resolv.conf
```

#### JIPANGU

```
# A1: 192.178.0.0/29
auto eth0
iface eth0 inet static
	address 192.178.0.3
	netmask 255.255.255.248
        gateway 192.178.0.1
        up echo nameserver 192.168.122.1 > /etc/resolv.conf
```

#### GUANHAO

```
# A5: 192.178.36.0/30
auto eth0
iface eth0 inet static
	address 192.178.36.2
	netmask 255.255.255.252
        gateway 192.178.36.1
        up echo nameserver 192.168.122.1 > /etc/resolv.conf

# A6: 192.178.34.0/23
auto eth1
iface eth1 inet static
	address 192.178.34.1
	netmask 255.255.254.0

# A7: 192.178.32.0/24
auto eth2
iface eth2 inet static
	address 192.178.32.1
	netmask 255.255.255.0

# A8: 192.178.33.0/29
auto eth3
iface eth3 inet static
	address 192.178.33.1
	netmask 255.255.255.248
```

#### ELENA

```
# A6: 192.178.34.0/23
auto eth0
iface eth0 inet static
	address 192.178.34.2
	netmask 255.255.254.0
        gateway 192.178.34.1
        up echo nameserver 192.168.122.1 > /etc/resolv.conf
```

#### FUKUROU

```
# A7: 192.178.32.0/24
auto eth0
iface eth0 inet static
	address 192.178.32.2
	netmask 255.255.255.0
        gateway 192.178.32.1
        up echo nameserver 192.168.122.1 > /etc/resolv.conf
```

#### JORGE

```
# A8: 192.178.33.0/29
auto eth0
iface eth0 inet static
	address 192.178.33.2
	netmask 255.255.255.248
        gateway 192.178.33.1
        up echo nameserver 192.168.122.1 > /etc/resolv.conf
```

#### MAINGATE

```
# A8: 192.178.33.0/29
auto eth0
iface eth0 inet static
	address 192.178.33.3
	netmask 255.255.255.248
        gateway 192.178.33.1
        up echo nameserver 192.168.122.1 > /etc/resolv.conf
```

### Konfigurasi Routing

#### FOOSHA

```
route add -net 192.178.0.0 netmask 255.255.255.248 gw 192.178.16.2 #A3 - A1
route add -net 192.178.8.0 netmask 255.255.255.128 gw 192.178.16.2 #A3 - A2
route add -net 192.178.4.0 netmask 255.255.252.0 gw 192.178.16.2 #A3 - A4
route add -net 192.178.34.0 netmask 255.255.254.0 gw 192.178.36.2 #A5 - A6
route add -net 192.178.32.0 netmask 255.255.255.0 gw 192.178.36.2 #A5 - A7
route add -net 192.178.33.0 netmask 255.255.255.248 gw 192.178.36.2 #A5 - A8
```

#### WATER7

```
route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.178.16.1 #A3 - Self
```

#### GUANHAO

```
route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.178.36.1 #A5 - Self
```


## Referensi
- https://qastack.id/raspberrypi/8614/isc-dhcp-server-install-and-run-problem
- https://support.cumulusnetworks.com/hc/en-us/articles/201787526-Configuring-DHCP-Relays
- https://www.karlrupp.net/en/computer/nat_tutorial
- https://ipset.netfilter.org/iptables-extensions.man.html
- https://ipset.netfilter.org/iptables.man.html
