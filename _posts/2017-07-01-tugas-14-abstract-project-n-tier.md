---
layout: post
title: Abstract Project N-Tier
subtitle: Travel Kere Project
tags: [submission,psbk]
---

Kegiatan wisata tak dapat dipungkiri akan selalu menjadi kebutuhan setiap manusia
untuk menghilangkan kejenuhan dari kegiatan rutin yang dilakukan setiap hari. Hal ini membuat industri
pariwisata akan selalu menjadi hal yang tidak akan pernah mati. Masyarakat Indonesia khususnya DKI Jakarta
dan sekitarnya pun memiliki minat tinggi terhadap kegiatan wisata. Kendala bagi para traveler di Jakarta maupun
sekitarnya dalam melaksanakan kegiatan wisata yaitu minimnya waktu untuk melakukan wisata ke luar daerah,
anggaran yang diperlukan, dan teman untuk melakukan wisata. Kendala tersebut dikarenakan
kurangnya informasi mengenai pariwisata di sekitar DKI Jakarta dan Kepulauan Seribu.

Perkembangan teknologi web yang kini semakin berkembang, tidak hanya mampu menyediakan informasi, namun juga
mampu untuk mengolah informasi. Proses pengolahan informasi dengan memanfaatkan teknologi web menjadikan web media
informasi yang dinamis. Untuk memudahkan update data pariwisata dan maintenance
sistem, maka sistem dikembangkan dengan arsitektur N-tier. Pada architecture N-Tier,
layer dipisahkan menjadi persistence, accessor, business logic, presentation, dan elsewhere layer.

Persistence layer merupakan database dari sistem yang dibuat menggunakan aplikasi MySQL. Accessor layer
merupakan layer yang berfungsi untuk mengakses data dari persistence layer menggunakan script PHP dengan framework
Code Igniter pada bagian Model.  Business logic layer berfungsi untuk memproses data menggunakan script PHP pada bagian
Controller. Presentation layer merupakan tampilan aplikasi yang dibuat menggunakan script PHP pada bagian View.
Elsewhere layer merupakan cara komunikasi sistem yang dibuat dengan database Kepulauan Seribu dan DKI Jakarta
menggunakan web services REST dimana data tempat wisata diambil dari kedua database tersebut dan
jumlah traveler yang mengikuti trip pada sistem akan menjadi jumlah visitor pada masing-masing database pariwisata
tersebut.

Kata kunci : pariwisata, DKI Jakarta, Kepulauan Seribu, Arsitektur N-Tier.

Tourism activities can not be denied will always be the needs of every human being to eliminate the saturation
of routine activities performed every day. This makes the industry tourism will always be a thing that will never die.
Indonesian people especially DKI Jakarta and surrounding areas also have a high interest in tourism activities.
Constraints for the traveler in Jakarta and surrounding in carrying out the activities of the tour is the lack of
time to travel out of the area, budget required, and friends to do tours. The constraint is due lack of information
about tourism around DKI Jakarta and Kepulauan Seribu.

The growth of web technology development, not only able to provide information, but also
able to process information. The process of information processing by utilizing web technology makes it acts as media
dynamic information. To facilitate the update of tourism data and maintenance
System, then the system developed with N-tier architecture. In the N-Tier architecture,
Layer separated into persistence, accessor, business logic, presentation, and elsewhere layer.

Persistence layer is a database of systems created using MySQL applications. Accessor layer
is a layer that works to access data from persistence layer using PHP script with framework
Code Igniter in the Models section. Business logic layer works to process data using PHP script in the
Controller section. Presentation layer is an application display created using PHP script in the View section.
Elsewhere layer is a way of system communication made with database of Kepulauan Seribu and DKI Jakarta
using REST web services where tourism data is taken from both databases and
the number of travelers who join trips on the system will be the number of visitors on each tourism database.

Keywords : tourism, DKI Jakarta, Kepulauan Seribu, N- Tier Architecture.
