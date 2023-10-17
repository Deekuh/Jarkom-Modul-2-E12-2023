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
Buatlah website utama pada node arjuna dengan akses ke arjuna.yyy.com dengan alias www.arjuna.yyy.com dengan yyy merupakan kode kelompok.

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
Dengan cara yang sama seperti soal nomor 2, buatlah website utama dengan akses ke abimanyu.yyy.com dan alias www.abimanyu.yyy.com.

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
Kemudian, karena terdapat beberapa web yang harus di-deploy, buatlah subdomain parikesit.abimanyu.yyy.com yang diatur DNS-nya di Yudhistira dan mengarah ke Abimanyu.

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
Buat juga reverse domain untuk domain utama. (Abimanyu saja yang direverse)

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
Seperti yang kita tahu karena banyak sekali informasi yang harus diterima, buatlah subdomain khusus untuk perang yaitu baratayuda.abimanyu.yyy.com dengan alias www.baratayuda.abimanyu.yyy.com yang didelegasikan dari Yudhistira ke Werkudara dengan IP menuju ke Abimanyu dalam folder Baratayuda.

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
Untuk informasi yang lebih spesifik mengenai Ranjapan Baratayuda, buatlah subdomain melalui Werkudara dengan akses rjp.baratayuda.abimanyu.yyy.com dengan alias www.rjp.baratayuda.abimanyu.yyy.com yang mengarah ke Abimanyu.

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
## Soal 10
## Soal 11
## Soal 12
## Soal 13
## Soal 14
## Soal 15
## Soal 16
## Soal 17
## Soal 18
## Soal 19
## Soal 20
