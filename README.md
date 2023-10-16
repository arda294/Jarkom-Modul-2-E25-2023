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
  - [Soal 3](#soal-3)
    - [Script](#script-2)
    - [Hasil](#hasil-2)
  - [Soal 4](#soal-4)
    - [Script](#script-3)
    - [Hasil](#hasil-3)
  - [Soal 5](#soal-5)
    - [Script](#script-4)
    - [Hasil](#hasil-4)
  - [Soal 6](#soal-6)
    - [Script](#script-5)
    - [Hasil](#hasil-5)
  - [Soal 7](#soal-7)
    - [Script](#script-6)
    - [Hasil](#hasil-6)
  - [Soal 8](#soal-8)
    - [Script](#script-7)
    - [Hasil](#hasil-7)
  - [Soal 9](#soal-9)
    - [Script](#script-8)
    - [Hasil](#hasil-8)
  - [Soal 10](#soal-10)
    - [Script](#script-9)
    - [Hasil](#hasil-9)
  - [Soal 11](#soal-11)
    - [Script](#script-10)
    - [Result](#result-10)
  - [Soal 12](#soal-12)
    - [Script](#script-11)
    - [Result](#result-11)
  - [Soal 13](#soal-13)
    - [Script](#script-12)
    - [Result](#result-12)
  - [Soal 14](#soal-14)
    - [Script](#script-13)
    - [Result](#result-13)
  - [Soal 15](#soal-15)
    - [Script](#script-14)
    - [Result](#result-14)
  - [Soal 16](#soal-16)
    - [Script](#script-15)
    - [Result](#result-15)
  - [Soal 17](#soal-17)
    - [Script](#script-16)
    - [Result](#result-16)
  - [Soal 18](#soal-18)
    - [Script](#script-17)
    - [Result](#result-17)
  - [Soal 19](#soal-19)
    - [Script](#script-18)
    - [Result](#result-18)
  - [Soal 20](#soal-20)
    - [Script](#script-19)
    - [Result](#result-19)

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
#### Script
#### Hasil
### Soal 12
#### Script
#### Hasil
### Soal 13
#### Script
#### Hasil
### Soal 14
#### Script
#### Hasil
### Soal 15
#### Script
#### Hasil
### Soal 16
#### Script
#### Hasil
### Soal 17
#### Script
#### Hasil
### Soal 18
#### Script
#### Hasil
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
#### Script
#### Hasil






