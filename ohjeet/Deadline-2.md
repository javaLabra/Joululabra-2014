﻿# Deadline 2

### Aloita ohjelmointi

* Toteuta projektia pieninä paloina
* Aloita oleellisesta ohjelmalogiikasta, älä käyttöliittymästä tai ulkoasusta
* Lähde liikkeelle yksinkertaisesta toteutuksesta

### Clean Code

* Koodin tulisi alusta lähtien olla siistiä ja laajennettavaa
* [Koodin laatuvaatimukset](Koodin-laatuvaatimukset.md)
* Tuo projektiisi checkstyle, kts. [checkstyle ohjeet](Checkstyle.md)
* Lisää checkstyle raportti dokumentaatio kansioon

### JUnit-yksikkötestit:

* Ohjelman testien tulisi alusta lähtien olla kattavia
  * Testaa mahdollisimman montaa luokkaa
  * Testaa mahdollisimman montaa metodia
  * Testaa mahdollisimman monelta kantilta
  * Huomioi [koodin laatuvaatimuksien](Koodin-laatuvaatimukset.md) alakohta *Testaus*
* Noin 10 testiä valmiina
* Generoi pit-raportti ja laita se dokumentaatiokansion sisälle pit-kansioon.
  * [ohjeet](Maven-Cobertura-ja-PIT.md#raportit)
  * Kannattaa myös generoida ja katsoa läpi cobertura-raportti, mutta sitä ei tarvitse lisätä dokumentaatioon.

### Luokkakaavio

* Piirrä käsin tai jollain ohjelmalla
  * Skannaa tai ota selkeä kuva käsinpiirretystä
* Palauta .png tai .jpg -tiedostomuodossa
* Hahmottele ensimmäinen versio ohjelmastasi
* Määrittelyvaiheen luokkakaavio
* Luokkakaavioon järjestelmän tärkeimmät luokat
* Luokkien nimet ja yhteydet riittää
* [Matin Ilmoittautumisjärjestelmän minikaavio tuopinalusessa](https://raw.github.com/javaLabra/Javalabra2013-1/master/luokkakaavio1.jpg)