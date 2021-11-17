# traktoriin tuleva laitteisto



# Gps:n firmware-asetukset

# Windows-asetukset

# Piirilevyn tilausprosessi

Teoriassa tässä tarvittava arduino-ympäristö olisi mahdollista rakentaa hyppylangoilla suoraan levyltä levylle, mutta luotettavuuden ja selkeyden vuoksi tässä ei olisi mitään järkeä. Varsinkin kun valmiita piirilevy-designeja on saatavissa useita, ja levyjen teettäminen ei nykypäivänä maksa juuri mitään, ei muissa vaihtoehdoissa ole järkeä. Foorumeillä on listattuna monia levyjä joissa on omat hyvät ja huonot puolensa. Kirjoittaja päätyi aikoinaan Suomalaiseen designiin ##todo linkki, kauopoimod vN piirilevyyn. Tilasin levyt kiinalaiselta valmistajalta, levy tai oikeastaan viisi kappaletta levyjä maksoivat muutaman euron, toimitus hiukan enemmän.

# Komponenttien hankinta

# Anturien sijoitus

Toimiakseen oikein ohjelmisto käyttää signaaleja eri antureista. Näitä vovat etuäakselin asento, gps sekä koneen kallistus. Näistä viimeisin on normaalisti asennettuna piirilevylle, ja tämän suunta määrittelee myös piirilevyn asennussuunnan traktorissa. Tämä on hyvä ottaa huomioon jo piirilevyn kotelointia miettiessä niin että laatikosta lähtevät johdot ovat järkevään suuntaan kun kiihtyvyysanturi on oikeassa asennossa suhteessa traktoriin. Jos tämä ei ole mahdollista, on asentoanturin sijoitus-suuntaa mahdollista korjata arduino-koodia muokaamalla, mutta valmiita asetuksia tähän ei ainakaan vielä tällähetkellä ole olemassa käyttöliittymässä. 

# Akselianturin vivusto

Monen suosima tapa rakentaa etuakselin asennon anturi on ottaa pyörivä hall-anturi ja rakentaa siihen sopiva vivusto. Monessa paikkaa suositellussa anturissa on D-mallinen akseli M5-kierteellä. Esim puuilo ja muut rautakauapat myyvät kierretankoon sopivia palloniveliä joilla vivusto on helppo tehdä, ja koska voimaa tuon ei kauheasti tarvi kestää, kierretanko voi olla ohutkin. Esimerkkitoteutuksessa kiinnitimme tangon pään putkiklemmarilla raidetankoon, ja kierretangon ja anturin välissä on laserleikattu vaneripala (joka toki ei ole kauhean kosteutta kestävä ratkaisu pitkän päälle, mutta oli käytettävissä olevilla työkaluilla nopein tehdä. Tämän korvaaminen metallista jyrsityllä kappaleella on työlistalla. 

Anturi on liimattau sähköasennusrasiaan joka huolehtii sen suojauksesta vedeltä ja kuralta. Toki paras olisi jos anturin akseli ei osottaisi ylöspäin tai olisi suojattu ylhäältä tulevalta vedeltä. Rasia on kiinnitetty etuakselin ympärille kiristetyllä lattarauta + kierretanko-pannalla. Anturin johto on kolminapainen, ja se on viety ohjaamoon takaikkunan läpiviennin kautta.

# Gps-antennin paikka

Koneessakin oleva gps-antenni tulee asentaa maadoitettuun metallipintaan radiosignaalin toimivuuden takia. Tälläistä ei nykytratktoreista ilman muuuta katolta löydy, joten se piti erikseen sinne rakentaa. Antennin sijoitus neuvotaan tekemään taka-akselin etupuolelle, koneen keskilinjalle ja toki näkyvyyden maksimoinniksi mahdollisimman ylös. Käytätännössä paikka on siis yleensä ohjaamon katon etureunasssa.

Antennin asennuspiste suhteessa taka-akseliin syötetään ohjelmistoon, tässä puhutaan senttiluokan tarkkuudesta jotta ohjaus-algoritmi osaa kompensoida antennin liikkeet oikein.

GPS-antennin kaapeli on kiinteällä liittimellä, eikä kaapelia ole syytä signaalihäviöiden välttämiseksi jatkaa, joten asennupaikka ja läpivienti ohjaamoon tarvii valita niin että viisimetrinen kaapeli riittää. Samoin läpiviennin koko on oltava sellainen että reilusti antennin ohutta kaapelia paksumpi liitin mahtuu siitä läpi, ja toki mielellään myös läpivienti olisi lopullisessa mallissaan tiivis.

# Rattirulla

Helpoin tapa saada traktori ohjautumaan autonmaation pohjalta, on laittaa kone pyörittämään rattia. Tähän näkee kahta päätyyliä, toinen on pyörittää itse rattia esim rc-auton renkaalla suoraan. Toinen vaihtoehto on rakentaa rattiakselin ympärille erillinen kiekko tai ratas jota sitten moottorilla pyöritetään. Moottorista ja ohjaimesta riippuen ratin käsikäyttö voi vaatia joko moottorin irroituksen fyysisestä kontaktista tai sähköstä.

Perus-ohjeen mukainen Cytron-moottoriohjain virtaa saadessaan yrittää pitää moottorin paikoillaan jos ohjaus ei sitä johonkin suuntaan käännä. Tähän on olemassa modaus jolla moottori vapautuu kun softasta automaattiohjaus kytketään pois päältä ## todo linkki forumipostaukseen

# Liittimet

# Asennusjärjestys

# Arduinon ohjelmointi

# Testausvaiheet

# Traktorin omat anturit, canbus, hydrauliikka

Monessa traktorissa on jo valmiina paljon mahdollisuuksia automaattiohjaukseen, esimerkiksi kiinteästi asennettu etuakselin asentoanturi. Näiden käyttömahdolisuudet on kuitenkin täysin merkki- ja mallikohtaisia, joten tässä niihin ei pystytä juurikaan syventymään.

Hyviä vaihtoehtoja rattia pyörittävälle moottorille ovat suoraan canbussin kautta traktorin oman hydrauliikan ohjaus, tai erillisellä venttiilistöllä sen ohjaus ohi ratin. Näistä ei kirjoittajalla ole vielä kokemusta.