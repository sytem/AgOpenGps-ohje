# Komponentit

Tässä on esimerkkilistaus järjestelmässä tarvittavista fyysisistä komponenteista. Linkit ovat vain yksi ehdotus ostopaikasta, eikä kirjoittajalla ole mitään sidonnaisuuksia näihin.

## [RTK-tukiasema RaspberyPI:llä](RTK-GPS.md)

* RaspberyPI 3 b+ https://www.verkkokauppa.com/fi/product/24605/kcjmm/Raspberry-Pi-3-model-B-yhden-piirilevyn-tietokone
* virtalähde:
  * USB-virtalähde, 5v 2A esim [Ikeasta](https://www.ikea.com/fi/fi/p/koppla-3-paikkainen-usb-laturi-valkoinen-20415027/) ja [micro-usb-kaapeli](https://www.ikea.com/fi/fi/p/lillhult-usb-a-mikro-usb-johto-tummanharmaa-70484792/) 
  * tai POE-injektori esim https://www.aliexpress.com/item/1005001356576287.html
* Ardusimple GPS-moduli ja antenni https://www.ardusimple.com/product/simplertk2b-basic-starter-kit-ip65/
* kotelo, IP55 tai parempi, esim [Motonetistä](https://www.motonet.fi/fi/tuote/9000216/Asennuskotelo-160x135x83mm-IP55)
* Micro-SD muistikortti, 8GB tai isompi
* Metallialusta ja tolppakiinnitys antennin asennukseen paikan mukaisesti

Syksyllä 2021 yleisen komponenttipulan myötä RaspberryPI-korttitietokoneiden saatavuus on varsin heikko. 3B+ malli olisi monessa mielessä paras mutta näitä ei juuri kaupoista löydy. 

## traktorin PC

PC:n osalta järjestelmä itsessään ei ole kovinkaan vaativa, mutta ympäristö jossa sitä käytetään, aiheuttaa paljonkin vaatimuksia. Normaalia (kannettavaa) tietokonetta kun ei ole suunniteltu kestämään pölyä, tärinää tai lämpötilanvaihteluita, eikä myöskään näytöt ole yleensä suunniteltu riittämään auringonpaisteessa. Yleensä peltotöitä ei kuitenkaan haluta keskeyttää vaikka olisikin hiukan aurinkoisempi päivä...

Tehojen puolesta mikä tahansa Windows 10:ä pyörittävä PC kelpaa. Konetta hankkiessa nykypäivänä toki kannattaa pitää jonkunlaisena minimitasona core-i5 suoritinta neljännestä sukupolvesta ylöspäin (eli siis core i5-4xxx tai suurempi numero) ja 8 gigaa ram-muistia. SSD-tallennusmedia on tärisevässä ympäristössä itsestäänselvä valinta, tämän ei ole tarvetta olla suurempi kuin 128 gigatavua. Käytettävyyden kannalta kosketusnäyttö on melko ehdoton vaatimus

Lisälaitteita varten tarvitaan muutama USB-portti (voi käyttää myös erillistä hubia), ja toki sähkönsyöttö pitää saada järjestettyä traktorin järjestelmästä, eli käytännössä 12v pistokkeesta.

Fyysisesti vahvistettuja koneita saa tämän tehoisena mukavasti käyttettynä, tunnetuin valmistaja on Panasonic ToughBook-sarjallaan. Google-haku "käytetty toughbook" antaakin useita suomalaisia kauppiaita, esim https://laptops.fi/tuote-osasto/kannettavat-tietokoneet/vahvistetut-ja-ajoneuvokoneet

Toinen monen käyttämä ratkaisu on tablettimallinen windows-pc, tässä kosketusnäyttö hoituu itsestään, samoin kuin akkuvarmennus ja kevyemmän laitteen asennus traktorissa on yleensä huomattavasti helpompaa, tablettimallisille koneille on paljon valmiita ratkaisuja saatavissa.

GPS-korjausdataa varten pc:lle tarvitaan internet-yhteys, tämä voi järjestyä joko pc:n sisäisellä 4G-modeemilla, erillisellä wifi-mokkulalla tai jakamalla netti omasta puhelimesta.


## traktorin elektroniikka

* Ardusimple GPS-moduli ja antenni https://www.ardusimple.com/product/simplertk2b-basic-starter-kit-ip65/

* Elektroniikkamoduli
   * piirilevy, dokumentaatio: https://discourse.agopengps.com/t/kaupoimod-pcb-v4/3920
   * arduino
   * asento/kiihtyvyys-anturi
   * moottoriohjain
   * virransyöttö ja muut oheiskomponentit
   * sopiva kotelo, kaapelointi, liittimet

* Asentoanturi etuakselille
* painonappeja ohjaukseen

* moottori ja mekaaninen asennus ratin pyöritykseen
* TAI: ohjauksen hydrauliventtiilin ohjauskomponentit / Can-väyläohjaus (ei tämän dokumentaation piirissä toistaiseksi)


