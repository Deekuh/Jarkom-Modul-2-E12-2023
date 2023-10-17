# Jarkom-Modul-2-E12-2023

## Anggota Kelompok
- Andhika Lingga Mariano (5025211161)
- Beauty Valen Fajri (5025211227)

## Daftar Isi
- [Topologi](#topologi)
- [Configure](#configure) 
- [Soal 1](#soal-1)
  - [Jawaban](#jawaban)
- [Soal 2](#soal-2)
  - [Jawaban](#jawaban)
- [Soal 3](#soal-3)
  - [Jawaban](#jawaban)
- [Soal 4](#soal-4)
  - [Jawaban](#jawaban)
- [Soal 5](#soal-5)
  - [Jawaban](#jawaban)
- [Soal 6](#soal-6)
  - [Jawaban](#jawaban)
- [Soal 7](#soal-7)
  - [Jawaban](#jawaban)
- [Soal 8](#soal-8)
  - [Jawaban](#jawaban)
- [Soal 9](#soal-9)
  - [Jawaban](#jawaban)
- [Soal 10](#soal-10)
  - [Jawaban](#jawaban)
- [Soal 11](#soal-11)
  - [Jawaban](#jawaban)
- [Soal 12](#soal-12)
  - [Jawaban](#jawaban)
- [Soal 13](#soal-13)
  - [Jawaban](#jawaban)
- [Soal 14](#soal-14)
  - [Jawaban](#jawaban)
- [Soal 15](#soal-15)
  - [Jawaban](#jawaban)
- [Soal 16](#soal-16)
  - [Jawaban](#jawaban)
- [Soal 17](#soal-17)
  - [Jawaban](#jawaban)
- [Soal 18](#soal-18)
  - [Jawaban](#jawaban)
- [Soal 19](#soal-19)
  - [Jawaban](#jawaban)
- [Soal 20](#soal-20)
  - [Jawaban](#jawaban)

## Topologi
<img width="807" alt="Screen Shot 2023-10-17 at 00 22 05" src="https://github.com/Deekuh/Jarkom-Modul-2-E12-2023/assets/114421539/e9b65115-c371-4b68-9f34-25b4496311e0">

## Configure
WerkudaraDNSSlave

<img width="240" alt="Screen Shot 2023-10-17 at 00 22 50" src="https://github.com/Deekuh/Jarkom-Modul-2-E12-2023/assets/114421539/bb0e69a0-1725-4189-811d-efbdc390ad49">

YudhistiraDNSMaster

<img width="227" alt="Screen Shot 2023-10-17 at 00 23 47" src="https://github.com/Deekuh/Jarkom-Modul-2-E12-2023/assets/114421539/fc70bd3a-2a26-45a8-ae8d-c74f4162f367">

WisanggeniWebServer

<img width="235" alt="Screen Shot 2023-10-17 at 00 24 02" src="https://github.com/Deekuh/Jarkom-Modul-2-E12-2023/assets/114421539/9b498135-7965-42ba-b59d-c873aaba2737">

AbimanyuWebServer

<img width="239" alt="Screen Shot 2023-10-17 at 00 24 16" src="https://github.com/Deekuh/Jarkom-Modul-2-E12-2023/assets/114421539/51d3af75-2864-4763-a647-ed0816e1fa70">

PrabukusumaWebServer

<img width="238" alt="Screen Shot 2023-10-17 at 00 24 31" src="https://github.com/Deekuh/Jarkom-Modul-2-E12-2023/assets/114421539/d5334e20-9840-48d6-8228-492303f8f5f7">

ArjunaLoadBalancer

<img width="238" alt="Screen Shot 2023-10-17 at 00 24 44" src="https://github.com/Deekuh/Jarkom-Modul-2-E12-2023/assets/114421539/a8d88a06-195e-4dfd-bf1e-38e1c6dd66cc">

SadewaClient

<img width="245" alt="Screen Shot 2023-10-17 at 00 24 57" src="https://github.com/Deekuh/Jarkom-Modul-2-E12-2023/assets/114421539/92daa643-337e-46b6-aa86-d390eaed11a8">

Nakula Client

<img width="239" alt="Screen Shot 2023-10-17 at 00 25 09" src="https://github.com/Deekuh/Jarkom-Modul-2-E12-2023/assets/114421539/611998bf-0440-43c6-a190-a2eac18f0f12">

## Soal 1
Yudhistira akan digunakan sebagai DNS Master, Werkudara sebagai DNS Slave, Arjuna merupakan Load Balancer yang terdiri dari beberapa Web Server yaitu Prabakusuma, Abimanyu, dan Wisanggeni. Buatlah topologi dengan pembagian seperti di soal. Folder topologi dapat diakses pada drive yang sudah disediakan pada platform praktikum jarkom.

### Jawaban
NakulaClient

Lakukan `ping google.com -c 5` pada NakulaClient

Hasil 

<img width="719" alt="Screen Shot 2023-10-17 at 00 29 41" src="https://github.com/Deekuh/Jarkom-Modul-2-E12-2023/assets/114421539/832258a9-f1a3-4470-9eaf-b89846eaab89">

SadewaClient

Lakukan `ping google.com -c 5` pada SadewaClient

Hasil

<img width="718" alt="Screen Shot 2023-10-17 at 00 30 14" src="https://github.com/Deekuh/Jarkom-Modul-2-E12-2023/assets/114421539/129b2b3c-287e-4d74-8c39-8446de2342c1">

## Soal 2
Buatlah website utama pada node arjuna dengan akses ke **arjuna.yyy.com** dengan alias **www.arjuna.yyy.com** dengan yyy merupakan kode kelompok.

### Jawaban
Yudhistira

Lakukan `nano no2.sh` pada YudhistiraClient

```
#!/bin/bash

apt-get update
apt-get install bind9 -y

echo '
zone "arjuna.e12.com" {
        type master;
        file "/etc/bind/jarkom/arjuna.e12.com";
};' > /etc/bind/named.conf.local

mkdir -p /etc/bind/jarkom
cp /etc/bind/db.local /etc/bind/jarkom/arjuna.e12.com

echo '
;
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     arjuna.e12.com. root.arjuna.e12.com. (
                     2023101001         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      arjuna.e12.com.
@       IN      A       192.212.1.4     ; IP Arjuna
www     IN      CNAME   arjuna.e12.com.
@       IN      AAAA    ::1' > /etc/bind/jarkom/arjuna.e12.com

service bind9 restart
```

NakulaClient

Gunakan IP Node Yudhistira dengan `nano /etc/resolv.conf` pada NakulaClient  

<img width="461" alt="Screen Shot 2023-10-17 at 01 08 15" src="https://github.com/Deekuh/Jarkom-Modul-2-E12-2023/assets/114421539/ce89f80d-917c-4e36-be9e-d8f2123b23a5">

Lakukan `ping arjuna.e12.com -c 5` pada NakulaClient  

Hasil

<img width="568" alt="Screen Shot 2023-10-17 at 01 08 50" src="https://github.com/Deekuh/Jarkom-Modul-2-E12-2023/assets/114421539/63c3021a-41c9-43da-86c3-e6e2bcef6114">

Lakukan `ping www.arjuna.e12.com -c 5` pada NakulaClient  

Hasil

<img width="562" alt="Screen Shot 2023-10-17 at 01 09 19" src="https://github.com/Deekuh/Jarkom-Modul-2-E12-2023/assets/114421539/0261f1b4-6164-4867-943b-e4363cb2cd62">

## Soal 3
Dengan cara yang sama seperti soal nomor 2, buatlah website utama dengan akses ke **abimanyu.yyy.com** dan alias **www.abimanyu.yyy.com**.

### Jawaban
Yudhistira

Lakukan `nano no3.sh` pada YudhistiraClient

```
#!/bin/bash

apt-get update
apt-get install bind9 -y

echo '
zone "arjuna.e12.com" {
        type master;
        file "/etc/bind/jarkom/arjuna.e12.com";
};' > /etc/bind/named.conf.local

mkdir -p /etc/bind/jarkom
cp /etc/bind/db.local /etc/bind/jarkom/arjuna.e12.com

echo '
;
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     arjuna.e12.com. root.arjuna.e12.com. (
                     2023101001         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      arjuna.e12.com.
@       IN      A       192.212.1.4     ; IP Arjuna
www     IN      CNAME   arjuna.e12.com.
@       IN      AAAA    ::1' > /etc/bind/jarkom/arjuna.e12.com

service bind9 restart
```

NakulaClient

Gunakan IP Node Yudhistira dengan `nano /etc/resolv.conf` pada NakulaClient  

<img width="461" alt="Screen Shot 2023-10-17 at 01 08 15" src="https://github.com/Deekuh/Jarkom-Modul-2-E12-2023/assets/114421539/ce89f80d-917c-4e36-be9e-d8f2123b23a5">

Lakukan `ping abimanyu.e12.com -c 5` pada NakulaClient

Hasil

<img width="564" alt="Screen Shot 2023-10-17 at 01 10 48" src="https://github.com/Deekuh/Jarkom-Modul-2-E12-2023/assets/114421539/f435d893-9edb-4623-81fe-693d59ff7f46">

Lakukan `ping www.abimanyu.e12.com -c 5` pada NakulaClient

Hasil

<img width="562" alt="Screen Shot 2023-10-17 at 01 11 14" src="https://github.com/Deekuh/Jarkom-Modul-2-E12-2023/assets/114421539/68f21cbe-d787-4f98-83b8-9ac05295dd35">

## Soal 4
Kemudian, karena terdapat beberapa web yang harus di-deploy, buatlah subdomain **parikesit.abimanyu.yyy.com** yang diatur DNS-nya di Yudhistira dan mengarah ke Abimanyu.

### Jawaban
Yudhistira

Lakukan `nano no4.sh` pada YudhistiraClient

```
#!/bin/bash

echo '
;
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     abimanyu.e12.com. root.abimanyu.e12.com. (
                     2023101001         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      abimanyu.e12.com.
@       IN      A       192.212.3.3     ; IP Abimanyu
www     IN      CNAME   abimanyu.e12.com.
parikesit IN    A       192.212.3.3     ; IP Abimanyu
@       IN      AAAA    ::1
' > /etc/bind/jarkom/abimanyu.e12.com

service bind9 restart
```

Lakukan `ping parikesit.abimanyu.e12.com -c 5` pada NakulaClient

Hasil

<img width="603" alt="Screen Shot 2023-10-17 at 01 34 30" src="https://github.com/Deekuh/Jarkom-Modul-2-E12-2023/assets/114421539/5b39e3d4-ca74-4940-8501-71ab762326ff">

## Soal 5
Buat juga reverse domain untuk domain utama. (*Abimanyu saja yang direverse*)

### Jawaban

Yudhistira

Lakukan `nano no5.sh` pada YudhistiraClient

```
#!/bin/bash

echo '
zone "3.212.192.in-addr.arpa" {
    type master;
    file "/etc/bind/jarkom/3.212.192.in-addr.arpa";
};' >> /etc/bind/named.conf.local

cp /etc/bind/db.local /etc/bind/jarkom/3.212.192.in-addr.arpa

echo '
;
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     abimanyu.e12.com. root.abimanyu.e12.com. (
                     2023101001         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
3.212.192.in-addr.arpa. IN      NS      abimanyu.e12.com.
3                       IN      PTR     abimanyu.e12.com.       ; Byte ke-4 IP Abimanyu' > /etc/bind/jarkom/3.212.192.in-addr.arpa

service bind9 restart
```

Lakukan pengecekan pada addres yang dimiliki abimanyu

<img width="515" alt="Screen Shot 2023-10-17 at 07 20 53" src="https://github.com/Deekuh/Jarkom-Modul-2-E12-2023/assets/114421539/e84d4343-31d1-4cf8-9f15-fd38b7ffb1d9">

Lakukan `host -t PTR 192.212.3.3` pada NakulaClient

Hasil

<img width="479" alt="Screen Shot 2023-10-17 at 06 44 44" src="https://github.com/Deekuh/Jarkom-Modul-2-E12-2023/assets/114421539/9c90521e-b832-41fb-b600-dae391fe0601">

## Soal 6
Agar dapat tetap dihubungi ketika DNS Server Yudhistira bermasalah, buat juga Werkudara sebagai DNS Slave untuk domain utama.

### Jawaban
Yudhistira

Lakukan `nano no6.sh` pada YudhistiraClient

```
#!/bin/bash

echo '
zone "arjuna.e12.com" {
        type master;
        also-notify { 192.212.2.2; }; // IP WerkudaraDNSSlave
        allow-transfer { 192.212.2.2; }; // IP WerkudaraDNSSlave
        file "/etc/bind/jarkom/arjuna.e12.com";
};

zone "abimanyu.e12.com" {
    type master;
    notify yes;
    also-notify { 192.212.2.2; }; // IP WerkudaraDNSSlave
    allow-transfer { 192.212.2.2; }; // IP WerkudaraDNSSlave
    file "/etc/bind/jarkom/abimanyu.e12.com";
};

zone "2.212.192.in-addr.arpa" {
    type master;
    file "/etc/bind/jarkom/2.212.192.in-addr.arpa";
};' > /etc/bind/named.conf.local

service bind9 restart
```

Werkudara

Lakukan `nano no6.sh` pada WerkudaraDNSSlave

```
#!/bin/bash

apt-get update
apt-get install bind9 -y

echo '
zone "arjuna.e12.com" {
    type slave;
    masters { 192.212.2.3; }; // IP Yudhis
    file "/var/lib/bind/arjuna.e12.com";
};

zone "abimanyu.e12.com" {
    type slave;
    masters { 192.212.2.3; }; // IP Yudhis
    file "/var/lib/bind/abimanyu.e12.com";
};
' > /etc/bind/named.conf.local

service bind9 restart
```

Atur `service bind9` pada YudhistiraDNSMaster

Hasil

<img width="436" alt="Screen Shot 2023-10-17 at 06 52 15" src="https://github.com/Deekuh/Jarkom-Modul-2-E12-2023/assets/114421539/e8fb9586-6f49-4a76-97a5-d8466e215f90">

Lakukan `ping arjuna.e12.com -c 5` pada NakulaClient

Hasil

<img width="561" alt="Screen Shot 2023-10-17 at 06 58 19" src="https://github.com/Deekuh/Jarkom-Modul-2-E12-2023/assets/114421539/64547d90-655d-4f57-8504-c1d922f1d1df">

Lakukan `ping www.arjuna.e12.com` pada NakulaClient

Hasil

<img width="530" alt="Screen Shot 2023-10-17 at 06 58 32" src="https://github.com/Deekuh/Jarkom-Modul-2-E12-2023/assets/114421539/a304a81a-ba2b-4b14-8fbc-45bcae9433bc">

## Soal 7
Seperti yang kita tahu karena banyak sekali informasi yang harus diterima, buatlah subdomain khusus untuk perang yaitu **baratayuda.abimanyu.yyy.com** dengan alias **www.baratayuda.abimanyu.yyy.com** yang didelegasikan dari Yudhistira ke Werkudara dengan IP menuju ke Abimanyu dalam folder Baratayuda.

### Jawaban
Yudhistira

Lakukan `nano no7.sh` pada YudhistiraClient

```
#!/bin/bash

apt-get update
apt-get install bind9 -y

echo ';
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     abimanyu.e12.com. root.abimanyu.e12.com. (
                     2023101001         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      abimanyu.e12.com.
@       IN      A       192.212.3.3     ; IP Abimanyu
www     IN      CNAME   abimanyu.e12.com.
parikesit IN    A       192.212.3.3     ; IP Abimanyu
ns1     IN      A       192.212.2.2     ; IP Werkudara
baratayuda IN   NS      ns1
@       IN      AAAA    ::1' > /etc/bind/jarkom/abimanyu.e12.com

service bind9 restart

echo 'options {
       directory "/var/cache/bind";

       // If there is a firewall between you and nameservers you want
       // to talk to, you may need to fix the firewall to allow multiple
       // ports to talk.  See http://www.kb.cert.org/vuls/id/800113

       // If your ISP provided one or more IP addresses for stable
       // nameservers, you probably want to use them as forwarders.
       // Uncomment the following block, and insert the addresses replacing
       // the all-0'\''s placeholder.
       // forwarders {
       //      0.0.0.0;
       // };

       //========================================================================
       // If BIND logs error messages about the root key being expired,
       // you will need to update your keys.  See https://www.isc.org/bind-keys
       //========================================================================
       //dnssec-validation auto;
       allow-query{any;};

       auth-nxdomain no;    # conform to RFC1035
       listen-on-v6 { any; };
};' > /etc/bind/named.conf.options

echo '
zone "arjuna.e12.com" {
       type master;
       file "/etc/bind/jarkom/arjuna.e12.com";
};

zone "abimanyu.e12.com" {
    type master;
    file "/etc/bind/jarkom/abimanyu.e12.com";
    allow-transfer { 192.212.2.2; }; // IP Werkudara
};

zone "2.212.192.in-addr.arpa" {
    type master;
    file "/etc/bind/jarkom/2.212.192.in-addr.arpa";
};' > /etc/bind/named.conf.local

service bind9 restart
```

Werkudara

Lakukan `nano no7.sh` pada WerkudaraDNSSlave

```
#!/bin/bash

apt-get update
apt-get install bind9 -y

echo 'options {
        directory "/var/cache/bind";

        // If there is a firewall between you and nameservers you want
        // to talk to, you may need to fix the firewall to allow multiple
        // ports to talk.  See http://www.kb.cert.org/vuls/id/800113

        // If your ISP provided one or more IP addresses for stable
        // nameservers, you probably want to use them as forwarders.
        // Uncomment the following block, and insert the addresses replacing
        // the all-0'\''s placeholder.

        // forwarders {
        //      0.0.0.0;
        // };

        //========================================================================
        // If BIND logs error messages about the root key being expired,
        // you will need to update your keys.  See https://www.isc.org/bind-keys
        //========================================================================
        //dnssec-validation auto;
        allow-query{any;};

        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
};' > /etc/bind/named.conf.options

echo '
zone "arjuna.e12.com" {
    type slave;
    masters { 192.212.2.3; }; // IP Yudhis
    file "/var/lib/bind/arjuna.e12.com";
};

zone "abimanyu.e12.com" {
    type slave;
    masters { 192.212.2.3; }; // IP Yudhis
    file "/var/lib/bind/abimanyu.e12.com";
};

zone "baratayuda.abimanyu.e12.com" {
    type master;
    file "/etc/bind/baratayuda/baratayuda.abimanyu.e12.com";
};' > /etc/bind/named.conf.local

mkdir -p /etc/bind/baratayuda
cp /etc/bind/db.local /etc/bind/baratayuda/baratayuda.abimanyu.e12.com

echo '
;
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     baratayuda.abimanyu.e12.com. root.baratayuda.abimanyu.e12.com. (
                     2023101001         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      baratayuda.abimanyu.e12.com.
@       IN      A       192.212.3.3     ; IP Abimanyu
www     IN      CNAME   baratayuda.abimanyu.e12.com.' > /etc/bind/baratayuda/baratayuda.abimanyu.e12.com

service bind9 restart
```

Lakukan `ping baratayuda.abimanyu.e12.com` pada Nakulaclient

Hasil

<img width="618" alt="Screen Shot 2023-10-17 at 07 06 05" src="https://github.com/Deekuh/Jarkom-Modul-2-E12-2023/assets/114421539/fc65f95f-dffc-410e-a4a6-ce032f8d09e8">

Lakukan `ping www.baratayuda.abimanyu.e12.com` pada Nakulaclient

Hasil

<img width="615" alt="Screen Shot 2023-10-17 at 07 08 17" src="https://github.com/Deekuh/Jarkom-Modul-2-E12-2023/assets/114421539/7b06498c-88b7-4dd0-ba02-88afc6ff4ccc">

Lakukan `host -t CNAME www.baratayuda.abimanyu.e12.com` pada Nakulaclient

Hasil

<img width="704" alt="Screen Shot 2023-10-17 at 07 06 58" src="https://github.com/Deekuh/Jarkom-Modul-2-E12-2023/assets/114421539/5d35696d-c345-4784-8fa9-aa0a596e5332">

## Soal 8
Untuk informasi yang lebih spesifik mengenai Ranjapan Baratayuda, buatlah subdomain melalui Werkudara dengan akses **rjp.baratayuda.abimanyu.yyy.com** dengan alias **www.rjp.baratayuda.abimanyu.yyy.com** yang mengarah ke Abimanyu.

### Jawaban
Werkudara

Lakukan `nano no8.sh` pada WerkudaraDNSSlave

```
#!/bin/bash

echo ';
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     baratayuda.abimanyu.e12.com. root.baratayuda.abimanyu.e12.com. (
                     2023101001         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      baratayuda.abimanyu.e12.com.
@       IN      A       192.212.3.3     ; IP Abimanyu
www     IN      CNAME   baratayuda.abimanyu.e12.com.
rjp     IN      A       192.212.3.3     ; IP Abimanyu
www.rjp IN      CNAME   rjp.baratayuda.abimanyu.e12.com.' > /etc/bind/baratayuda/baratayuda.abimanyu.e12.com

service bind9 restart
```

Lakukan `ping rjp.baratayuda.abimanyu.e12.com` pada Nakulaclient

Hasil

<img width="661" alt="Screen Shot 2023-10-17 at 07 11 29" src="https://github.com/Deekuh/Jarkom-Modul-2-E12-2023/assets/114421539/fd59bb99-4a77-41e1-83a8-86be104c8a66">

Lakukan `ping www.rjp.baratayuda.abimanyu.e12.com -c 5 ` pada NakulaClient

Hasil

<img width="650" alt="Screen Shot 2023-10-17 at 07 11 41" src="https://github.com/Deekuh/Jarkom-Modul-2-E12-2023/assets/114421539/f701e4e6-6d7f-4ec9-8277-9c0d85176a4a">

## Soal 9
Arjuna merupakan suatu Load Balancer Nginx dengan tiga worker (yang juga menggunakan nginx sebagai webserver) yaitu Prabakusuma, Abimanyu, dan Wisanggeni. Lakukan deployment pada masing-masing worker.

### Jawaban
Pada node Arjuna, install nginx dan ubah konfigurasi file `/etc/nginx/sites-available/lb-jarkom` seperti berikut.

```
#!/bin/bash

 apt-get update
 apt-get install bind9 nginx

echo '
 # Default menggunakan Round Robin
 upstream myweb  {
        server 192.212.3.2; #IP Prabukusuma
        server 192.212.3.3; #IP Abimanyu
        server 192.212.3.4; #IP Wisanggeni
 }

 server {
        listen 80;
        server_name arjuna.e12.com www.arjuna.e12.com;

        location / {
        proxy_pass http://myweb;
        }
 }' > /etc/nginx/sites-available/lb-jarkom

 ln -s /etc/nginx/sites-available/lb-jarkom /etc/nginx/sites-enabled

service nginx restart
```

Pada tiap node worker, buat direktori `/var/www/jarkom` lalu buat file **index.php** yang berisi pesan untuk menandakan worker mana yang sedang berjalan. Lakukan juga konfigurasi pada file `/etc/nginx/sites-available/jarkom` seperti berikut.

**Prabukusuma**
```
#!/bin/bash

apt-get update && apt install nginx php php-fpm -y

mkdir -p /var/www/jarkom

echo '<?php
 echo "Halo, Kamu berada di Prabukusuma";
 ?>' > /var/www/jarkom/index.php

echo '
 server {

        listen 80;

        root /var/www/jarkom/;

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
 }' > /etc/nginx/sites-available/jarkom

ln -s /etc/nginx/sites-available/jarkom /etc/nginx/sites-enabled
rm -rf /etc/nginx/sites-enabled/default
service php7.0-fpm start
service php7.0-fpm restart
service nginx restart
```

**Abimanyu**
```
#!/bin/bash

apt-get update && apt install nginx php php-fpm -y

mkdir -p /var/www/jarkom

echo '<?php
 echo "Halo, Kamu berada di Abimanyu";
 ?>' > /var/www/jarkom/index.php

echo '
 server {

        listen 80;

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
 }' > /etc/nginx/sites-available/jarkom

ln -s /etc/nginx/sites-available/jarkom /etc/nginx/sites-enabled
rm -rf /etc/nginx/sites-enabled/default
service php7.0-fpm start
service php7.0-fpm restart
service nginx restart
```

**Wisanggeni**
```
#!/bin/bash

apt-get update && apt install nginx php php-fpm -y

mkdir -p /var/www/jarkom

echo '<?php
 echo "Halo, Kamu berada di Wisanggeni";
 ?>' > /var/www/jarkom/index.php

echo '
 server {

        listen 80;

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
 }' > /etc/nginx/sites-available/jarkom

ln -s /etc/nginx/sites-available/jarkom /etc/nginx/sites-enabled
rm -rf /etc/nginx/sites-enabled/default
service php7.0-fpm start
service php7.0-fpm restart
service nginx restart
```

*Catatan*:
- `ln -s /etc/nginx/sites-available/jarkom /etc/nginx/sites-enabled` digunakan untuk membuat symlink (link simbolik) dari file konfigurasi Nginx yang berada di direktori /etc/nginx/sites-available ke direktori /etc/nginx/sites-enabled
- `rm -rf /etc/nginx/sites-enabled/default` digunakan untuk menghapus file default agar default page nginx tidak muncul saat dilakukan lynx
- Jangan lupa untuk melakukan `service php7.0-fpm restart` dan `service nginx restart` setiap kali melakukan konfigurasi.

Untung testing, lakukan **lynx** ke setiap node worker dari **NakulaClient**.

`lynx 192.212.3.2` (IP Prabukusuma)<br>
<img src="https://cdn.discordapp.com/attachments/1102231088945963098/1163645792339370055/image.png?ex=65405498&is=652ddf98&hm=d07cb85853240f02953b25bb68b824c481d50f242e74dddca899d1a680388294&">

`lynx 192.212.3.3` (IP Abimanyu)<br>
<img src="https://cdn.discordapp.com/attachments/1102231088945963098/1163645792725258260/image.png?ex=65405498&is=652ddf98&hm=201d32557766ba5f6b989f8089f8eaddf6a488c71770527c0c76e9d0af963cb7&">

`lynx 192.212.3.4` (IP Wisanggeni)<br>
<img src="https://cdn.discordapp.com/attachments/1102231088945963098/1163645793073365052/image.png?ex=65405498&is=652ddf98&hm=97a4fa882856c4e7d4ced1fd72931ce3a79b282446d33302b1fa2bf4b449200f&">

## Soal 10
Kemudian gunakan algoritma **Round Robin** untuk Load Balancer pada **Arjuna**. Gunakan *server_name* pada soal nomor 1. Untuk melakukan pengecekan akses alamat web tersebut kemudian pastikan worker yang digunakan untuk menangani permintaan akan berganti ganti secara acak. Untuk webserver di masing-masing worker wajib berjalan di port 8001-8003. Contoh
- *Prabakusuma:8001*
- *Abimanyu:8002*
- *Wisanggeni:8003*

### Jawaban
Ubah konfigurasi file `/etc/nginx/sites-available/lb-jarkom` pada node Arjuna agar IP address dari setiap node workernya menyertakan port yang digunakan.

```
#!/bin/bash

echo '
 # Default menggunakan Round Robin
 upstream myweb  {
        server 192.212.3.2:8001; #IP Prabukusuma
        server 192.212.3.3:8002; #IP Abimanyu
        server 192.212.3.4:8003; #IP Wisanggeni
 }

 server {
        listen 80;
        server_name arjuna.e12.com www.arjuna.e12.com;

        location / {
        proxy_pass http://myweb;
        }
 }' > /etc/nginx/sites-available/lb-jarkom

 ln -s /etc/nginx/sites-available/lb-jarkom /etc/nginx/sites-enabled

service nginx restart
```

Ubah juga konfigurasi file `/etc/nginx/sites-available/jarkom` pada setiap worker agar masing-masing worker mendengarkan (listen) port mereka sendiri.

**Prabukusuma**
```
#!/bin/bash

echo '
 server {

        listen 8001;

        root /var/www/jarkom/;

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
 }' > /etc/nginx/sites-available/jarkom

ln -s /etc/nginx/sites-available/jarkom /etc/nginx/sites-enabled

service php7.0-fpm start
service php7.0-fpm restart
service nginx restart
```

**Abimanyu**
```
#!/bin/bash

echo '
 server {

        listen 8002;

        root /var/www/jarkom/;

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
 }' > /etc/nginx/sites-available/jarkom

ln -s /etc/nginx/sites-available/jarkom /etc/nginx/sites-enabled

service php7.0-fpm start
service php7.0-fpm restart
service nginx restart
```

**Wisanggeni**
```
#!/bin/bash

echo '
 server {

        listen 8003;

        root /var/www/jarkom/;

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
 }' > /etc/nginx/sites-available/jarkom

ln -s /etc/nginx/sites-available/jarkom /etc/nginx/sites-enabled

service php7.0-fpm start
service php7.0-fpm restart
service nginx restart
```

Untuk testing, lakukan lynx IP tiap worker disertai dengan port masing-masing pada NakulaClient.

`lynx 192.212.3.2:8001`<br>
<img src="https://cdn.discordapp.com/attachments/1102231088945963098/1163654292092239945/image.png?ex=65405c82&is=652de782&hm=8208acdff4fd52eb97ceaf77e72559a2eaa140cafa369e8d0a584237d1bf7936&">

`lynx 192.212.3.3:8002`<br>
<img src="https://cdn.discordapp.com/attachments/1102231088945963098/1163654292465537147/image.png?ex=65405c82&is=652de782&hm=75fa496cf7ff875c6d245a13d30b70e861b8e60f23a72404f6bc5ab1fde94760&">

`lynx 192.212.3.4:8003`<br>
<img src="https://cdn.discordapp.com/attachments/1102231088945963098/1163654292826243082/image.png?ex=65405c83&is=652de783&hm=78066e13b0099eb57a5d43b4a3116d8c1b1bdcc3d9b62e3cf9f3e62723487b7a&">

`curl arjuna.e12.com`<br>
<img src="https://cdn.discordapp.com/attachments/1102231088945963098/1163654935586557962/image.png?ex=65405d1c&is=652de81c&hm=90c967504a8de934c086a4c2b06c531b164ebcffb8fcfb912f62aebe2c8b6cce&">

## Soal 11
Selain menggunakan Nginx, lakukan konfigurasi Apache Web Server pada worker Abimanyu dengan web server **www.abimanyu.yyy.com**. Pertama dibutuhkan web server dengan DocumentRoot pada /var/www/abimanyu.yyy

### Jawaban
Install command wget, unzip, dan juga apache2 pada node Abimanyu.
```
#!/bin/bash

apt-get install wget -y
apt-get install unzip -y
apt-get install apache2
```

Kemudian download dan unzip file abimanyu dari link google drive yang diberikan menggunakan command berikut.
```
wget -O '/var/www/abimanyu.e12.com' 'https://drive.usercontent.google.com/download?id=1a4V23hwK9S7hQEDEcv9FL14UkkrHc-Zc'
unzip -o /var/www/abimanyu.e12.com -d /var/www/
mv /var/www/abimanyu.yyy.com /var/www/abimanyu.e12
rm /var/www/abimanyu.e12.com
rm -rf /var/www/abimanyu.e12/abimanyu.yyy.com
```

Lakukan konfigurasi pada file `/etc/apache2/sites-available/abimanyu.e12.com.conf` seperti berikut.
```
echo '
<VirtualHost *:80>
  ServerAdmin webmaster@localhost
  DocumentRoot /var/www/abimanyu.e12

  ServerName abimanyu.e12.com
  ServerAlias www.abimanyu.e12.com

  ErrorLog ${APACHE_LOG_DIR}/error.log
  CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>' > /etc/apache2/sites-available/abimanyu.e12.com.conf

service apache2 start
a2ensite abimanyu.e12.com.conf
service apache2 restart
```

Untuk testing, lakukan `lynx abimanyu.e12.com` pada NakulaClient.

Kami menemui permasalahan di mana `lynx abimanyu.e12.com` tidak memunculkan apa-apa, sementara `lynx abimanyu.e12.com/home.html` memunculkan pesan "Akulah Abimanyu".

`lynx abimanyu.e12.com`
<img src="https://cdn.discordapp.com/attachments/1102231088945963098/1163661980289208362/image.png?ex=654063ab&is=652deeab&hm=119565adc323bf6fa097d90993ec4f07b16c7b05ee6a4775aaa9087de10141c9&">

`lynx abimanyu.e12.com/home.html`
<img src="https://cdn.discordapp.com/attachments/1102231088945963098/1163661886391328848/image.png?ex=65406395&is=652dee95&hm=e6e333d5e1862b52fd3c955e598cd9ab766566fa97cded7554eef1352f80f419&">

## Soal 12
Setelah itu ubahlah agar url **www.abimanyu.yyy.com/index.php/home** menjadi **www.abimanyu.yyy.com/home**.

### Jawaban
Lakukan konfigurasi pada file `/etc/apache2/sites-available/abimanyu.e12.com.conf` dengan menambahkan
```
<Directory /var/www/abimanyu.e12/index.php/home>
        Options +Indexes
</Directory>

Alias "/home" "/var/www/abimanyu.e12/index.php/home"```
```

Seperti berikut
```
#!/bin/bash

service apache2 start

echo '
<VirtualHost *:80>
  ServerAdmin webmaster@localhost
  DocumentRoot /var/www/abimanyu.e12

  ServerName abimanyu.e12.com
  ServerAlias www.abimanyu.e12.com

  <Directory /var/www/abimanyu.e12/index.php/home>
          Options +Indexes
  </Directory>

  Alias "/home" "/var/www/abimanyu.e12/index.php/home"

  ErrorLog ${APACHE_LOG_DIR}/error.log
  CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>' > /etc/apache2/sites-available/abimanyu.e12.com.conf

service apache2 restart
```

Untuk testing, lakukan `lynx abimanyu.e12.com/home` pada NakulaClient. Pada nomor ini kami juga menemui permasalahan berupa 404 Not Found.
<img src="https://cdn.discordapp.com/attachments/1102231088945963098/1163665513864495114/image.png?ex=654066f6&is=652df1f6&hm=daaa5af6effadf00006ed39a9bbeff29fc7723f1b6bda4b3dc3671042a329ff5&">

## Soal 13
Selain itu, pada subdomain **www.parikesit.abimanyu.yyy.com**, DocumentRoot disimpan pada /var/www/parikesit.abimanyu.yyy

### Jawaban
Download dan unzip file parikesit.abimanyu.
```
#!/bin/bash

wget -O '/var/www/parikesit.abimanyu.e12.com' 'https://drive.usercontent.google.com/download?id=1LdbYntiYVF_NVNgJis1GLCLPEGyIOreS'
unzip -o /var/www/parikesit.abimanyu.e12.com -d /var/www/
mv /var/www/parikesit.abimanyu.yyy.com /var/www/parikesit.abimanyu.e12
rm /var/www/parikesit.abimanyu.e12.com
rm -rf /var/www/parikesit.abimanyu.yyy.com
``` 

Lalu konfigurasi file `/etc/apache2/sites-available/parikesit.abimanyu.e12.com.conf` seperti berikut.
```
echo '
<VirtualHost *:80>
  ServerAdmin webmaster@localhost
  DocumentRoot /var/www/parikesit.abimanyu.e12

  ServerName parikesit.abimanyu.e12.com
  ServerAlias www.parikesit.abimanyu.e12.com

  ErrorLog ${APACHE_LOG_DIR}/error.log
  CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>' > /etc/apache2/sites-available/parikesit.abimanyu.e12.com.conf

a2ensite parikesit.abimanyu.e12.com.conf
service apache2 restart
```

Untuk testing, lakukan `lynx parikesit.abimanyu.e12.com` pada NakulaClient.

<img src="https://cdn.discordapp.com/attachments/1102231088945963098/1163672741703061555/image.png?ex=65406db1&is=652df8b1&hm=672807acba2d03f6298832d488a34bc0c81c35f3de50ca663d1c49ab446a8afb&">

## Soal 14
Pada subdomain tersebut folder /public hanya dapat melakukan directory listing sedangkan pada folder /secret tidak dapat diakses (403 Forbidden).

### Jawaban
Tambahkan konfigurasi berikut untuk mengaktifkan directory listing pada folder /public dan mematikan directory listing pada folder /secret.
```
  <Directory /var/www/parikesit.abimanyu.e12/public>
          Options +Indexes
  </Directory>

  <Directory /var/www/parikesit.abimanyu.e12/secret>
          Options -Indexes
  </Directory>

  Alias "/public" "/var/www/parikesit.abimanyu.e12/public"
  Alias "/secret" "/var/www/parikesit.abimanyu.e12/secret"
```

Sehingga konfigurasi file `/etc/apache2/sites-available/parikesit.abimanyu.e12.com.conf` menjadi seperti berikut.
```
#!/bin/bash

mkdir -p /var/www/parikesit.abimanyu.e12/secret

echo '
<VirtualHost *:80>
  ServerAdmin webmaster@localhost
  DocumentRoot /var/www/parikesit.abimanyu.e12

  ServerName parikesit.abimanyu.e12.com
  ServerAlias www.parikesit.abimanyu.e12.com

  <Directory /var/www/parikesit.abimanyu.e12/public>
          Options +Indexes
  </Directory>

  <Directory /var/www/parikesit.abimanyu.e12/secret>
          Options -Indexes
  </Directory>

  Alias "/public" "/var/www/parikesit.abimanyu.e12/public"
  Alias "/secret" "/var/www/parikesit.abimanyu.e12/secret"

  ErrorLog ${APACHE_LOG_DIR}/error.log
  CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>' > /etc/apache2/sites-available/parikesit.abimanyu.e12.com.conf

service apache2 restart
```

Untuk testing, lakukan `lynx parikesit.abimanyu.e12.com/public` dan `lynx parikesit.abimanyu.e12.com/secret` pada NakulaClient.

`lynx parikesit.abimanyu.e12.com/public`<br>
<img src="https://cdn.discordapp.com/attachments/1102231088945963098/1163673850354094090/image.png?ex=65406eb9&is=652df9b9&hm=1838ceb9f82c51396b229d9ca3945483eaa2b413300f93b82634b839ac1929ef&">

`lynx parikesit.abimanyu.e12.com/secret`<br>
<img src="https://cdn.discordapp.com/attachments/1102231088945963098/1163673850773516318/image.png?ex=65406eba&is=652df9ba&hm=92d695d42ef19eeb4e9cd57c0b2ba33517bf294e37b980c219898a56ec54f5d3&">


## Soal 15
Buatlah kustomisasi halaman error pada folder /error untuk mengganti error kode pada Apache. Error kode yang perlu diganti adalah 404 Not Found dan 403 Forbidden.

### Jawaban
Tambahkan `ErrorDocument 404 /error/404.html` dan `ErrorDocument 403 /error/403.html` pada konfigurasi file `/etc/apache2/sites-available/parikesit.abimanyu.e12.com.conf` seperti berikut.
```
#!/bin/bash

echo '
<VirtualHost *:80>
  ServerAdmin webmaster@localhost
  DocumentRoot /var/www/parikesit.abimanyu.e12

  ServerName parikesit.abimanyu.e12.com
  ServerAlias www.parikesit.abimanyu.e12.com

  <Directory /var/www/parikesit.abimanyu.e12/public>
          Options +Indexes
  </Directory>

  <Directory /var/www/parikesit.abimanyu.e12/secret>
          Options -Indexes
  </Directory>

  Alias "/public" "/var/www/parikesit.abimanyu.e12/public"
  Alias "/secret" "/var/www/parikesit.abimanyu.e12/secret"

  ErrorDocument 404 /error/404.html
  ErrorDocument 403 /error/403.html

  ErrorLog ${APACHE_LOG_DIR}/error.log
  CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>' > /etc/apache2/sites-available/parikesit.abimanyu.e12.com.conf

service apache2 restart
```

Untuk testing, lakukan `lynx parikesit.abimanyu.e12.com/testerror` dan `lynx parikesit.abimanyu.e12.com/secret` pada NakulaClient.

`lynx parikesit.abimanyu.e12.com/testerror` (Test 404 Not Found)
<img src="https://cdn.discordapp.com/attachments/1102231088945963098/1163675890979455036/image.png?ex=654070a0&is=652dfba0&hm=b1cb4c4ffc6f0540904d3a091744b319d71f07fc70b9d2c6ba4bc7e06e8a6254&">
<img src="https://cdn.discordapp.com/attachments/1102231088945963098/1163675891361120316/image.png?ex=654070a0&is=652dfba0&hm=ce4a066db710213b2854f800c9dc3e0b9f60a8178d441145ca2fb23c03f8a368&">

`lynx parikesit.abimanyu.e12.com/secret` (Test 403 Forbidden)
<img src="https://cdn.discordapp.com/attachments/1102231088945963098/1163675891872841810/image.png?ex=654070a0&is=652dfba0&hm=4b19ae52dfb4bd7b2b0c9b51d5918833ee86d0840c3bafe5a7a3b2f1ad157356&">
<img src="https://cdn.discordapp.com/attachments/1102231088945963098/1163675892220952616/image.png?ex=654070a0&is=652dfba0&hm=1a67d2bbe1a1ca588c40e0f8c9b89b8ce9c23e7bcaa966d1753df4b976aa88d6&">


## Soal 16
Buatlah suatu konfigurasi virtual host agar file asset **www.parikesit.abimanyu.yyy.com/public/js** menjadi 
**www.parikesit.abimanyu.yyy.com/js** 

### Jawaban
Tambahkan konfigurasi alias untuk direktori /js pada file `/etc/apache2/sites-available/parikesit.abimanyu.e12.com.conf` seperti berikut.

```
#!/bin/bash

echo '
<VirtualHost *:80>
  ServerAdmin webmaster@localhost
  DocumentRoot /var/www/parikesit.abimanyu.e12

  ServerName parikesit.abimanyu.e12.com
  ServerAlias www.parikesit.abimanyu.e12.com

  <Directory /var/www/parikesit.abimanyu.e12/public>
          Options +Indexes
  </Directory>

  <Directory /var/www/parikesit.abimanyu.e12/secret>
          Options -Indexes
  </Directory>

  Alias "/public" "/var/www/parikesit.abimanyu.e12/public"
  Alias "/secret" "/var/www/parikesit.abimanyu.e12/secret"
  Alias "/js" "/var/www/parikesit.abimanyu.e12/public/js"

  ErrorDocument 404 /error/404.html
  ErrorDocument 403 /error/403.html

  ErrorLog ${APACHE_LOG_DIR}/error.log
  CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>' > /etc/apache2/sites-available/parikesit.abimanyu.e12.com.conf

service apache2 restart
```

Untuk testing, lakukan `lynx parikesit.abimanyu.e12.com/js` pada NakulaClient.

<img src="https://cdn.discordapp.com/attachments/1102231088945963098/1163676684042637322/image.png?ex=6540715d&is=652dfc5d&hm=c3f6595c93aba8aa14ca2438fe14e7a5482fe431fe7053cdc47805f1b755678f&">

## Soal 17
Agar aman, buatlah konfigurasi agar **www.rjp.baratayuda.abimanyu.yyy.com** hanya dapat diakses melalui port 14000 dan 14400.

### Jawaban
Download dan unzip file rjp.baratayuda.abimanyu.

```
#!/bin/bash

wget -O '/var/www/rjp.baratayuda.abimanyu.e12.com' 'https://drive.usercontent.google.com/download?id=1pPSP7yIR05JhSFG67RVzgkb-VcW9vQO6'
unzip -o /var/www/rjp.baratayuda.abimanyu.e12.com -d /var/www/
mv /var/www/rjp.baratayuda.abimanyu.yyy.com /var/www/rjp.baratayuda.abimanyu.e12
rm /var/www/rjp.baratayuda.abimanyu.e12.com
rm -rf /var/www/rjp.baratayuda.abimanyu.yyy.com
```

Kemudian ubah konfigurasi file `/etc/apache2/sites-available/rjp.baratayuda.abimanyu.e12.com.conf` seperti berikut.

```
echo '
<VirtualHost *:14000 *:14400>
  ServerAdmin webmaster@localhost
  DocumentRoot /var/www/rjp.baratayuda.abimanyu.e12

  ServerName rjp.baratayuda.abimanyu.e12.com
  ServerAlias www.rjp.baratayuda.abimanyu.e12.com

  ErrorDocument 404 /error/404.html
  ErrorDocument 403 /error/403.html

  ErrorLog ${APACHE_LOG_DIR}/error.log
  CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>' > /etc/apache2/sites-available/rjp.baratayuda.abimanyu.e12.com.conf
```

Dan tambahkan `Listen 14000` serta `Listen 14400` pada file `/etc/apache2/ports.conf` seperti berikut.

```
echo '
# If you just change the port or add more ports here, you will likely also
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

# vim: syntax=apache ts=4 sw=4 sts=4 sr noet' > /etc/apache2/ports.conf

a2ensite rjp.baratayuda.abimanyu.e12.com.conf
service apache2 restart
```

Untuk testing, lakukan `lynx rjp.baratayuda.abimanyu.e12.com:14000` atau `lynx rjp.baratayuda.abimanyu.e12.com:14400` pada NakulaClient.

<img src="https://cdn.discordapp.com/attachments/1102231088945963098/1163678151717691442/image.png?ex=654072bb&is=652dfdbb&hm=9cdedeeea59efed0fa47ac48ab7ce9adf350d3f9413f8d02b9710f24c7fbd58e&">

Apabila menggunakan port selain 14000 atau 14400, maka website tidak dapat terhubung.

<img src="https://cdn.discordapp.com/attachments/1102231088945963098/1163678152070004826/image.png?ex=654072bb&is=652dfdbb&hm=2c9748338a4ed79052b0b4fd1f499a183652458f7d2c83f2e54822478fa2689c&">

## Soal 18
Untuk mengaksesnya buatlah autentikasi username berupa “Wayang” dan password “baratayudayyy” dengan yyy merupakan kode kelompok. Letakkan DocumentRoot pada /var/www/rjp.baratayuda.abimanyu.yyy.

### Jawaban
Ubah konfigurasi file `/etc/apache2/sites-available/rjp.baratayuda.abimanyu.e12.com.conf` seperti berikut.

```
#!/bin/bash

echo '
<VirtualHost *:14000 *:14400>
  ServerAdmin webmaster@localhost
  DocumentRoot /var/www/rjp.baratayuda.abimanyu.e12

  ServerName rjp.baratayuda.abimanyu.e12.com
  ServerAlias www.rjp.baratayuda.abimanyu.e12.com

  <Directory /var/www/rjp.baratayuda.abimanyu.e12>
          AuthType Basic
          AuthName "Restricted Content"
          AuthUserFile /etc/apache2/.htpasswd
          Require valid-user
  </Directory>

  ErrorDocument 404 /error/404.html
  ErrorDocument 403 /error/403.html

  ErrorLog ${APACHE_LOG_DIR}/error.log
  CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>' > /etc/apache2/sites-available/rjp.baratayuda.abimanyu.e12.com.conf
```

Lalu panggil command `htpasswd` berikut untuk mengautentikasi username dan password.
```
htpasswd -c -b /etc/apache2/.htpasswd Wayang baratayudae12
```

Untuk testing, lakukan `lynx rjp.baratayuda.abimanyu.e12.com:14000` atau `lynx rjp.baratayuda.abimanyu.e12.com:14400` pada NakulaClient.

<img src="https://cdn.discordapp.com/attachments/1102231088945963098/1163679256451219548/image.png?ex=654073c2&is=652dfec2&hm=c06633f66161b7a02f9e1cecbb2a221194f3eeb14adf057a32599a2ffd41650a&">

<img src="https://cdn.discordapp.com/attachments/1102231088945963098/1163679256761614437/image.png?ex=654073c2&is=652dfec2&hm=5c8823f1a81c18d4b02598b41b0bf6858565422a4774e5af2f186ffcebdd2a15&">

<img src="https://cdn.discordapp.com/attachments/1102231088945963098/1163679257210388490/image.png?ex=654073c3&is=652dfec3&hm=06afeb7e8ae130471ad956864fb017e0dacd88e671ef1071356fb1b1f9cbc3e7&">

<img src="https://cdn.discordapp.com/attachments/1102231088945963098/1163679257604661278/image.png?ex=654073c3&is=652dfec3&hm=bb86bd1a167fc92f7362d81a916f758776a0be67d35256f6797ae52845de0d14&">

## Soal 19
Buatlah agar setiap kali mengakses IP dari Abimanyu akan secara otomatis dialihkan ke **www.abimanyu.yyy.com (alias)**

### Jawaban
Ubah konfigurasi file `/etc/apache2/sites-available/000-default.conf` seperti berikut.

```
#!/bin/bash

echo '
<VirtualHost *:80>
    ServerAdmin webmaster@abimanyu.e12.com
    DocumentRoot /var/www/html

    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined

    Redirect / http://www.abimanyu.e12.com/
</VirtualHost>' > /etc/apache2/sites-available/000-default.conf

service apache2 restart
```

Untuk testing, lakukan lynx IP address Abimanyu (`lynx 192.212.3.3`). Dalam soal ini kami menemukan permasalahan yang sama dengan nomor 11, di mana `lynx 192.212.3.3` tidak memunculkan apa-apa, sementara `lynx 192.212.3.3/home.html` memunculkan pesan "Akulah Abimanyu".

`lynx 192.212.3.3`<br>
<img src="https://cdn.discordapp.com/attachments/1102231088945963098/1163680288925307000/image.png?ex=654074b9&is=652dffb9&hm=33f9b8603146bbfa3dd2a732a554f112396f1d8e8ed8f2e866e0c9f694912809&">

`lynx 192.212.3.3/home.html`<br>
<img src="https://cdn.discordapp.com/attachments/1102231088945963098/1163680289256640552/image.png?ex=654074b9&is=652dffb9&hm=266206db767b8825aa4651222c6013228f9495ca55c317738fe9e42244924ddc&">

## Soal 20
Karena website **www.parikesit.abimanyu.yyy.com** semakin banyak pengunjung dan banyak gambar gambar random, maka ubahlah request gambar yang memiliki substring “abimanyu” akan diarahkan menuju abimanyu.png.

### Jawaban
Pertama jalankan comman `a2enmod rewrite` untuk mengaktifkan module rewrite.

Buat file `.htaccess` pada direktori `/var/www/parikesit.abimanyu.e12/` dan isi dengan konfigurasi berikut.
```
echo '
RewriteEngine On
RewriteCond %{REQUEST_URI} ^/public/images/(.*)abimanyu(.*)
RewriteCond %{REQUEST_URI} !/public/images/abimanyu.png
RewriteRule abimanyu http://parikesit.abimanyu.e12.com/public/images/abimanyu.png$1 [L,R=301]' > /var/www/parikesit.abimanyu.e12/.htaccess
```

Kemudian tambahkan

```
<Directory /var/www/parikesit.abimanyu.e12>
        Options +FollowSymLinks -Multiviews
        AllowOverride All
</Directory>
```

pada file `/etc/apache2/sites-available/parikesit.abimanyu.e12.com.conf` seperti berikut.

```
echo '
<VirtualHost *:80>
  ServerAdmin webmaster@localhost
  DocumentRoot /var/www/parikesit.abimanyu.e12

  ServerName parikesit.abimanyu.e12.com
  ServerAlias www.parikesit.abimanyu.e12.com

  <Directory /var/www/parikesit.abimanyu.e12/public>
          Options +Indexes
  </Directory>

  <Directory /var/www/parikesit.abimanyu.e12/secret>
          Options -Indexes
  </Directory>

  <Directory /var/www/parikesit.abimanyu.e12>
          Options +FollowSymLinks -Multiviews
          AllowOverride All
  </Directory>

  Alias "/public" "/var/www/parikesit.abimanyu.e12/public"
  Alias "/secret" "/var/www/parikesit.abimanyu.e12/secret"
  Alias "/js" "/var/www/parikesit.abimanyu.e12/public/js"

  ErrorDocument 404 /error/404.html
  ErrorDocument 403 /error/403.html

  ErrorLog ${APACHE_LOG_DIR}/error.log
  CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>' > /etc/apache2/sites-available/parikesit.abimanyu.e12.com.conf

service apache2 restart
```

Untuk testing, lakukan command-command berikut.

`lynx parikesit.abimanyu.e12.com/public/images/not-abimanyu.png`

`lynx parikesit.abimanyu.e12.com/public/images/abimanyu-student.jpg`

`lynx parikesit.abimanyu.e12.com/public/images/abimanyu.png`

`lynx parikesit.abimanyu.e12.com/public/images/notabimanyujustmuseum.177013`

<img src="https://cdn.discordapp.com/attachments/1102231088945963098/1163680845203251230/image.png?ex=6540753d&is=652e003d&hm=a343b7464e1ebb02ef0612e6e46788e922dbb262dd5f340e345a0d67e1a997bb&">

