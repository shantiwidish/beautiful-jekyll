---
layout: post
title: SOAP (SIMPLE OBJECT ACCESS PROTOKOL)
bigimg: /img/false-soap.jpg
tags: [submission,psbk]
---
**Definisi**

SOAP adalah standar protokol komunikasi untuk melakukan pertukaran pesan yang digunakan oleh Web Services. SOAP menggunakan XML sebagai skema pengkodean untuk permintaan dan merespons parameter-parameter dari permintaan tersebut menggunakan HTTP.
SOAP mencakup empat hal sebagai berikut, yaitu :

* Sebuah format pesan untuk komunikasi satu arah yang menggambarkan bagaimana pesan dapat dikemas ke dalam dokumen XML .
* Sebuah deskripsi bagaimana pesan tersebut direspon menggunakan HTTP (untuk interaksi berbasis Web) atau SMTP (untuk email berbasis interaksi).
* Sekumpulan peraturan yang harus dipenuhi untuk memproses pesan SOAP dan klasifikasi sederhana dari entitas yang terlibat dalam pengolahan pesan SOAP.
* Sekumpulan konvensi tentang cara mengaktifkan panggilan RPC (Remote Procedure Call) menjadi pesan SOAP.


**Struktur SOAP**

Struktur SOAP terdiri dari element-element sebagai berikut :

1. Element <Envelope>  yang mengidentifikasi dokumen XML sebagai SOAP
2. Element <Header> yang terdiri dari blok-blok informasi yang relevan dengan bagaimana pesan akan diproses (informasi header) dan bersifat opsional. 
3. <Body> adalah elemen dimana informasi end to end yang utama yang disampaikan di SOAP harus dilakukan (informasi call dan response).
4. <Fault> adalah informasi error yang terjadi dan bersifat opsional.


**Contoh Penggunaan SOAP**

SOAP Request
~~~ xml
POST /InStock HTTP/1.1
Host: www.example.org
Content-Type: application/soap+xml; charset=utf-8
Content-Length: nnn

<?xml version="1.0"?>
<soap:Envelope
xmlns:soap="http://www.w3.org/2003/05/soap-envelope/"
soap:encodingStyle="http://www.w3.org/2003/05/soap-encoding">
<soap:Body xmlns:m="http://www.example.org/stock">
  <m:GetStockPrice>
    <m:StockName>IBM</m:StockName>
  </m:GetStockPrice>
</soap:Body>
</soap:Envelope>
~~~

SOAP Response
~~~ xml
HTTP/1.1 200 OK
Content-Type: application/soap+xml; charset=utf-8
Content-Length: nnn

<?xml version="1.0"?>
<soap:Envelope
xmlns:soap="http://www.w3.org/2003/05/soap-envelope/"
soap:encodingStyle="http://www.w3.org/2003/05/soap-encoding">
<soap:Body xmlns:m="http://www.example.org/stock">
  <m:GetStockPriceResponse>
    <m:Price>34.5</m:Price>
  </m:GetStockPriceResponse>
</soap:Body>
</soap:Envelope>
~~~

**Kelebihan dan Kelemahan SOAP**

Kelebihan SOAP, yaitu :

1. Simplicity
2. Portability
3. Interoperability
4. Universal Acceptance

Sedangkan, kelemahan SOAP, yaitu :

1. Terlalu bergantung pada HTTP
2. Statelessness
3. Serilization by value and not by reference.
      

**Mekanisme**

Berikut adalah gambaran dari implementasi SOAP
![SOAP](/img/soapdg001.gif)
SOAP client akan mengirimkan SOAP Request melalui internet ( protocol http dapat diakses public melalui internet ) dan diterima oleh SOAP Server(machine) lalu di teruskan kepada SOAP Service untuk memproses request tersebut. Setelah pemrosesan selesai dilakukan SOAP Service akan memberikan SOAP Response kepada SOAP Client.


**Referensi**

https://www.w3schools.com/xml/xml_soap.asp
Papazoglou, Michael P. Web Services, 1st Edition. 2008.  