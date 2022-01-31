# traktoriin tuleva laitteisto

Traktorin palikat koostuvat muutamasta selkeästä peruspalikasta:

   * PC
   * GPS
   * Elektroniikka-boksi arduinon ympärillä
   * Ulkoiset anturit


## Gps:n firmware-asetukset

Traktorissa oleva GPS-moduli tarvitsee mahdollisimman nopean päivityksen ja vain tiettyjä viestityyppejä. Vastaavasti kuten tukiaseman kanssa on tarve tehdä, moduli tarvii asetukset. Hyväksi havaittu asetustiedosto Ardusimple FP9-vastaanottimelle löytyy osoitteesta https://discourse.agopengps.com/t/improved-konfiguration-files-for-f9p-with-firmware-1-13/2923

päivitysohje osoitteessa: https://discourse.agopengps.com/t/ublox-f9p-config-for-rover/308





## Piirilevyn tilausprosessi

Teoriassa tässä tarvittava arduino-ympäristö olisi mahdollista rakentaa hyppylangoilla suoraan levyltä levylle, mutta luotettavuuden ja selkeyden vuoksi tässä ei olisi mitään järkeä. Varsinkin kun valmiita piirilevy-designeja on saatavissa useita, ja levyjen teettäminen ei nykypäivänä maksa juuri mitään, ei muissa vaihtoehdoissa ole järkeä. Foorumeillä on listattuna monia levyjä joissa on omat hyvät ja huonot puolensa. Kirjoittaja päätyi aikoinaan Suomalaiseen designiin ##todo linkki, kauopoimod vN piirilevyyn. Tilasin levyt kiinalaiselta valmistajalta https://jlcpcb.com/, levy tai oikeastaan viisi kappaletta levyjä maksoivat muutaman euron, toimitus hiukan enemmän mutta kokonaisuutena puhuttiin kympeistä.

Aiemmin, piirilevyjä harrastuskäyttöön on tehnyt myös itse valottamalla ja syövyttämällä, mutta nykypäivänä tehdastekoisten saatavuus on tehnyt DIY-levyistä epäkäytännöllisen vaihtoehdon useimpiin tarkoituksiin.

Toinen monien harrastajien käyttämä piirilevypaja on https://aisler.net/ Hollannissa. Tilaaminen täältä toimii kuten kiinalaistenkin kanssa, ladataan Kicadin tai vastaanvan suuninnitelusoftan tuottama tiedostopaketti, valitaan levyn paksuus ja muut yksityiskohdat sekä toimitus.

Hyvä esimerkki piirilevyn suunnittelusta alusta asti löytyy Jyväskylän Hacklabilta: https://jyvaskyla.hacklab.fi/2022/01/02/esimerkki-elektroniikkasuunnittelusta-tee-se-itse-moottoriohjain/

Toki tässä projektissa suurin osa vaiheista on jo tehty valmiiksi tarjolla olevaksi paketiksi

## Anturien sijoitus

Toimiakseen oikein ohjelmisto käyttää signaaleja eri antureista. Näitä vovat etuäakselin asento, gps sekä koneen kallistus. Näistä viimeisin on normaalisti asennettuna piirilevylle, ja tämän suunta määrittelee myös piirilevyn asennussuunnan traktorissa. Tämä on hyvä ottaa huomioon jo piirilevyn kotelointia miettiessä niin että laatikosta lähtevät johdot ovat järkevään suuntaan kun kiihtyvyysanturi on oikeassa asennossa suhteessa traktoriin. Jos tämä ei ole mahdollista, on asentoanturin sijoitus-suuntaa mahdollista korjata arduino-koodia muokaamalla, mutta valmiita asetuksia tähän ei ainakaan vielä tällähetkellä ole olemassa käyttöliittymässä. 

## Akselianturin vivusto

Monen suosima tapa rakentaa etuakselin asennon anturi on ottaa pyörivä hall-anturi ja rakentaa siihen sopiva vivusto. Monessa paikkaa suositellussa anturissa on D-mallinen akseli M5-kierteellä. Esim puuilo ja muut rautakauapat myyvät kierretankoon sopivia palloniveliä joilla vivusto on helppo tehdä, ja koska voimaa tuon ei kauheasti tarvi kestää, kierretanko voi olla ohutkin. Esimerkkitoteutuksessa kiinnitimme tangon pään putkiklemmarilla raidetankoon, ja kierretangon ja anturin välissä on laserleikattu vaneripala (joka toki ei ole kauhean kosteutta kestävä ratkaisu pitkän päälle, mutta oli käytettävissä olevilla työkaluilla nopein tehdä. Tämän korvaaminen metallista jyrsityllä kappaleella on työlistalla. 

Anturi on liimattau sähköasennusrasiaan joka huolehtii sen suojauksesta vedeltä ja kuralta. Toki paras olisi jos anturin akseli ei osottaisi ylöspäin tai olisi suojattu ylhäältä tulevalta vedeltä. Rasia on kiinnitetty etuakselin ympärille kiristetyllä lattarauta + kierretanko-pannalla. Anturin johto on kolminapainen, ja se on viety ohjaamoon takaikkunan läpiviennin kautta.

## Gps-antennin paikka

Koneessakin oleva gps-antenni tulee asentaa maadoitettuun metallipintaan radiosignaalin toimivuuden takia. Tälläistä ei nykytratktoreista ilman muuuta katolta löydy, joten se piti erikseen sinne rakentaa. Antennin sijoitus neuvotaan tekemään taka-akselin etupuolelle, koneen keskilinjalle ja toki näkyvyyden maksimoinniksi mahdollisimman ylös. Käytätännössä paikka on siis yleensä ohjaamon katon etureunasssa.

Antennin asennuspiste suhteessa taka-akseliin syötetään ohjelmistoon, tässä puhutaan senttiluokan tarkkuudesta jotta ohjaus-algoritmi osaa kompensoida antennin liikkeet oikein.

GPS-antennin kaapeli on kiinteällä liittimellä, eikä kaapelia ole syytä signaalihäviöiden välttämiseksi jatkaa, joten asennupaikka ja läpivienti ohjaamoon tarvii valita niin että viisimetrinen kaapeli riittää. Samoin läpiviennin koko on oltava sellainen että reilusti antennin ohutta kaapelia paksumpi liitin mahtuu siitä läpi, ja toki mielellään myös läpivienti olisi lopullisessa mallissaan tiivis.

## Rattirulla

Helpoin tapa saada traktori ohjautumaan autonmaation pohjalta, on laittaa kone pyörittämään rattia. Tähän näkee kahta päätyyliä, toinen on pyörittää itse rattia esim rc-auton renkaalla suoraan. Toinen vaihtoehto on rakentaa rattiakselin ympärille erillinen kiekko tai ratas jota sitten moottorilla pyöritetään. Moottorista ja ohjaimesta riippuen ratin käsikäyttö voi vaatia joko moottorin irroituksen fyysisestä kontaktista tai sähköstä.

Perus-ohjeen mukainen Cytron-moottoriohjain virtaa saadessaan yrittää pitää moottorin paikoillaan jos ohjaus ei sitä johonkin suuntaan käännä. Tähän on olemassa modaus jolla moottori vapautuu kun softasta automaattiohjaus kytketään pois päältä https://discourse.agopengps.com/t/motor-wiring-to-prevent-back-feed-cytron/4925/11

## Liittimet

Jotta elektroniikkaboksin kytkentä traktoriin olisi helppoa, tarvitaan liittimiä. Tähän löytyy monenlaisia tapoja toimia, itse käytin miljoonalaatikoista löytyneitä AV-alalla yleisiä XLR-liittimiä. Ajonevuokättöön tarkoitetut liittimet ovat toki parempi ratkaisu jos kaupasta joka tapauksessa näitä lähtee hankkimaan, esimerkiksi <todo>

Tarvittavat liitokset:
	* rattimoottori
    * etuakselin asentoanturi
    * napit automaattiohjauksen kytkentään
    * rajakytkin työkonene aktiivisuudelle

Omassa toteutuksessani boksissa on lisäksi muutamia kiinteitä johtoja läpivienti-tiivisteellä liittimen sijaan
    * sähkönsyöttö boksille, 2m kaapeli traktorin pistokkseen sopivalla liittimellä
	* GPS:n antenni, tälle sopivaa liitintä ei ollut käsillä, ja toki myös jokainen liittos heikentää signaali. Toki tämä vaatii joko boksin avaamisen sitä irroittaessa tai gps-antennnin irroittamisen katolta ja johdon pujottelun läpivienneistään.
    * tietokoneen sähkönsyöttö ja usb (boksissa hubi jossa kiinni arduino ja gps sekä langattoman näppäimistön vastaanotin)

## Asennusjärjestys

## Arduinon ohjelmointi

## Testausvaiheet

## Traktorin omat anturit, canbus, hydrauliikka

Monessa traktorissa on jo valmiina paljon mahdollisuuksia automaattiohjaukseen, esimerkiksi kiinteästi asennettu etuakselin asentoanturi. Näiden käyttömahdolisuudet on kuitenkin täysin merkki- ja mallikohtaisia, joten tässä niihin ei pystytä juurikaan syventymään.

Hyviä vaihtoehtoja rattia pyörittävälle moottorille ovat suoraan canbussin kautta traktorin oman hydrauliikan ohjaus, tai erillisellä venttiilistöllä sen ohjaus ohi ratin. Näistä ei kirjoittajalla ole vielä kokemusta.