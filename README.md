# Jarkom-Modul-2-E25-2023
Berikut adalah laporan resmi untuk pengerjaan Praktikum Modul 2 Jarkom DNS dan Webserver
## Anggota Kelompok E25
| Nama | NRP |
| --- | --- |
| Zakia Kolbi | 5025211049 |
| Ketut Arda Putra Mahotama Sadha | 5025211235 |

# Daftar Isi
- [Topologi](#topologi)
- [Konfigurasi Network Node](#konfigurasi-network-node)
- [Soal-Soal](#soal-soal)
  - [Soal 1](#soal-1)
    - [Script](#script)
    - [Hasil](#hasil)
  - [Soal 2](#soal-2)
    - [Script](#script-1)
    - [Hasil](#hasil-1)
    


## Topologi
Topologi kelompok kami yaitu topologi 1

![image](https://github.com/arda294/Jarkom-Modul-2-E25-2023/assets/114855785/95bff51c-9add-4549-8feb-93efe08b0939)

## Konfigurasi Network Node
Berdasarkan topologi 1 dan juga Prefix IP untuk kelompok kami yaitu 10.49, Konfigurasi network untuk masing masing node adalah sebagai berikut :
- Pandudewanata (Sebagai router)
  ```
  auto eth0
  iface eth0 inet dhcp
  
  auto eth1
  iface eth1 inet static
  	address 10.49.1.1
  	netmask 255.255.255.0
  
  auto eth2
  iface eth2 inet static
  	address 10.49.2.1
  	netmask 255.255.255.0
  
  auto eth3
  iface eth3 inet static
  	address 10.49.3.1
  	netmask 255.255.255.0
  ```
- Yudhistira
  ```
  auto eth0
  iface eth0 inet static
  	address 10.49.1.2
  	netmask 255.255.255.0
  	gateway 10.49.1.1
  ```
- Nakula
  ```
  auto eth0
  iface eth0 inet static
  	address 10.49.1.3
  	netmask 255.255.255.0
  	gateway 10.49.1.1
  ```
- Werkudara
  ```
  auto eth0
  iface eth0 inet static
  	address 10.49.2.2
  	netmask 255.255.255.0
  	gateway 10.49.2.1
  ```
- Sadewa
  ```
  auto eth0
  iface eth0 inet static
  	address 10.49.2.3
  	netmask 255.255.255.0
  	gateway 10.49.2.1
  ```
- Arjuna
  ```
  auto eth0
  iface eth0 inet static
  	address 10.49.3.2
  	netmask 255.255.255.0
  	gateway 10.49.3.1
  ```
- Prabukusuma
  ```
  auto eth0
  iface eth0 inet static
  	address 10.49.3.3
  	netmask 255.255.255.0
  	gateway 10.49.3.1
  ```
- Abimanyu
  ```
  auto eth0
  iface eth0 inet static
  	address 10.49.3.4
  	netmask 255.255.255.0
  	gateway 10.49.3.1
  ```
- Wisanggeni
  ```
  auto eth0
  iface eth0 inet static
  	address 10.49.3.5
  	netmask 255.255.255.0
  	gateway 10.49.3.1
  ```

Setelah itu, sebagai persiapan untuk mengerjakan tiap soal, setiap node akan diberi script yang menginstall ``dnsutils`` dan ``lynx`` sebagai berikut :

```
apt-get -y install dnsutils
echo 'nameserver 10.49.1.2
nameserver 10.49.2.2
nameserver 192.168.122.1' > /etc/resolv.conf
apt-get -y install lynx
```

Script diatas akan disimpan ke dalam file ``resolv.sh`` yang nantinya akan dijalankan dalam ``.bashrc``. Fungsi dari script diatas selain untuk menginstall ``dnsutils`` dan ``lynx`` yaitu untuk menambahkan kedua nameserver yudhistira (10.49.1.2) dan wekudara (10.49.2.2)

Sebagai tambahan untuk pandudewanata sebagai router, yaitu :

```
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE -s 10.49.0.0/16
echo 'nameserver 192.168.122.1' > /etc/resolv.conf
```

Hasilnya adalah setiap node bisa melakukan ping satu sama lain, dan juga bisa mengakses internet.

![image](https://github.com/arda294/Jarkom-Modul-2-E25-2023/assets/114855785/af07f6f2-7a21-44b7-b6de-d85f887fbf87)

## Soal-Soal
### Soal 1
> Yudhistira akan digunakan sebagai DNS Master, Werkudara sebagai DNS Slave, Arjuna merupakan Load Balancer yang terdiri dari beberapa Web Server yaitu Prabakusuma, Abimanyu, dan Wisanggeni. Buatlah topologi dengan pembagian sebagai berikut. Folder topologi dapat diakses pada drive berikut

Untuk soal ini sudah dijelaskan pada bagian [Topologi](#topologi)
#### Script
#### Hasil
### Soal 2
#### Script
#### Hasil
