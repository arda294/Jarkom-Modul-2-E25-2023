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
    - [Script](#script-2)
    - [Hasil](#hasil-2)
  - [Soal 3](#soal-3)
    - [Script](#script-3)
    - [Hasil](#hasil-3)
  - [Soal 4](#soal-4)
    - [Script](#script-4)
    - [Hasil](#hasil-4)
  - [Soal 5](#soal-5)
    - [Script](#script-5)
    - [Hasil](#hasil-5)
  - [Soal 6](#soal-6)
    - [Script](#script-6)
    - [Hasil](#hasil-6)
  - [Soal 7](#soal-7)
    - [Script](#script-7)
    - [Hasil](#hasil-7)
  - [Soal 8](#soal-8)
    - [Script](#script-8)
    - [Hasil](#hasil-8)
  - [Soal 9](#soal-9)
    - [Script](#script-9)
    - [Hasil](#hasil-9)
  - [Soal 10](#soal-10)
    - [Script](#script-10)
    - [Hasil](#hasil-10)
  - [Soal 11](#soal-11)
    - [Script](#script-11)
    - [Result](#hasil-11)
  - [Soal 12](#soal-12)
    - [Script](#script-12)
    - [Result](#hasil-12)
  - [Soal 13](#soal-13)
    - [Script](#script-13)
    - [Result](#hasil-13)
  - [Soal 14](#soal-14)
    - [Script](#script-14)
    - [Result](#hasil-14)
  - [Soal 15](#soal-15)
    - [Script](#script-15)
    - [Result](#hasil-15)
  - [Soal 16](#soal-16)
    - [Script](#script-16)
    - [Result](#hasil-16)
  - [Soal 17](#soal-17)
    - [Script](#script-17)
    - [Result](#hasil-17)
  - [Soal 18](#soal-18)
    - [Script](#script-18)
    - [Result](#hasil-18)
  - [Soal 19](#soal-19)
    - [Script](#script-19)
    - [Result](#hasil-19)
  - [Soal 20](#soal-20)
    - [Script](#script-20)
    - [Result](#hasil-20)

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
> 
#### Script
Untuk soal ini sudah dijelaskan pada bagian [Topologi](#topologi).
#### Hasil
Bisa dilihat pada [Topologi](#topologi).
### Soal 2
> Buatlah website utama pada node arjuna dengan akses ke arjuna.yyy.com dengan alias www.arjuna.yyy.com dengan yyy merupakan kode kelompok.

Untuk melakukan ini akan dilakukan setup DNS pada Yudhistira
#### Script
```
apt-get install bind9 -y

echo 'zone "arjuna.e25.com" {
    type master;
    file "/etc/bind/jarkom/arjuna.e25.com";
};' > /etc/bind/named.conf.local


mkdir /etc/bind/jarkom

echo ';
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     arjuna.e25.com. root.arjuna.e25.com. (
                              2         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@                       IN      NS      arjuna.e25.com.
@                       IN      A       10.49.3.2
www                     IN      CNAME   arjuna.e25.com.
@                       IN      AAAA    ::1' > /etc/bind/jarkom/arjuna.e25.com

service bind9 restart
```

script diatas disimpan didalam file ``domain.sh`` yang akan di jalankan dalam ``.bashrc``
#### Hasil
Sadewa melakukan ping terhadap arjuna.e25.com yang pointing ke ip node arjuna (10.49.3.2)

![image](https://github.com/arda294/Jarkom-Modul-2-E25-2023/assets/114855785/1bd4b44f-3efe-48c0-8854-e960b7f5b1f9)
### Soal 3
> Dengan cara yang sama seperti soal nomor 2, buatlah website utama dengan akses ke abimanyu.yyy.com dan alias www.abimanyu.yyy.com.

Untuk soal ini, hanya perlu menambahkan zone baru pada script pada [Soal 1](#soal-1)
#### Script
```
apt-get install bind9 -y

echo 'zone "arjuna.e25.com" {
    type master;
    file "/etc/bind/jarkom/arjuna.e25.com";
};

zone "abimanyu.e25.com" {
    type master;
    file "/etc/bind/jarkom/abimanyu.e25.com";
};' > /etc/bind/named.conf.local

mkdir /etc/bind/jarkom

echo ';
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     abimanyu.e25.com. root.abimanyu.e25.com. (
                              2         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@                       IN      NS      abimanyu.e25.com.
@                       IN      A       10.49.3.4
www                     IN      CNAME   abimanyu.e25.com.
@                       IN      AAAA    ::1' > /etc/bind/jarkom/abimanyu.e25.com

service bind9 restart
```

Script diatas menambahkan zone untuk domain ``abimanyu.e25.com`` yang pointing ke node abimanyu (10.49.3.4)
#### Hasil
Sadewa melakukan ping terhadap ``abimanyu.e25.com``

![image](https://github.com/arda294/Jarkom-Modul-2-E25-2023/assets/114855785/1a7525c9-f5f0-4b94-b21a-5a3477be1a79)


### Soal 4
> Kemudian, karena terdapat beberapa web yang harus di-deploy, buatlah subdomain parikesit.abimanyu.yyy.com yang diatur DNS-nya di Yudhistira dan mengarah ke Abimanyu.

Hal ini dilakukan dengan menambahkan subdomain parikesit pada zone abimanyu.e25.com
#### Script
```
echo ';
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     abimanyu.e25.com. root.abimanyu.e25.com. (
                              2         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@                       IN      NS      abimanyu.e25.com.
@                       IN      A       10.49.3.4
www                     IN      CNAME   abimanyu.e25.com.
parikesit               IN      A       10.49.3.4
www.parikesit           IN      CNAME   parikesit.abimanyu.e25.com.
@                       IN      AAAA    ::1' > /etc/bind/jarkom/abimanyu.e25.com

service bind9 restart
```

Dapat dilihat ``parikesit.abimanyu.e25.com`` juga pointing ke node abimanyu (10.49.3.4)
#### Hasil
Sadewa melakukan ping terhadap ``parikesit.abimanyu.e25.com``

![image](https://github.com/arda294/Jarkom-Modul-2-E25-2023/assets/114855785/e3cea893-c466-4612-8d93-ec2c0a034e90)
### Soal 5
> Buat juga reverse domain untuk domain utama.

Untuk ini, perlu disiapkan zone khusus untuk menyimpan PTR record
#### Script
```
echo 'zone "arjuna.e25.com" {
    type master;
    file "/etc/bind/jarkom/arjuna.e25.com";
};

zone "abimanyu.e25.com" {
    type master;
    file "/etc/bind/jarkom/abimanyu.e25.com";
};

zone "3.49.10.in-addr.arpa" {
    type master;
    file "/etc/bind/jarkom/3.49.10.in-addr.arpa";
};' > /etc/bind/named.conf.local

echo ';
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     arjuna.e25.com. root.arjuna.e25.com. (
                              2         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
3.49.10.in-addr.arpa.   IN      NS      arjuna.e25.com.
2                       IN      PTR     arjuna.e25.com.
4                       IN      PTR     abimanyu.e25.com.' > /etc/bind/jarkom/3.49.10.in-addr.arpa

service bind9 restart
```

Script diatas akan menambahkan zone ``3.49.10.in-addr.arpa`` yang akan menyimpan PTR record untuk ``arjuna.e25.com`` dan ``abimanyu.e25.com``
#### Hasil
Sadewa menjalankan command untuk mencari hostname ip node abimanyu (10.49.3.4)

![image](https://github.com/arda294/Jarkom-Modul-2-E25-2023/assets/114855785/d8ab0038-5ffc-45ca-8a08-abbf0ed0e67f)

### Soal 6
> Agar dapat tetap dihubungi ketika DNS Server Yudhistira bermasalah, buat juga Werkudara sebagai DNS Slave untuk domain utama.

Untuk soal ini, perlu ditambahkan beberapa line yang akan allow transfer dns zone dari yudhistira (master) ke werkudara (slave). Selain itu juga, ditambahkan konfigurasi zone sebagai slave pada werkudara
#### Script
Pada yudhistira :

```
echo 'zone "arjuna.e25.com" {
    type master;
    notify yes;
    also-notify { 10.49.2.2; }; // IP Werkudara
    allow-transfer { 10.49.2.2; };
    file "/etc/bind/jarkom/arjuna.e25.com";
};

zone "abimanyu.e25.com" {
    type master;
    notify yes;
    also-notify { 10.49.2.2; }; // IP Werkudara
    allow-transfer { 10.49.2.2; };
    file "/etc/bind/jarkom/abimanyu.e25.com";
};

zone "3.49.10.in-addr.arpa" {
    type master;
    notify yes;
    also-notify { 10.49.2.2; }; // IP Werkudara
    allow-transfer { 10.49.2.2; };
    file "/etc/bind/jarkom/3.49.10.in-addr.arpa";
};' > /etc/bind/named.conf.local
```

Pada werkudara :

```
apt-get install bind9 -y

mkdir /etc/bind/baratayuda

echo 'zone "arjuna.e25.com" {
    type slave;
    masters { 10.49.1.2; }; // IP Yudhistira
    file "/var/lib/bind/arjuna.e25.com";
};

zone "abimanyu.e25.com" {
    type slave;
    masters { 10.49.1.2; }; // IP Yudhistira
    file "/etc/bind/abimanyu.e25.com";
};

zone "3.49.10.in-addr.arpa" {
    type slave;
    masters { 10.49.1.2; }; // IP Yudhistira
    file "/etc/bind/3.49.10.in-addr.arpa";
};' > /etc/bind/named.conf.local
```

Pada zone-zone yang ada di yudhistira akan ditambahkan ip yudhistira sebagai master untuk zone tersebut.

#### Hasil
Sadewa melakukan ping terhadap ``arjuna.e25.com`` dan ``abimanyu.e25.com`` dengan node ``yudhistira`` sedang down.

![image](https://github.com/arda294/Jarkom-Modul-2-E25-2023/assets/114855785/a3a7e2d6-0fdd-45cd-87f0-f9bcc592449a)

Sadewa melakukan resolve host dari ip ``arjuna`` dan ``abimanyu``

![image](https://github.com/arda294/Jarkom-Modul-2-E25-2023/assets/114855785/58a7d5f9-1ca9-431f-83f0-0dbb9f411abd)

Bisa dilihat attempt pertama gagal karena node ``yudhistira`` sedang down, dan beralih ke slave pada ``werkudara``
### Soal 7
> Seperti yang kita tahu karena banyak sekali informasi yang harus diterima, buatlah subdomain khusus untuk perang yaitu baratayuda.abimanyu.yyy.com dengan alias www.baratayuda.abimanyu.yyy.com yang didelegasikan dari Yudhistira ke Werkudara dengan IP menuju ke Abimanyu dalam folder Baratayuda.

Untuk melakukan ini, perlu membuat NS record yang pointing ke ip ``werkudara`` sebagai delegasi dan juga setup zone pada node ``werkudara`` untuk zone yang didelegasikan. Selain itu juga, pada kedua DNS server, perlu mengubah ``named.conf.options`` agar dapat melakukan query pada nameserver yang didelegasikan.
#### Script
Pada yudhistira :
```
echo ';
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     abimanyu.e25.com. root.abimanyu.e25.com. (
                              2         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@                       IN      NS      abimanyu.e25.com.
@                       IN      A       10.49.3.4
www                     IN      CNAME   abimanyu.e25.com.
parikesit               IN      A       10.49.3.4
www.parikesit           IN      CNAME   parikesit.abimanyu.e25.com.
baratayuda              IN      NS      ns1.abimanyu.e25.com.
ns1                     IN      A       10.49.2.2
@                       IN      AAAA    ::1' > /etc/bind/jarkom/abimanyu.e25.com

echo "options {
        directory \"/var/cache/bind\";

        // If there is a firewall between you and nameservers you want
        // to talk to, you may need to fix the firewall to allow multiple
        // ports to talk.  See http://www.kb.cert.org/vuls/id/800113

        // If your ISP provided one or more IP addresses for stable
        // nameservers, you probably want to use them as forwarders.
        // Uncomment the following block, and insert the addresses replacing
        // the all-0's placeholder.

        // forwarders {
        //      0.0.0.0;
        // };

        //========================================================================
        // If BIND logs error messages about the root key being expired,
        // you will need to update your keys.  See https://www.isc.org/bind-keys
        //========================================================================
        //dnssec-validation auto;
        allow-query{any;};

        listen-on-v6 { any; };
};" > /etc/bind/named.conf.options

service bind9 restart
```

Script menambahkan NS record menuju werkudara untuk subdomain baratayuda

Pada werkudara :
```
mkdir /etc/bind/baratayuda

echo 'zone "arjuna.e25.com" {
    type slave;
    masters { 10.49.1.2; }; // IP Yudhistira
    file "/var/lib/bind/arjuna.e25.com";
};

zone "abimanyu.e25.com" {
    type slave;
    masters { 10.49.1.2; }; // IP Yudhistira
    file "/etc/bind/abimanyu.e25.com";
};

zone "baratayuda.abimanyu.e25.com" {
    type master;
    file "/etc/bind/baratayuda/baratayuda.abimanyu.e25.com";
};

zone "3.49.10.in-addr.arpa" {
    type slave;
    masters { 10.49.1.2; }; // IP Yudhistira
    file "/etc/bind/3.49.10.in-addr.arpa";
};' > /etc/bind/named.conf.local

echo ';
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     baratayuda.abimanyu.e25.com. root.baratayuda.abimanyu.e25.com. (
                              2         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@                       IN      NS      baratayuda.abimanyu.e25.com.
@                       IN      A       10.49.3.4
www                     IN      CNAME   baratayuda.abimanyu.e25.com.
@                       IN      AAAA    ::1' > /etc/bind/baratayuda/baratayuda.abimanyu.e25.com

echo "options {
        directory \"/var/cache/bind\";

        // If there is a firewall between you and nameservers you want
        // to talk to, you may need to fix the firewall to allow multiple
        // ports to talk.  See http://www.kb.cert.org/vuls/id/800113

        // If your ISP provided one or more IP addresses for stable
        // nameservers, you probably want to use them as forwarders.
        // Uncomment the following block, and insert the addresses replacing
        // the all-0's placeholder.

        // forwarders {
        //      0.0.0.0;
        // };

        //========================================================================
        // If BIND logs error messages about the root key being expired,
        // you will need to update your keys.  See https://www.isc.org/bind-keys
        //========================================================================
        //dnssec-validation auto;
        allow-query{any;};

        listen-on-v6 { any; };
};" > /etc/bind/named.conf.options

service bind9 restart
```

Script diatas menambahkan zone ``baratayuda.abimanyu.e25.com`` pada ``wekudara``.
#### Hasil
Sadewa melakukan ping terhadap ``baratayuda.abimanyu.e25.com``

![image](https://github.com/arda294/Jarkom-Modul-2-E25-2023/assets/114855785/5c7f8282-13d7-4946-9e83-475ec94efdfc)

### Soal 8
> Untuk informasi yang lebih spesifik mengenai Ranjapan Baratayuda, buatlah subdomain melalui Werkudara dengan akses rjp.baratayuda.abimanyu.yyy.com dengan alias www.rjp.baratayuda.abimanyu.yyy.com yang mengarah ke Abimanyu.

Untuk soal ini, hanya perlu menambahkan subdomain rjp pada zone ``baratayuda.abimanyu.e25.com`` di dalam ``werkudara``
#### Script
```
echo ';
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     baratayuda.abimanyu.e25.com. root.baratayuda.abimanyu.e25.com. (
                              2         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@                       IN      NS      baratayuda.abimanyu.e25.com.
@                       IN      A       10.49.3.4
www                     IN      CNAME   baratayuda.abimanyu.e25.com.
rjp                     IN      A       10.49.3.4
www.rjp                 IN      CNAME   rjp.baratayuda.abimanyu.e25.com.
@                       IN      AAAA    ::1' > /etc/bind/baratayuda/baratayuda.abimanyu.e25.com

service bind9 restart
```

Script diatas menambahkan subdomain rjp dalam zone ``baratayuda.abimanyu.e25.com``
#### Hasil
Sadewa melakukan ping terhadap ``rjp.baratayuda.e25.com``

![image](https://github.com/arda294/Jarkom-Modul-2-E25-2023/assets/114855785/b8c9b7db-570b-4ff0-97ce-9d81d844b9cd)

### Soal 9
> Arjuna merupakan suatu Load Balancer Nginx dengan tiga worker (yang juga menggunakan nginx sebagai webserver) yaitu Prabakusuma, Abimanyu, dan Wisanggeni. Lakukan deployment pada masing-masing worker.

Soal ini memerlukan setup Nginx pada ``arjuna`` sebagai load balancer dan juga pada ``prabukusuma``, ``abimanyu``, dan ``wisanggeni`` sebagai worker node yang akan host website.
#### Script
Akan dilanjutkan pada [Soal 10](#soal-10)
#### Hasil
Akan dilanjutkan pada [Soal 10](#soal-10)
### Soal 10
> Kemudian gunakan algoritma Round Robin untuk Load Balancer pada Arjuna. Gunakan server_name pada soal nomor 1. Untuk melakukan pengecekan akses alamat web tersebut kemudian pastikan worker yang digunakan untuk menangani permintaan akan berganti ganti secara acak. Untuk webserver di masing-masing worker wajib berjalan di port 8001-8003. Contoh

Prabakusuma:8001

Abimanyu:8002

Wisanggeni:8003

Lanjutan dari soal 9, config nginx yang listen pada port sesuai diatas untuk masing-masing node.
#### Script
Pada arjuna :
```
apt-get install bind9 nginx -y

echo ' # Default menggunakan Round Robin
 upstream myweb  {
 	server 10.49.3.3:8001; #IP Prabukusuma
 	server 10.49.3.4:8002; #IP Abimanyu
    server 10.49.3.5:8003; #IP Wisanggeni
 }

 server {
 	listen 80;
 	server_name arjuna.e25.com www.arjuna.e25.com;

 	location / {
 	proxy_pass http://myweb;
 	}
 }' > /etc/nginx/sites-available/lb-jarkom

ln -s /etc/nginx/sites-available/lb-jarkom /etc/nginx/sites-enabled/lb-jarkom

# rm /etc/nginx/sites-enabled/default

service nginx restart
```

Script diatas akan setup load balancer nginx menggunakan round robin (secara default) pada arjuna

Pada masing-masing worker node :
```
apt install nginx php php-fpm -y

mkdir /var/www/jarkom

echo " <?php
\$hostname = gethostname();
\$date = date('Y-m-d H:i:s');
\$php_version = phpversion();
\$username = get_current_user();



echo \"Hello World!<br\>\";
echo \"Saya adalah: \$username<br\>\";
echo \"Saat ini berada di: \$hostname<br\>\";
echo \"Versi PHP yang saya gunakan: \$php_version<br\>\";
echo \"Tanggal saat ini: \$date<b\r\>\";
?>" > /var/www/jarkom/index.php

echo '
 server {

 	listen [port untuk node masing-masing];

 	root /var/www/jarkom;

 	index index.php index.html index.htm;
 	server_name _;

 	location / {
 			try_files $uri $uri/ /index.php?$query_string;
 	}

 	# pass PHP scripts to FastCGI server
 	location ~ \.php$ {
 	include snippets/fastcgi-php.conf;
 	fastcgi_pass unix:/var/run/php/php7.0-fpm.sock;
 	}

    location ~ /\.ht {
 			deny all;
 	}

 	error_log /var/log/nginx/jarkom_error.log;
 	access_log /var/log/nginx/jarkom_access.log;
 }
' > /etc/nginx/sites-available/jarkom

ln -s /etc/nginx/sites-available/jarkom /etc/nginx/sites-enabled/jarkom
rm /etc/nginx/sites-enabled/default

service nginx restart
service php7.0-fpm stop
service php7.0-fpm start
```

Script diatas akan setup config nginx untuk listen pada port masing-masing sesuai soal untuk tiap worker node. Untuk image docker yang digunakan pada praktikum ini, menggunakan versi php 7.0 sehingga php-fpm yang digunakan juga 7.0.

Script diatas disimpan dalam file ``nginx.conf`` yang akan dijalankan pada ``.bashrc``
#### Hasil
Sadewa mencoba mengakses ``arjuna.e25.com`` menggunakan ``lynx``

![image](https://github.com/arda294/Jarkom-Modul-2-E25-2023/assets/114855785/4443f5f2-28fd-4749-8520-7e93f92410e6)

Ketika dijalankan lagi, akan host akan berubah-ubah sesuai urutan (round robin)

### Soal 11
> Selain menggunakan Nginx, lakukan konfigurasi Apache Web Server pada worker Abimanyu dengan web server www.abimanyu.yyy.com. Pertama dibutuhkan web server dengan DocumentRoot pada /var/www/abimanyu.yyy

Pertama kita perlu melakukan ``Setup`` kemudian kita juga perlu Menggunakan ``Server Alias`` agar bisa melakukan ``www`` nantinya.

#### Script
#### Abimanyu
```
echo "<VirtualHost *:80>
        # The ServerName directive sets the request scheme, hostname and port that
        # the server uses to identify itself. This is used when creating
        # redirection URLs. In the context of virtual hosts, the ServerName
        # specifies what hostname must appear in the request's Host: header to
        # match this virtual host. For the default virtual host (this file) this
        # value is not decisive as it is used as a last resort host regardless.
        # However, you must set it for any further virtual host explicitly.
        #ServerName www.example.com

        ServerName abimanyu.e25.com
        ServerAlias www.abimanyu.e25.com

        ServerAdmin webmaster@localhost
        DocumentRoot /var/www/abimanyu.e25

        # Available loglevels: trace8, ..., trace1, debug, info, notice, warn,
        # error, crit, alert, emerg.
        # It is also possible to configure the loglevel for particular
        # modules, e.g.
        #LogLevel info ssl:warn

        <Directory /var/www/abimanyu.e25>
            Options +FollowSymLinks -Multiviews
            AllowOverride All
        </Directory>

        ErrorLog \${APACHE_LOG_DIR}/error.log
        CustomLog \${APACHE_LOG_DIR}/access.log combined

        # For most configuration files from conf-available/, which are
        # enabled or disabled at a global level, it is possible to
        # include a line for only one particular virtual host. For example the
        # following line enables the CGI configuration for this host only
        # after it has been globally disabled with "a2disconf".
        #Include conf-available/serve-cgi-bin.conf
</VirtualHost>" > /etc/apache2/sites-available/abimanyu.e25.com.conf

a2ensite abimanyu.e25.com.conf

service apache2 restart
```

##### Setup
```
wget -O '/var/www/abimanyu.e25.com' 'https://drive.usercontent.google.com/download?id=1a4V23hwK9S7hQEDEcv9FL14UkkrHc-Zc'
unzip -o /var/www/abimanyu.e25.com -d /var/www/
mv /var/www/abimanyu.yyy.com /var/www/abimanyu.e25
rm /var/www/abimanyu.e25.com
rm -rf /var/www/abimanyu.yyy.com
```

##### Sadewa
```
lynx abimanyu.e25.com
```

#### Hasil
![Screenshot_42](https://github.com/arda294/Jarkom-Modul-2-E25-2023/assets/108173647/ce526751-a769-4ed2-a7ae-117bdc0419f4)

### Soal 12
> Setelah itu ubahlah agar url www.abimanyu.yyy.com/index.php/home menjadi www.abimanyu.yyy.com/home.

Disini kita akan melakukan rewrite index, agar dapat mengakses ``/home``

#### Script
#### Abimanyu
```
<Directory /var/www/abimanyu.e25>
            Options +FollowSymLinks -Multiviews
            AllowOverride All
        </Directory>
```
```
echo 'RewriteEngine On
RewriteCond %{REQUEST_FILENAME} !-d
RewriteCond %{REQUEST_FILENAME} !-f
RewriteRule ^(home)+$ index.php/$1 [NC,L]
' > /var/www/abimanyu.e25/.htaccess
```

##### Sadewa
``` 
lynx abimanyu.e25.com/home
```

#### Hasil
![Screenshot_43](https://github.com/arda294/Jarkom-Modul-2-E25-2023/assets/108173647/1e7f08ab-8508-4452-bc7a-255cd2328097)

### Soal 13
> Selain itu, pada subdomain www.parikesit.abimanyu.yyy.com, DocumentRoot disimpan pada /var/www/parikesit.abimanyu.yyy

Pertama kita perlu melakukan ``setup``. Kemudian membuat ``Name Server`` dan ``Server Alias``

#### Script
#### Abimanyu
```
echo "<VirtualHost *:80>
        # The ServerName directive sets the request scheme, hostname and port that
        # the server uses to identify itself. This is used when creating
        # redirection URLs. In the context of virtual hosts, the ServerName
        # specifies what hostname must appear in the request's Host: header to
        # match this virtual host. For the default virtual host (this file) this
        # value is not decisive as it is used as a last resort host regardless.
        # However, you must set it for any further virtual host explicitly.
        #ServerName www.example.com

        ServerName parikesit.abimanyu.e25.com
        ServerAlias www.parikesit.abimanyu.e25.com

        ServerAdmin webmaster@localhost
        DocumentRoot /var/www/parikesit.abimanyu.e25

        ErrorLog \${APACHE_LOG_DIR}/error.log
        CustomLog \${APACHE_LOG_DIR}/access.log combined

        # For most configuration files from conf-available/, which are
        # enabled or disabled at a global level, it is possible to
        # include a line for only one particular virtual host. For example the
        # following line enables the CGI configuration for this host only
        # after it has been globally disabled with "a2disconf".
        #Include conf-available/serve-cgi-bin.conf
</VirtualHost>" > /etc/apache2/sites-available/parikesit.abimanyu.e25.com.conf

a2ensite parikesit.abimanyu.e25.com.conf

service apache2 restart
```

##### Setup
```
wget -O '/var/www/parikesit.abimanyu.e25.com' 'https://drive.usercontent.google.com/download?id=1LdbYntiYVF_NVNgJis1GLCLPEGyIOreS'
unzip -o /var/www/parikesit.abimanyu.e25.com -d /var/www/
mv /var/www/parikesit.abimanyu.yyy.com /var/www/parikesit.abimanyu.e25
rm /var/www/parikesit.abimanyu.e25.com
rm -rf /var/www/parikesit.abimanyu.yyy.com
mkdir /var/www/parikesit.abimanyu.e25/secret
```

#### Sadewa
```
lynx parikesit.abimanyu.e25.com
lynx www.parikesit.abimanyu.e25.com
```

#### Hasil
![Screenshot_44](https://github.com/arda294/Jarkom-Modul-2-E25-2023/assets/108173647/11dc8092-6e8e-4e1c-a989-dbe392411e7d)

### Soal 14
> Pada subdomain tersebut folder /public hanya dapat melakukan directory listing sedangkan pada folder /secret tidak dapat diakses (403 Forbidden).

Karena kita mau mengizinkan public agar dapat melakukan directory listing kita menggunakan Options +Indexes. Sedangkan agar suatu folder tidak dapat di akses, kita dapat menggunakan Option -Indexes.

#### Script
#### Abimanyu
```
echo "<VirtualHost *:80>
        # The ServerName directive sets the request scheme, hostname and port that
        # the server uses to identify itself. This is used when creating
        # redirection URLs. In the context of virtual hosts, the ServerName
        # specifies what hostname must appear in the request's Host: header to
        # match this virtual host. For the default virtual host (this file) this
        # value is not decisive as it is used as a last resort host regardless.
        # However, you must set it for any further virtual host explicitly.
        #ServerName www.example.com

        ServerName parikesit.abimanyu.e25.com
        ServerAlias www.parikesit.abimanyu.e25.com

        ServerAdmin webmaster@localhost
        DocumentRoot /var/www/parikesit.abimanyu.e25

        # Available loglevels: trace8, ..., trace1, debug, info, notice, warn,
        # error, crit, alert, emerg.
        # It is also possible to configure the loglevel for particular
        # modules, e.g.
        #LogLevel info ssl:warn

        <Directory /var/www/parikesit.abimanyu.e25/public>
            Options +Indexes
        </Directory>

        <Directory /var/www/parikesit.abimanyu.e25/secret>
            Options -Indexes
        </Directory>

        ErrorLog \${APACHE_LOG_DIR}/error.log
        CustomLog \${APACHE_LOG_DIR}/access.log combined

        # For most configuration files from conf-available/, which are
        # enabled or disabled at a global level, it is possible to
        # include a line for only one particular virtual host. For example the
        # following line enables the CGI configuration for this host only
        # after it has been globally disabled with "a2disconf".
        #Include conf-available/serve-cgi-bin.conf
</VirtualHost>" > /etc/apache2/sites-available/parikesit.abimanyu.e25.com.conf

service apache2 restart
```

#### Sadewa
```
lynx parikesit.abimanyu.e25.com/public
lynx parikesit.abimanyu.e25.com/secret
```

#### Hasil
##### Public
![Screenshot_45](https://github.com/arda294/Jarkom-Modul-2-E25-2023/assets/108173647/bb8fae02-56e0-4a31-92ae-a44b46bd03a2)

##### Secret
![Screenshot_46](https://github.com/arda294/Jarkom-Modul-2-E25-2023/assets/108173647/521fb753-3198-44ff-9792-076c37894fae)
![Screenshot_61](https://github.com/arda294/Jarkom-Modul-2-E25-2023/assets/108173647/c6c0dd0c-ac9d-40fe-886e-afde2a14913e)

### Soal 15
> Buatlah kustomisasi halaman error pada folder /error untuk mengganti error kode pada Apache. Error kode yang perlu diganti adalah 404 Not Found dan 403 Forbidden.

#### Script
#### Abimanyu
```
echo "<VirtualHost *:80>
        # The ServerName directive sets the request scheme, hostname and port that
        # the server uses to identify itself. This is used when creating
        # redirection URLs. In the context of virtual hosts, the ServerName
        # specifies what hostname must appear in the request's Host: header to
        # match this virtual host. For the default virtual host (this file) this
        # value is not decisive as it is used as a last resort host regardless.
        # However, you must set it for any further virtual host explicitly.
        #ServerName www.example.com

        ServerName parikesit.abimanyu.e25.com
        ServerAlias www.parikesit.abimanyu.e25.com

        ServerAdmin webmaster@localhost
        DocumentRoot /var/www/parikesit.abimanyu.e25

        # Available loglevels: trace8, ..., trace1, debug, info, notice, warn,
        # error, crit, alert, emerg.
        # It is also possible to configure the loglevel for particular
        # modules, e.g.
        #LogLevel info ssl:warn

        <Directory /var/www/parikesit.abimanyu.e25/public>
            Options +Indexes
        </Directory>

        <Directory /var/www/parikesit.abimanyu.e25/secret>
            Options -Indexes
        </Directory>

        ErrorDocument 404 /error/404.html
        ErrorDocument 403 /error/403.html

        ErrorLog \${APACHE_LOG_DIR}/error.log
        CustomLog \${APACHE_LOG_DIR}/access.log combined

        # For most configuration files from conf-available/, which are
        # enabled or disabled at a global level, it is possible to
        # include a line for only one particular virtual host. For example the
        # following line enables the CGI configuration for this host only
        # after it has been globally disabled with "a2disconf".
        #Include conf-available/serve-cgi-bin.conf
</VirtualHost>" > /etc/apache2/sites-available/parikesit.abimanyu.e25.com.conf

service apache2 restart
```

#### Sadewa
```
lynx parikesit.abimanyu.e25.com/testerror
lynx parikesit.abimanyu.e25.com/secret
```

#### Hasil
##### Error
![Screenshot_48](https://github.com/arda294/Jarkom-Modul-2-E25-2023/assets/108173647/e01efea0-0db2-4d44-94ce-ed65e3ffc22c)
![Screenshot_49](https://github.com/arda294/Jarkom-Modul-2-E25-2023/assets/108173647/40f6f965-264f-427d-9f1f-86560578ad8d)

##### Forbidden
![Screenshot_50](https://github.com/arda294/Jarkom-Modul-2-E25-2023/assets/108173647/1da26c8b-1337-4f20-9541-aa8d22b2a81e)
![Screenshot_51](https://github.com/arda294/Jarkom-Modul-2-E25-2023/assets/108173647/7c026180-cbbf-4ed7-be1e-370edb07e64e)

### Soal 16
> Buatlah suatu konfigurasi virtual host agar file asset www.parikesit.abimanyu.yyy.com/public/js menjadi 
www.parikesit.abimanyu.yyy.com/js 

Disini kita hanya perlu menggunakan Alias ``"/js"`` ``"/var/www/parikesit.abimanyu.a09/public/js"`` untuk mengubah virtual host agar file tersebut menjadi lebih singkat. Disini kami juga menggunakan ``ServerName`` dan ``ServerAlias`` agar virtual host dapat berjalan.

#### Script
#### Abimanyu
```
echo "<VirtualHost *:80>
        # The ServerName directive sets the request scheme, hostname and port that
        # the server uses to identify itself. This is used when creating
        # redirection URLs. In the context of virtual hosts, the ServerName
        # specifies what hostname must appear in the request's Host: header to
        # match this virtual host. For the default virtual host (this file) this
        # value is not decisive as it is used as a last resort host regardless.
        # However, you must set it for any further virtual host explicitly.
        #ServerName www.example.com

        ServerName parikesit.abimanyu.e25.com
        ServerAlias www.parikesit.abimanyu.e25.com

        ServerAdmin webmaster@localhost
        DocumentRoot /var/www/parikesit.abimanyu.e25

        # Available loglevels: trace8, ..., trace1, debug, info, notice, warn,
        # error, crit, alert, emerg.
        # It is also possible to configure the loglevel for particular
        # modules, e.g.
        #LogLevel info ssl:warn

        <Directory /var/www/parikesit.abimanyu.e25/public>
            Options +Indexes
        </Directory>

        <Directory /var/www/parikesit.abimanyu.e25/secret>
            Options -Indexes
        </Directory>

        <Directory /var/www/parikesit.abimanyu.e25/public/js>
            Options +Indexes
        </Directory>

        Alias "/js" "/var/www/parikesit.abimanyu.e25/public/js"

        ErrorDocument 404 /error/404.html
        ErrorDocument 403 /error/403.html

        ErrorLog \${APACHE_LOG_DIR}/error.log
        CustomLog \${APACHE_LOG_DIR}/access.log combined

        # For most configuration files from conf-available/, which are
        # enabled or disabled at a global level, it is possible to
        # include a line for only one particular virtual host. For example the
        # following line enables the CGI configuration for this host only
        # after it has been globally disabled with "a2disconf".
        #Include conf-available/serve-cgi-bin.conf
</VirtualHost>" > /etc/apache2/sites-available/parikesit.abimanyu.e25.com.conf

service apache2 restart
```

#### Sadewa
```
lynx parikesit.abimanyu.e25.com/js
```

#### Hasil
![Screenshot_52](https://github.com/arda294/Jarkom-Modul-2-E25-2023/assets/108173647/1c8623c0-4e68-48f4-b243-a5a782d2cb0c)

### Soal 17
> Agar aman, buatlah konfigurasi agar www.rjp.baratayuda.abimanyu.yyy.com hanya dapat diakses melalui port 14000 dan 14400.

Pertama, kita melakukan ``setup``. Untuk melakukan kustomisasi pada port tertentu. Kita hanya perlu mengubah file ports.conf dengan menambahkan ``Listen 14000`` dan ``Listen 14400``. Kita juga perlu mengubah ``<VirtualHost *:14000 *:14400>``

#### Script
#### Abimanyu
```
echo "# If you just change the port or add more ports here, you will likely also
# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default.conf

Listen 80
Listen 14000
Listen 14400

<IfModule ssl_module>
        Listen 443
</IfModule>

<IfModule mod_gnutls.c>
        Listen 443
</IfModule>

# vim: syntax=apache ts=4 sw=4 sts=4 sr noet" > /etc/apache2/ports.conf
```

```
echo "<VirtualHost *:14000 *:14400>
        # The ServerName directive sets the request scheme, hostname and port that
        # the server uses to identify itself. This is used when creating
        # redirection URLs. In the context of virtual hosts, the ServerName
        # specifies what hostname must appear in the request's Host: header to
        # match this virtual host. For the default virtual host (this file) this
        # value is not decisive as it is used as a last resort host regardless.
        # However, you must set it for any further virtual host explicitly.
        #ServerName www.example.com

        ServerName rjp.baratayuda.abimanyu.e25.com
        ServerAlias www.rjp.baratayuda.abimanyu.e25.com

        ServerAdmin webmaster@localhost
        DocumentRoot /var/www/rjp.baratayuda.abimanyu.e25

        # Available loglevels: trace8, ..., trace1, debug, info, notice, warn,
        # error, crit, alert, emerg.
        # It is also possible to configure the loglevel for particular
        # modules, e.g.
        #LogLevel info ssl:warn

        ErrorLog \${APACHE_LOG_DIR}/error.log
        CustomLog \${APACHE_LOG_DIR}/access.log combined

        # For most configuration files from conf-available/, which are
        # enabled or disabled at a global level, it is possible to
        # include a line for only one particular virtual host. For example the
        # following line enables the CGI configuration for this host only
        # after it has been globally disabled with "a2disconf".
        #Include conf-available/serve-cgi-bin.conf
</VirtualHost>" > /etc/apache2/sites-available/rjp.baratayuda.abimanyu.e25.com.conf

a2ensite rjp.baratayuda.abimanyu.e25.com.conf

service apache2 restart
```

##### Setup
```
wget -O '/var/www/rjp.baratayuda.abimanyu.e25.com' 'https://drive.usercontent.google.com/download?id=1pPSP7yIR05JhSFG67RVzgkb-VcW9vQO6'
unzip -o /var/www/rjp.baratayuda.abimanyu.e25.com -d /var/www/
mv /var/www/rjp.baratayuda.abimanyu.yyy.com /var/www/rjp.baratayuda.abimanyu.e25
rm /var/www/rjp.baratayuda.abimanyu.e25.com
rm -rf /var/www/rjp.baratayuda.abimanyu.yyy.com
```

#### Sadewa
```
lynx rjp.baratayuda.abimanyu.e25.com:14000
lynx rjp.baratayuda.abimanyu.e25.com:14400
```

#### Hasil
##### Port 14000
![Screenshot_56](https://github.com/arda294/Jarkom-Modul-2-E25-2023/assets/108173647/039bae7c-9670-4928-a4d2-2a99290afe58)

##### Port 14400
![Screenshot_57](https://github.com/arda294/Jarkom-Modul-2-E25-2023/assets/108173647/65edc2ac-d28f-445f-967e-8f721e83ad09)

##### Port Acak
![Screenshot_58](https://github.com/arda294/Jarkom-Modul-2-E25-2023/assets/108173647/8b51f9ec-0448-4c82-b917-a94e569a85a4)


### Soal 18
> Untuk mengaksesnya buatlah autentikasi username berupa ``“Wayang”`` dan ``password “baratayudayyy”`` dengan ``yyy`` merupakan kode kelompok. Letakkan DocumentRoot pada ``/var/www/rjp.baratayuda.abimanyu.yyy``.

Untuk melakukan autentikasi pada sebuah server, diperlukan AuthType dan Require Valid-User. Lalu untuk AuthUserFile sendiri adalah tempat yang ingin kita gunakan untuk melakukan write. Sedangkan untuk AuthName adalah content-type Autentikasi pada apache2

#### Script
#### Abimanyu
```
echo "<VirtualHost *:14000 *:14400>
        # The ServerName directive sets the request scheme, hostname and port that
        # the server uses to identify itself. This is used when creating
        # redirection URLs. In the context of virtual hosts, the ServerName
        # specifies what hostname must appear in the request's Host: header to
        # match this virtual host. For the default virtual host (this file) this
        # value is not decisive as it is used as a last resort host regardless.
        # However, you must set it for any further virtual host explicitly.
        #ServerName www.example.com

        ServerName rjp.baratayuda.abimanyu.e25.com
        ServerAlias www.rjp.baratayuda.abimanyu.e25.com

        ServerAdmin webmaster@localhost
        DocumentRoot /var/www/rjp.baratayuda.abimanyu.e25

        # Available loglevels: trace8, ..., trace1, debug, info, notice, warn,
        # error, crit, alert, emerg.
        # It is also possible to configure the loglevel for particular
        # modules, e.g.
        #LogLevel info ssl:warn

        ErrorLog \${APACHE_LOG_DIR}/error.log
        CustomLog \${APACHE_LOG_DIR}/access.log combined

        <Location />
            AuthType Basic
            AuthName "Secret"
            AuthUserFile /var/www/rjp.baratayuda.abimanyu.e25/.htpasswd
            Require valid-user
        </Location>

        # For most configuration files from conf-available/, which are
        # enabled or disabled at a global level, it is possible to
        # include a line for only one particular virtual host. For example the
        # following line enables the CGI configuration for this host only
        # after it has been globally disabled with "a2disconf".
        #Include conf-available/serve-cgi-bin.conf
</VirtualHost>" > /etc/apache2/sites-available/rjp.baratayuda.abimanyu.e25.com.conf

a2ensite rjp.baratayuda.abimanyu.e25.com.conf

service apache2 restart
```

Tambahkan autentikasi dengan menggunakan command htpasswd, pertama masukkan username ``Wayang`` menggunakan command
```
htpasswd -c ./.htpasswd Wayang
```

Kemudian masukkan password ``baratayudayyy`` yyy diganti nama kelompok
```
baratayudae25
```

Jika sudah, lakukan 
```
cat htpasswd
```

Lalu, masukkan hasilnya ke dalam ``/var/www/rjp.baratayuda.abimanyu.e25/.htpasswd`` seperti berikut.
```
echo 'Wayang:$apr1$4xfsgYei$.mHG8h1QJ0RkyoHTqZ6Fs0' > /var/www/rjp.baratayuda.abimanyu.e25/.htpasswd
```

![Screenshot_60](https://github.com/arda294/Jarkom-Modul-2-E25-2023/assets/108173647/884316bd-8f1a-4eb9-a2f1-23906ec501a5)

#### Sadewa
```
lynx rjp.baratayuda.abimanyu.e25.com:14000
lynx rjp.baratayuda.abimanyu.e25.com:14400
```

#### Hasil
![Screenshot_53](https://github.com/arda294/Jarkom-Modul-2-E25-2023/assets/108173647/1c26efae-0ebb-4a3b-99c4-415bc0a600ad)
![Screenshot_54](https://github.com/arda294/Jarkom-Modul-2-E25-2023/assets/108173647/29947fbb-6b03-4e57-a624-3ba8eea50394)
![Screenshot_55](https://github.com/arda294/Jarkom-Modul-2-E25-2023/assets/108173647/15e8a51a-c5d1-4205-9c4a-4b50a3a480e2)
![Screenshot_56](https://github.com/arda294/Jarkom-Modul-2-E25-2023/assets/108173647/952a584b-07bd-4140-ba84-0527a97b61fa)

### Soal 19
> Buatlah agar setiap kali mengakses IP dari Abimanyu akan secara otomatis dialihkan ke www.abimanyu.yyy.com (alias)

Untuk soal ini, diperlukan mengedit file ``000-default.conf`` pada node ``abimanyu`` untuk redirect ke ``abimanyu.e25.com`` ketika ServerName tidak match pada virtual host lainnya.
#### Script
```
echo "<VirtualHost *:80>
        # The ServerName directive sets the request scheme, hostname and port that
        # the server uses to identify itself. This is used when creating
        # redirection URLs. In the context of virtual hosts, the ServerName
        # specifies what hostname must appear in the request's Host: header to
        # match this virtual host. For the default virtual host (this file) this
        # value is not decisive as it is used as a last resort host regardless.
        # However, you must set it for any further virtual host explicitly.
        #ServerName www.example.com

        ServerAdmin webmaster@localhost
        DocumentRoot /var/www/html

        RewriteEngine On
        RewriteCond %{HTTP_HOST} !^abimanyu.e25.com$
        RewriteRule /.* http://abimanyu.e25.com/ [R]

        # Available loglevels: trace8, ..., trace1, debug, info, notice, warn,
        # error, crit, alert, emerg.
        # It is also possible to configure the loglevel for particular
        # modules, e.g.
        #LogLevel info ssl:warn

        ErrorLog \${APACHE_LOG_DIR}/error.log
        CustomLog \${APACHE_LOG_DIR}/access.log combined

        # For most configuration files from conf-available/, which are
        # enabled or disabled at a global level, it is possible to
        # include a line for only one particular virtual host. For example the
        # following line enables the CGI configuration for this host only
        # after it has been globally disabled with "a2disconf".
        #Include conf-available/serve-cgi-bin.conf
</VirtualHost>" > /etc/apache2/sites-available/000-default.conf

service apache2 restart
```

Bisa dilihat script diatas menambahkan rewrite dengan kondisi host tidak ``abimanyu.e25.com``. Jika kondisi tersebut true, maka akan redirect ke ``abimanyu.e25.com``



#### Hasil
Sadewa menajalankan command ``lynx 10.49.3.4``

![image](https://github.com/arda294/Jarkom-Modul-2-E25-2023/assets/114855785/bc79e5a3-f088-4ecc-8be1-d8b9b8adb43d)
### Soal 20
> Karena website www.parikesit.abimanyu.yyy.com semakin banyak pengunjung dan banyak gambar gambar random, maka ubahlah request gambar yang memiliki substring “abimanyu” akan diarahkan menuju abimanyu.png.

Untuk melakukan hal itu, akan diperlukan file ``.htaccess`` pada directory ``/var/www/parikesit.abimanyu.e25/public/images`` yang rewrite uri menjadi abimanyu.png ketika terdapat substring abimanyu pada uri.
#### Script
```
echo "<VirtualHost *:80>
        # The ServerName directive sets the request scheme, hostname and port that
        # the server uses to identify itself. This is used when creating
        # redirection URLs. In the context of virtual hosts, the ServerName
        # specifies what hostname must appear in the request's Host: header to
        # match this virtual host. For the default virtual host (this file) this
        # value is not decisive as it is used as a last resort host regardless.
        # However, you must set it for any further virtual host explicitly.
        #ServerName www.example.com

        ServerName parikesit.abimanyu.e25.com
        ServerAlias www.parikesit.abimanyu.e25.com

        ServerAdmin webmaster@localhost
        DocumentRoot /var/www/parikesit.abimanyu.e25

        # Available loglevels: trace8, ..., trace1, debug, info, notice, warn,
        # error, crit, alert, emerg.
        # It is also possible to configure the loglevel for particular
        # modules, e.g.
        #LogLevel info ssl:warn

        <Directory /var/www/parikesit.abimanyu.e25/public>
            Options +Indexes
        </Directory>

        <Directory /var/www/parikesit.abimanyu.e25/secret>
            Options -Indexes
        </Directory>

        <Directory /var/www/parikesit.abimanyu.e25/public/js>
            Options +Indexes
        </Directory>

        Alias "/js" "/var/www/parikesit.abimanyu.e25/public/js"

        <Directory /var/www/parikesit.abimanyu.e25/public/images>
            Options +FollowSymLinks +Indexes -Multiviews
            AllowOverride All
        </Directory>

        ErrorDocument 404 /error/404.html
        ErrorDocument 403 /error/403.html

        ErrorLog \${APACHE_LOG_DIR}/error.log
        CustomLog \${APACHE_LOG_DIR}/access.log combined

        # For most configuration files from conf-available/, which are
        # enabled or disabled at a global level, it is possible to
        # include a line for only one particular virtual host. For example the
        # following line enables the CGI configuration for this host only
        # after it has been globally disabled with "a2disconf".
        #Include conf-available/serve-cgi-bin.conf
</VirtualHost>" > /etc/apache2/sites-available/parikesit.abimanyu.e25.com.conf

echo '
RewriteEngine On
RewriteCond %{REQUEST_URI} abimanyu
RewriteRule .* abimanyu.png [NC,L]
' > /var/www/parikesit.abimanyu.e25/public/images/.htaccess

service apache2 restart
```

Pada config virtual host, ditambahkan directory ``/var/www/parikesit.abimanyu.e25/public/images`` yang berisi options ``+FollowSymLinks +Indexes -Multiviews`` dan ``AllowOverride All`` agar rewrite dapat dilakukan pada ``.htaccess``. Kemudian, file ``.htaccess`` berisi rewrite condition ``abimanyu`` yang akan mencari substring ``abimanyu`` pada request uri. Ketika pattern tersebut match, akan melakukan rewrite uri menjadi ``abimanyu.png`` 
#### Hasil
Sadewa melakukan command ``lynx parikesit.abimanyu.e25.com/public/images/abimanyu-student.jpg``

![image](https://github.com/arda294/Jarkom-Modul-2-E25-2023/assets/114855785/4e5ca4dc-4f31-4139-b3bc-441e3a2fb348)
![image](https://github.com/arda294/Jarkom-Modul-2-E25-2023/assets/114855785/451cdcf4-e1c9-4219-bc8a-a2729d93f562)

Jika dilihat file abimanyu-student.jpg yang didownload, ukuran filenya telah sesuai dengan file abimanyu.png yang ada pada ``parikesit.abimanyu.e25.com``

![image](https://github.com/arda294/Jarkom-Modul-2-E25-2023/assets/114855785/babcc004-aa9c-4d3a-8921-43db479d365b)









