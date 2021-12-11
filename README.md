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
iface eth0 inet dhcp
```

#### CIPHER

```
# A4: 192.178.4.0/22
auto eth0
iface eth0 inet dhcp
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
iface eth0 inet dhcp
```

#### FUKUROU

```
# A7: 192.178.32.0/24
auto eth0
iface eth0 inet dhcp
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

## Prerequisites

Jalankan iptables MASQUERADE pada FOOSHA dan routing nya agar subnet dapat akses internet.

```
iptables -t nat -D POSTROUTING -o eth0 -j MASQUERADE -s 192.178.0.0/16
```

Setelah itu kita install hal - hal yang diperlukan untuk masing - masing node.

Buat DHCP Relay pada router FOOSHA, WATER7 dan GUANHAO dengan command berikut. Jika muncul suatu interpreter tekan enter hingga kembali pada terminal.

```
apt-get update
apt-get install isc-dhcp-relay -y
```

Kemudian install DHCP server pada JIPANGU dengan command berikut. Jika muncul suatu interpreter tekan enter hingga kembali pada terminal.

```
apt-get update
apt-get install isc-dhcp-server -y
```

Kemudian pada JIPANGU edit pada `/etc/default/isc-dhcp-server` edit line interface menjadi berikut.

```
INTERFACES="eth0"
```

Kemudian pada JIPANGU edit pada `/etc/dhcp/dhcpd.conf`. Tambahkan line berikut. Dengan `192.178.0.2` adalah IP DNS Server DORIKI dan `192.168.122.1` merupakan nameserver NAT pada `/etc/resolv.conf` pada FOOSHA.

```
subnet 192.178.0.0 netmask 255.255.252.0 {

}

# BLUENO : A2: 192.178.8.0/25 - 100 Host
subnet 192.178.8.0 netmask 255.255.255.128 {
        range 192.178.8.2 192.178.8.127;
        option routers 192.178.8.1;
        option broadcast-address 192.178.8.128;
        option domain-name-servers 192.178.0.2, 192.168.122.1;
}

# CIPHER : A4: 192.178.4.0/22 - 700 Host
subnet 192.178.4.0 netmask 255.255.252.0 { 
        range 192.178.4.2 192.178.7.254;
        option routers 192.178.4.1;
        option broadcast-address 192.178.7.255;
        option domain-name-servers 192.178.0.2, 192.168.122.1;
}

# ELENA : A6: 192.178.34.0/23 - 300 Host
subnet 192.178.34.0 netmask 255.255.254.0 { 
        range 192.178.34.2 192.178.35.254;
       option routers 192.178.34.1;
        option broadcast-address 192.178.35.255;
        option domain-name-servers 192.178.0.2, 192.168.122.1;
}

# FUKUROU : A7: 192.178.32.0/24 - 200 Host
subnet 192.178.32.0 netmask 255.255.255.0 { 
        range 192.178.32.2 192.178.32.254;
        option routers 192.178.32.1;
        option broadcast-address 192.178.32.255;
        option domain-name-servers 192.178.0.2, 192.168.122.1;
}
```

Kemudian start DHCP server pada JIPANGU dengan command berikut.

```
service isc-dhcp-server start
```

Pada FOOSHA, WATER7 dan GUANHAO edit pada `/etc/default/isc-dhcp-relay`. Pada bagian servers, ganti dengan IP Jipangu.

```
SERVERS="192.178.0.3"
```

Kemudian restart isc-dhcp-relay tersebut dengan command berikut.

```
service isc-dhcp-relay restart
```

## Soal Shift

### Soal 1

Agar topologi yang kalian buat dapat mengakses keluar, kalian diminta untuk mengkonfigurasi Foosha menggunakan iptables, tetapi Luffy tidak ingin menggunakan MASQUERADE.

#### Penjelasan

Pada FOOSHA kita drop IPTABLES MASQUERADE dengan command berikut. Command berikut akan menghapus seluruh rules yang ada pada NAT.

```
iptables -t nat -F
```

Kemudian agar subnet dapat mengakses internet jalankan command berikut. Dengan `NAT_NET` merupakan variable yang berisi IP Address dari eth0 FOOSHA (yang terhubung dengan internet).

```
NAT_NET=192.168.122.14

# A3: Water7
iptables -t nat -A POSTROUTING -s 192.178.16.0/30 -o eth0 -j SNAT --to-source $NAT_NET

# A5: Guanhao
iptables -t nat -A POSTROUTING -s 192.178.36.0/30 -o eth0 -j SNAT --to-source $NAT_NET

# A1: Dokiri, Jipangu
iptables -t nat -A POSTROUTING -s 192.178.0.0/29 -o eth0 -j SNAT --to-source $NAT_NET

# A8: Jorge, MainGate
iptables -t nat -A POSTROUTING -s 192.178.33.0/29 -o eth0 -j SNAT --to-source $NAT_NET

# A2: BluEno
iptables -t nat -A POSTROUTING -s 192.178.8.0/25 -o eth0 -j SNAT --to-source $NAT_NET

# A4: Cipher
iptables -t nat -A POSTROUTING -s 192.178.4.0/22 -o eth0 -j SNAT --to-source $NAT_NET

# A6: Elena
iptables -t nat -A POSTROUTING -s 192.178.34.0/23 -o eth0 -j SNAT --to-source $NAT_NET

# A7: Fukurou
iptables -t nat -A POSTROUTING -s 192.178.32.0/24 -o eth0 -j SNAT --to-source $NAT_NET
```

Setelah itu dapat dilakukan test ping dari seluruh node yang ada.

- FOOSHA

![image](https://user-images.githubusercontent.com/16128257/145674708-c062e16d-0718-416b-af7a-eaa0b004956b.png)

- GUANHAO

![image](https://user-images.githubusercontent.com/16128257/145674720-43348cd5-374d-4fd4-a184-ae0ef153db5b.png)

- WATER7

![image](https://user-images.githubusercontent.com/16128257/145674803-a65af01b-c735-490f-8712-5b5d67f5f83b.png)

- JIPANGU

![image](https://user-images.githubusercontent.com/16128257/145674835-c4ed12b0-1c87-42cf-842c-ea560f51f411.png)

- DORIKI

![image](https://user-images.githubusercontent.com/16128257/145674862-ae73059e-41b5-4dea-97bc-439f54926c7c.png)

- JORGE

![image](https://user-images.githubusercontent.com/16128257/145674880-dadf6372-e003-48bd-b29b-f2d46dd5e8b4.png)

- MAINGATE

![image](https://user-images.githubusercontent.com/16128257/145674897-94c01b60-abf9-488d-888c-1fa6920dba88.png)

- ELENA

![image](https://user-images.githubusercontent.com/16128257/145675191-daf1ba0b-1085-4a77-a461-df369749de93.png)

- CIPHER

![image](https://user-images.githubusercontent.com/16128257/145675216-b01b10af-b4a0-4c83-96bd-ec4fe261d0d1.png)

- FUKUROU

![image](https://user-images.githubusercontent.com/16128257/145675242-8c33ab7e-e1cf-4b70-9c50-6aca8105e151.png)

- BLUENO

![image](https://user-images.githubusercontent.com/16128257/145675283-3cab8f78-4cff-4333-8e35-760c36654116.png)

### Soal 2

Kalian diminta untuk mendrop semua akses HTTP dari luar Topologi kalian pada server yang merupakan DHCP Server dan DNS Server demi menjaga keamanan.

#### Penjelasan

Jadi begini.

### Soal 3

Karena kelompok kalian maksimal terdiri dari 3 orang. Luffy meminta kalian untuk membatasi DHCP dan DNS Server hanya boleh menerima maksimal 3 koneksi ICMP secara bersamaan menggunakan iptables, selebihnya didrop.

#### Penjelasan

Jadi begini.

### Soal 4

Akses dari subnet Blueno dan Cipher hanya diperbolehkan pada pukul 07.00 - 15.00 pada hari Senin sampai Kamis.

#### Penjelasan

Jadi begini.

### Soal 5

Akses dari subnet Elena dan Fukuro hanya diperbolehkan pada pukul 15.01 hingga pukul 06.59 setiap harinya.

#### Penjelasan

Jadi begini.

### Soal 6

Karena kita memiliki 2 Web Server, Luffy ingin Guanhao disetting sehingga setiap request dari client yang mengakses DNS Server akan didistribusikan secara bergantian pada Jorge dan Maingate

#### Penjelasan

Jadi begini.

## Referensi
- https://qastack.id/raspberrypi/8614/isc-dhcp-server-install-and-run-problem
- https://support.cumulusnetworks.com/hc/en-us/articles/201787526-Configuring-DHCP-Relays
- https://www.karlrupp.net/en/computer/nat_tutorial
- https://ipset.netfilter.org/iptables-extensions.man.html
- https://ipset.netfilter.org/iptables.man.html
