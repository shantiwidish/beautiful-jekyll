---
layout: post
title: Load Balancer using Apache
tags: [submission,kemanan jaringan]
---

Konsep load balancing adalah pendistribusian beban kerja kepada beberapa target pemrosesan. Tujuannya untuk meningkatkan performa, optimasi penggunaan sumber daya, mempercepat waktu response, dan menghindari penggunaan berlebihan / terpusat pada satu sumber daya. Load balancing dapat dicapai dengan menggunakan hardware ataupun software.

Saat ini akan saya praktekan implementasi load balancing menggunakan software dengan bantuan web server. Environment dalam praktek ini adalah :

* Sistem operasi Ubuntu
* Web server Apache2

Simulasi pada praktek ini web server akan berlaku sebagai load balancer yang membagi request kepada dua services sebagai target pemrosesan. Target pemrosesan hanyalah bagian dari pembuktian bahwa load balancing berjalan dengan benar, jadi cukup kita buat sebuah aplikasi kecil yang dapat diakses melalui TCP. Untuk praktek ini saya menggunakan python dengan flask agar aplikasi bisa berjalan pada port selain 80.

Konfigurasi Apache

1. Setup virtual host

Copy file contoh vhost dengan cara:

~~~
cp /etc/apache2/sites-available/000-default.conf.example /etc/apache2/sites-available/loadbalancer.conf
~~~

Berikut adalah contoh file config :

~~~xml
<VirtualHost *:80>
	ServerName localtesting.com
    ProxyRequests off	
	ServerAdmin webmaster@cena	
	<Proxy balancer://mycluster>
        # WebHead1
        BalancerMember http://0.0.0.0:8080
        # WebHead2
        BalancerMember http://0.0.0.0:8081
        Require all granted
        ProxySet lbmethod=byrequests
    </Proxy>
        # balancer-manager
        # This tool is built into the mod_proxy_balancer
        # module and will allow you to do some simple
        # modifications to the balanced group via a gui
        # web interface.
        <Location /balancer-manager>
            SetHandler balancer-manager
            Require host localtesting.com
        </Location>
        ProxyPass /balancer-manager !
        ProxyPass / balancer://mycluster/
</VirtualHost>
~~~

2. Enabling modules

Beberapa modul yang diperlukan agar load balancer dapat digunakan pada webserver apache2.

~~~
sudo a2enmod lbmethod_byrequests slotmem_shm a2enmod proxy
~~~
3. Reload apache service
~~~
sudo service apache2 reload
~~~

Persiapan Percobaan

Untuk dapat melakukan simulai ini, diperlukan service tambahan yang tidak berjalan pada port 80. Jadi saya menggunakan python dengan Flask (web services) dan menjalankannya di port 8080 dan 8081

1. Pastikan terdapat 2 mini services yang berjalan pada 2 port yang berbeda

~~~
import sys
from flask import Flask
app = Flask(__name__)

@app.route("/")
def hello():
    return "Hello World!"

if __name__ == "__main__":
    app.run(host='0.0.0.0', port=8080)
~~~

Buka browser dan coba akses pada kedua services pada port 8080 dan 8081. 

2. Test Load Balancer

Setelah dua service berjalan kita aktifkan config load balancer

~~~
sudo a2ensite loadbalancer.conf
sudo service apache2 reload
~~~

Pada browser coba akses local host dengan port 80. Seharusnya akan muncul isi dari mini services yang jalan pada port 8080 atau 8081. Lakukan refresh berkali - kali. Pastikan bahwa mini services secara bergantian diakses oleh load balancer.
