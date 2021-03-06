# GPS

## Paikannuksen perusteet

GPS-paikannuksella päästään nykyisin tyypillisesti muutaman metrin tarkkuuteen, joka esim maanteillä navigoidessa on enemmän kuin tarpeeksi, muttei vielä mahdollista tarkempaa ajamista itsekseen. Maantiellä nykyisin itseohjautuvat uudet autot hoitavat suunnan pitämisen lähinnä konenäkö-tekniikoiden avulla, koska tarkemmasta GPS-sijainnista ei juurikaan olisi hyötyä kunnes tiet ja niiden muutokset olisi reaaliaikaisesti senttitarkkuudella kartoitettu.

Pellolla sen sijaan vierekkäisiä uria ja toistuvasti samoja lohkoja ajaessa tarkasta paikkatiedosta on kameradataa enemmän hyötyä. Tällöin avoimen GPS-signaalin rinnalle otetaan sitä tarkentava korjaus-signaali, joita on käytännössä kahta eri tekniikkaa.

Tähän asti olen käyttänyt sanaa GPS paikannusjärjestelmistä, mutta oikeastaan pitäisi puhua GNSS-järjestelmistä joita ovat ovat vanhimman, jo 90-luvulla käyttöön otetun GPS:n (USA) lisäksi Galileo (EU), Glonass (Venäjä) ja uusimpana maailmanlaajuisesti toimivana Kiinalaisten BeiDou. Viimeisin ei ole vielä kovin laajassa käytössä vuonna 2021 kun verkko valmistui käyttökuntoon kesällä 2020 ja vastaanottimia ei ole kauaa ollut yleisesti saatavilla.

Kukin paikannusjärjestelmä on perusperiaatteeltaan kovin samantyyppinen, Maata kiertää muutamia kymmeniä satelliitteja tunnetuilla kiertoradoilla, nämä lähettävät radiosignaalina omaa paikkaansa sekä tarkkaa aikasignaalia. Vastaanotin kuuntelee yhtäaikaa mahdollisimman montaa satelliittia, käytännössä avoimella paikalla näitä on kussakin verkossa kaikkina ajanhetkinä horisontin yläpuolella vähintään 6 joista neljän signaalin perusteella voidaan paikka laskea. Mitä useampia signaaleja vastaanotetaan, ja mitä kauempana toisistaan kuultavat satelliitit ovat, sitä parempaan tarkkuuteen päästään. Käytännössä useimmat nykyvastaanottimet seuraavatkin samaan aikaan useamman eri verkon signaaleja.


Differentiaali-GPS, DGPS perustuu tunnetussa sijainnissa olevan tukiaseman vastaanottamaan paikkatietoon, ja reaaliajassa tehtävään vertailuun lasketun ja tunnetun sijainnin erotukseen. Tämä erotus lähetetään liikkuville vastaanottimille muodossa "sain juuri nyt sijaintini eroksi 6m lähteen ja 3m etelään, korjaa omaa gnss-signaalista laskemaasi paikkaa vastaavasti. Eli siis voidaan olettaa virheen olevan samansuuntainen ja -suuruinen myös liikkuvan vastaanottimen kohdalla


### täydennettäviä asioita:
* virhelähteet
* rtk
* kaupalliset korjaus-signaalit
* kiihtyvyysanturit
* https://www.use-snip.com/kb/knowledge-base/question-what-is-an-ntrip/



## Antennin asennuspaikka

Kuten edellä todettiin, GNSS-paikkasignaali on sitä parempi mitä enemmän satelliitteja kuullaan, eri puolilta näkyvää taivasta. Antennin olisi siis hyvä sijaita mahdollisimman korkealla ja avoimella näkyvyydellä eri suuntiin. Maatilaympäristössä viljankuivaamon katto olisi monesti paras paikka, mutta teknisesti hiukan haastava sekä fyysisen asennuksen että kaapelointien suhteen. Matalammat rakennuksetkin toimivat kunhan lähistöllä ei ole liikaa korkeita puita tai muita rakennuksia rajaamassa näkyvyyttä. GPS-signaali gigahertsitaajuusluokassa läpäisee varsin huonosti esteitä, käytännössä puhutaan avoimesta näkyvyydestä taivaalle.

AgOpenGPS:n suosittelemassa GNSS-vastaanottimessa mukana tuleva antenni vaatii alustakseen metallia, mielellään pyöreä tasainen levy noin parinkymmenen sentin säteellä tai riittävän suuri (=metrejä joka suuntaan) yhtenäinen, maadoitettu metallipinta, esim katto. Antennin kiinnitys tapahtuu magneetilla sekä tarvittaessa lisäksi ruuveilla.

Tukiaseman asennuksessa on syytä huomioida ukkossuojaus riittävästi, eli käytännössä tarpeeksi paksu maadoituskaapeli suoraan kiinteistön maadoitukseen.

Traktori-asennuksessa järkevin ja softan asetuksen osalta myös ainoa hyvin toimiva paikka on ohjaamon katolla, taka-akselin etupuolella. Tässäkin antennin alle tarvitaan metallipinta joka on maadoitettava koneen runkoon. Helpointa asennus toki on jos hytin katto sattuu olemaan peltiä, tällön magneetti-antennin heittäminen katolle ja johdon veto hyttiin riittää. Harmillisesti traktorivalmistajat ovat kuitenkin käyttäneet monesti muovia nykykoppiensa katoissa ja tarvittavan metallipinnan joutuu sinne erikseen rakentamaan.

## Tukiaseman softa, RaspberryPi-image

Helpoksi tavaksi tukiaseman pystyttämiseen on osoittautunut RaspberryPi-korttitietokoneen ja valmiin käyttöjärjestelmä-imagen käyttäminen. RaspberryPi on Brittiläisen säätiön alunperin opetuskäyttöön luoma pieni tietokone josta on vuosien varrella julkaistu eri versiota, ja joka on kerännyt hyvin laajan harrastajakunnan erilaisiin käyttötarkoituksiin.

Suositeltavin malli tähän käyttöön on [3B+](https://www.verkkokauppa.com/fi/product/24605/kcjmm/Raspberry-Pi-3-model-B-yhden-piirilevyn-tietokone) joka maksaa hiukan alle 50e. Uudempi 4-malli on huomattavasti tehokkaampi, mutta tässä kohtaa siitä ei ole hyötyä, päinvastoin lisääntynyt teho vaatii suurempaa virtalähdettä sekä aktiivista jäähdytystä.

Vakiona mukana ei tule minkäänlaista koteloa tai virtalähdettä, virransyöttö on normaalilla micro-usb liittimellä ja tehokkaat kännykän laturit toimivat. Käytännössä virtalähteessä pitää olla tarpeeksi tehoa, 2A pitäisi yleensä riittää kun käyttää tarpeeksi laadukasta eli johtimiltaan sopivan paksua kaapelia. Ikean myymät [laturit](https://www.ikea.com/fi/fi/p/koppla-3-paikkainen-usb-laturi-valkoinen-20415027/) ja [USB-kaapelit](https://www.ikea.com/fi/fi/p/lillhult-usb-a-mikro-usb-johto-tummanharmaa-70484792/) ovat monen harrastajan hyväksi toteamia valintoja.

Kotelon osalta tietokonekauppiaden harrastuskäyttöön myymät erilaiset kotelot eivät ehkä tässä käytössä ole tarpeellisia, vaan itse suosin sähkötarvikeliikkeestä/rautakaupasta asennuskoteloa joka on vesitiivis ajatellen asennusta esim kylmään ulkorakennukseen. Liian pientä ei kannata valita jos asennuspaikka ei ole ahdas, esim 15x10x8cm sisämitoilla oleva laatikko toimii oikein mukavasti tietokoneen, GPS-modulin sekä poe-virtalähteen asennukseen.

Tallenusmedianaan RPI käyttää micro-SD muistikorttia. Tämän ei tarvitse olla kovin iso, käytännössä 16 gigatavua jonka noin kympillä marketista saa, riittää paremmin kuin hyvin tähän käyttöön.

### Kortille asennetaan https://github.com/Stefal/rtkbase ohjelma.

* Lataa valmis käyttöjärjestelmä-image osoitteesta https://github.com/jancelin/pi-gen/releases ( Base_GNSS_<versio>.zip, noin 500 megatavua.
* pura zip-paketti, saat .img-tiedoston
* lataa esim https://www.balena.io/etcher/ jolla image kirjoitetaan muistikortille
* asenna kortti RPI:lle, kytke verkkokaapelilla samaan verkkoon pc:n kanssa
* avaa basegnss.local-sivu, salasana "admin"  


## Poe-sähkönsyöttö tukiasemalle

Koska tukiaseman tietokone on saatava 5m antennikaapelin etäisyydelle antennista, tarkoittaa se monesti sijaintia jossa ei välttämättä ole sähkötöpseliä helposti saatavilla. Ja koska tukiasema tarvitsee kuitenkin verkkoa, on yksi johto yleensä joka tapauksessa tarpeen vetää. Helpoimmillaan tämä on silloin ethernet-johto joka kytketään toisesta päästään reitittimeen, ja toisesta päästä tukiaseman tietokoneeseen, mutta väliin lisätään Power-over-ethernet muuntimet. Reitittimen päähän tulee [injektoriksi](https://www.verkkokauppa.com/fi/product/60099/gmnxd/TP-LINK-TL-POE150S-PoE-injektori) kutsuttu laite joka lisää verkkokaapeliin yleensä 48v DC-sähkön, ja tukiaseman päähän vastaavasti [poe-extractor](https://www.verkkokauppa.com/fi/product/53361/gvdhk/TP-LINK-TL-POE10R-PoE-splitter).

Injektorin voi toki korvata myös Poe-kytkimellä mikäli sähköä käyttäviä laitteita on useita. Esimerkki tällaisestä: https://www.verkkokauppa.com/fi/product/55086/mtggh/TP-LINK-TL-SG1005P-V2-5-porttinen-kytkin

Maailmalta löytyy myös toimivaksi havaittuja [POE-splittereitä](https://www.aliexpress.com/item/1005001356576287.html) joissa on suoraan RaspberryPi:stä löytyvä microusb-liitin. Tälläisen kanssa ei ole tarvetta erikseen kolvata sopivaa kaapelia väliin.

Poe-laitteiden kanssa on syytä tarkistaa että virransyöttö on riittävä, käytännössä minimitarve on 5V dc 2A.

Saatavilla on myös edullisempia "passive poe"-palikoita ja kaapeleita jotka eivät ole IEEE 802.3af tai muunkaan standardin mukaisia, vaan pelkästään passiivisia kytkentöjä niin että reittittimen päähän tulee laitteen alkuperäinen virtalähde. Näiden käyttö Raspberryn ja 5v syöttöjännitteen kanssa ei ole järkevää, ohuen ethernet-kaapelin häviöt ovat liian suuret ilman korkeamman jännitteen käyttämistä.

## Ardusimple GPS firmispäivitys

GPS-vastaanottimissa on sisäinen ohjelmisto joka on syytä päivittää, todennäköisesti tehtaalta saapuessa se on melko tuore mutta tästä ei voi olla varma. Päivitys tapahtuu Ublox:in windows-softalla, tarkempi ohjeistus TODO



## rtk2go

http://rtk2go.com/ on vapaasti käytetävissä oleva internetpalvelu joka tarjoaa NTRIP-korjausdatan välityspalvelun. Palvelu perustu SNIP-ohjelmistoon jonka voisi asentaa myös omalle tietokoneelle, mutta tässä käyttötapauksessa jonkun muun ylläpitämä palvelu on kovasti helppo ratkaisu.

Heidän käyttöehdoissa sanotaan:

> Terms of Use: By sending your data stream to this Caster you affirm that:
> a) You have the right to do so, and
> b) You consent to allow others to freely use your data, and
> c) The caster owner / operator shall be held harmless for any faults or loss – real or perceived.
> The caster owner / operator (SCSC) reserves the right to remove or block any party for abuse.

Eli: a) sinulla on lupa lähettää dataa, käytännössä tukiaseman tarkkaa paikkatietoa ja b) annat sen muiden vapaaseen käyttöön. Kohta c, palvelun tarjoaja ei vastaa mistään menetyksistä ja voi lopettaa palvelun tarjoamisen väärinkäyttäjille. Ei siis mitään erikoista.


Datan lähettäminen palveluun vaatii rekisteröitymisen http://www.rtk2go.com/new-reservation/

![kuva1](kuvat/gps/rekisterointi1.png)

Lomake vaatii nimesi, toimivan sähköpostiosoitteen (ei julkaista missään) sekä MountPT Name:n joka on julkisesti tukiasemasi yksilöivä tieto. Kannattaa huomioida että tämä julkaistaan yhdessä senttitarkan sijainnin kanssa, joten esim oma nimesi ei välttämättä ole järkevin valinta jos antenni on talosi katolla. Tilan nimi tai muu vastaava on oikein toimiva, 4-20 kirjainta tai numeroa ilman välilyöntejä, viiva ja alaviiva ovat sallittuja erikoismerkkejä. Nimessä pienet ja isot kirjaimet ovat eri asia.

![kuva2](kuvat/gps/rekisterointi2.png)

Salasanakentän voi jättää tyhjäksi tässä kohtaa, jolloin palvelu lähettää sinulle tarvittavan satunnais-salasanan. Tätä ei tarvitse syöttää kuin kerran tukiaseman asetuksiin, joten arvottu satunnaismerkkijono on hyvä.

Message Format ja ntrip protocol voi jättää oletusasetuksiinsa, samoin kuin optional settingsin valintaboksit.

![kuva3](kuvat/gps/rekisterointi3.png)

Kaupunki ja maakoodi (FIN) ovat näkyvillä tukiasemien listauksessa.

Mistä kuulit RTK2go:sta voi hyvin täyttää "Referred by Colleague" jos luet aiheesta täältä ensimmäistä kertaa...

Lähettämisen jälkeen sähköpostistasi pitäisi löytyä vastausviesti, johon pitää vastata jotta rekisteröinti etenee. Tämän jälkeen ihminen käsittelee ilmoituksesi ja saat sen jälkeen erikseen kuittausviestin jossa on tukiaseman yhdistämiseen tarvittavat tiedot.


## wifi tukiasemalle

Jos lankaverkon veto tukiaseman paikkaan ei ole helppo vaihtoehto, RaspberryPi:ssä on myös wifi. Tämän saa käyttöön kirjautumalla komentoriville, esim putty-ohjelmalla tai jos käytössä mac/linux, suoraan ssh-komennolla.

> ssg basegnss@basegnss.local

salasana basegnss!

komentorivi "basegnss@basegnss:~ $" aukeaa

Komento:
 > sudo nano /etc/wpa_supplicant/wpa_supplicant.conf"

avaa wifi-asetukset editoriin

täytä kohtaan ssid="" oma verkon nimesi, psk: "" salasanan

ctrl+x lopettaa editorin, kysyy tallennetaanko johon "y" vastaamalla kirjoitetaan muutokset

> sudo reboot

käynnistää tukiaseman uudestaan ja liittyy wifiin jos asetukset on oikein




## Gps:n asetukset

Jotta tukiasema toimii, tarvii se muutamia säätöjä. GPS:n päivitysvaiheessa asennettu konfiguraatio ei välttämättä ole oikea, ja se tarvitsee korvata tukiaseman omalla konffilla. Lisäksi pitää tarkistaa että tukiasemasofta koittaa löytää GPS:n oikeasta portista

Kirjaudutaan ensin selaimella osoitteeseen http://basegnss.local , salasana admin. Jos etusivulla näkyy suoraan paikka kartalla ja vihreitä ja keltaisia palkkeja satelliittien merkiksi, kaikki on mallikkaasti valmiiksi. Jos ei, niin tarkista settings-välilehdeltä, "main service" ja "options", mitä kohdassa "Com port" lukee. RaspberryPI:n kanssa oikea portti on "ttyACM0". Tämän jälkeen save, ja käytä Main Servicen liukusäädin hetki asennossa off.

Jos vieläkään ei paikkatieto lähde juoksemaan, sammuta "main service" selaimessa ja kirjaudu tukiasemaan ssh:lla kuten ylläolevassa wifi-ohjeessa.

aja komentorivillä

> basegnss@basegnss:~ $ ./"rtkbase/tools/set_zed-f9p.sh /dev/ttyACM0 115200 rtkbase/receiver_cfg/U-Blox_ZED-F9P_rtkbase.cfg

Tästä pitäisi tulla pitkä tuloste:


>U-Blox ZED-F9P detected
>Resetting ZED-F9P to default settings
>UBX-ACK-ACK:
>  ACK to Class x06 (CFG) ID x09 (CFG)

  ... ...

>  UBX-RXM-SFRBX:
>   gnssId 2 svId  36 reserved1 1 freqId 0 numWords 9
>    chn 49 version 2 reserved2 16
>      GAL: long message? len 9
>      GAL: even 0 page_type 0 word_type 4
>      Ephemeris 4: IODnav 50 SVID 36 Cic 65531 Cis 4
>         t0c 8180 af0 2143116590 af1 2096782 af2 0

>  Done
>  basegnss@basegnss:~ $   


Tämän jälkeen taas selaimessa "main-service" käyntiin ja nyt pitäisi paikan löytyä. Tässä kohtaa käyttöliittymästä tulee mukavampi kun muutaman minuutin jälkeen klikkaa kartan yläpuolella olemista koordinaateista oikeassa reunassa olevaa leikepöytänappia, ja käy tästä kopioidun paikkarimpsun liittämässä main servicen asetuksiin, Ranskan rannikon sijaan.

Tämä ei kuitenkaan ole vielä normaaliin RTK-paikannukseen pitkällä tähtäimellä riittävän tarkka tukiaseman sijainti, vaan seuraavaksi se määritellään tarkemmin.

## Tukiaseman paikan määritys

Jotta RTK-paikannus toimii mahdollisimman hyvin, on tukiaseman käsitys omasta paikastaan oltava mahdollisimman tarkka. Tämän varmistamiseksi on olemassa erilaisia menetelmiä, joilla on erilaisia tarkkuuksia.

Tässä kohtaa on hyvä huomata että eri karttapalvelut eivät ole välttämättä riittävän tarkkoja tietyn pisteen määrittämiseen edes metrin tarkkuudella, vaan kaikissa näissä on virhettä jonka suuruus ja suunta vaihtelee. Eli välttämättä tarkkakaan paikka ei osu millään kartalla juuri sentilleen oikean näköiseen kohtaan, kun kartta-aineisto ei ole tarpeeksi tarkkaa.

Ensimmäinen, ja samalla epätarkin määritysmahdollisuun on antaa tukiaseman keskiarvottaa omaa paikkaansa jonkin aikaa, ja sitten kopioida se sijainti talteen. Tämä antaa riittävän tarkkuuden traktorin suoraan kulkemiseen tiettynä päivänä, mutta jos halutaan toistaa esim samoja uria myöden ajo myöhemmin, tämä ei vielä välttämättä siihen riitä.

Parempi menetelmä on antaa tukiaseman tallentaa logia muutaman vuorokauden, ja sitten lähettää tämä ulkoiseen palveluun analysoitavaksi

Tallennus kytketään päälle tukiaseman webbihallinnassa kohdasta File Service, ja logs-välilehdellä näkyy datan tallentuminen. Muutaman päivän keräämisen jälkeen logi ladataan koneelle ja siirretään analysoitavaksi.

todo

https://rtklibexplorer.wordpress.com/2020/02/05/rtklib-tips-for-using-a-cors-station-as-base/

https://rtklibexplorer.wordpress.com/2017/11/23/ppp-solutions-with-the-swiftnav-piksi-multi/

Rinex-formaatti

viive mittauksen lähettämisessä parantaa tarkkuutta kun dataa on enemmän saatavilla

https://webapp.geod.nrcan.gc.ca/geod/tools-outils/ppp.php?locale=en




## Rtk2go oikeat parametrit, lähettävät viestityypit

Kun paikka on tarpeeksi tarkasti syötetty tukiaseman tietoihin, voidaan käynnistää lähetys rtk2go-palveluun. Tämä tapahtuu syöttämällä Ntrip-serviceen tarvittavat tiedot, eli siis

* Caster address: rtk2go.com
* Caster port: 2101
* Caster password: <rekisteröitymisen yhteydessä annettu>
* Mount name: <rekisteröidessä valitsemasi>

Kohdassa Rtcm messages valitaan mitä tietoja ja kuinka usein palveluun lähetetään. Viestityypit löytyvät esim täältä: https://www.use-snip.com/kb/knowledge-base/an-rtcm-message-cheat-sheet/ ja tarkemmin https://www.use-snip.com/kb/knowledge-base/rtcm-3-message-list/

luku suluissa tyypin jälkeen kertoo kuinka monen vastaanotetun paketin välein tietty viesti lähetetään eteenpäin. Jos siis gps antaa uuden datan 100ms välein eli 10Hz, luku yksi lähettää sen 10 kertaa sekunnissa, luku 10 kerran sekunnissa ja 100 kerran kymmenessä sekunnissa.

Perustilanteessa korjausdata halutaan lähettää joko kerta, ja tukiaseman tiedot voidaan lähettää harvemmin koska ne eivät muutu.

Agopen-gps:n käyttöön Ardusimplen GPS:llä seuraavat viestit on todettu toimivaksi: 1005(10),1077,1087,1097,1230(3)

Eli siis, lähetetään 10 kertaa sekunnissa
* 1077 gps data
* 1087 Glonass data
* 1097 Galileo data

joka kolmannella kerralla lähetetään

* 1230 "GLONASS L1 and L2 Code-Phase Biases"

kerran sekunnissa lähetetään

* 1005 "Stationary RTK Reference Station ARP", Antennin paikkatieto


## tukiaseman varmuuskopiointi

RaspberryPi:n massamuistinaan käyttämä SD-muistikortti ei ole tunnetusti maailman vakain ja pitkäikäisin tallennusmedia jatkuvasti kirjoitettuna. On siis syytä pitää varakortti jossa on asetukset tallessa, käytännössä käytön aikana kortin sisältö ei päivity joten sellaisen voi kloonata suoraan.

Yksi vaihtoehto olisi myös tehdä kortista kirjoitussuojattu, ja olla tallentamatta mitään muutoksia suoraan.

TODO


## vaihtoehtoinen asennus muunlaiselle tietokoneelle

Koska yleinen komponenttipula vaikeuttaa Rasberry PI:n saatavuutta, on yksi ihan varteenotettava vaihtoehto tukiasemalle käyttää esim vanhempaa kannettavaa johon asentaa linux ja ohjelmisto erikseen. Tässä on etuna operoinnin helppous kun sen voi tehdä koneella itsellään, mutta toki tämä aiheuttaa myös rajoitteita koneen asennuspaikkaan joka lähtökohtaisesti täytyy olla kuiva sisätila sähköpistokkeella, antenni- tai usb-kaapelin etäisyydellä antennin sijoituspaikasta. Toki vastaanottimen sijoittaminen kauemmas tietokoneesta on mahdollista aktiivisen usb-jatkokaapeli avulla, mutta tässäkin on toki omat rajoitteensa esim sähkönsyötön osalta.

Myös Windows-pc:n käyttö on mahdollista, ohjelmistona tällöin [Snip](https://www.use-snip.com/) jonka ilmaisversio riittää tässä tarkoituksessa.

Eräs vaihtoehto olisi käyttää myös todella yksinkertaista ESP32-sulautettua tietokonetta, tähän löytyy ohjelmisto https://github.com/nebkat/esp32-xbee 

## olemassa olevan tukiasemaverkoston käyttäminen

Syksyllä 2021 tuli mahdolliseksi käyttää Maanmittauslaitoksen kahdenkymmenen RTK-tukiaseman asemadataa Eurooppalaisen verkoston kautta

Verkostosta nämä Suomenkin asemien streamit ovat saatavissa avoimesti kolmen eri palveluntarjoajan kautta - myöskin maksutta, mutta vaatien ennakkorekisteröitymisen.

Tuolta 20 aseman joukosta joudut myös valitsemaan tukiaseman, joka sijaitsee lähimpänä käyttöpaikkaasi. Monilla alueilla etäisyys asemiin on sen verran suuri, että tarkkuus voi jäädä n. 5 cm luokkaan, eikä RTK:n tavoiteltu alle 2 cm, mutta paljon parempi kuin maksuttomat differentaalikorjaukset.

1. Avaa: https://register.rtcm-ntrip.org/cgi-bin/registration.cgi
2. Täytä yllämainitulla sivulla tietosi, haluamasi käyttäjätunnus sekä salasana (joilla NTRIP-verkkoon myöhemmin myös kirjaudut) ja ehtojen hyväksymisen jälkeen lähetä kaavake.
3. Saat ensin sähköpostin, että rekisteröitymisesi on vastaanotettu. Sitten jonkun ajan päästä (itsellä alle 30 min) joku hyväksyy rekisteröitymisesi ja saat toisen sähköpostin.
4. Vahvistusviestiä odottaessa voit etsiä tämän sivuston kartalta sinua lähimmän Maanmittauslaitoksen tukiaseman, johon maksutta on mahdollista päästä käsiksi. http://epncb.oma.be/_networkdata/data_access/real_time/map.php
Kirjaa sieltä ylös vaikkapa parin lähimmän aseman nimi joka pomppaa silmille kun sopivaa vihreää palluraa klikkaat.  esim. TUO200FIN0
5. Nyt voit avata GPS-laitteesi, RTKLIB tai SNIP-ohjelman tietokoneella, Lefebure NTRIP-Clientin puhelimella jne. ja kirjautua haluamaasi mountpointtiin/tukiasemaan seuraavalla osoitetiedolla.
euref-ip.net:2101
Eli toisin ilmaistuna:
Caster IP/osoite tai vastaavaan kohtaan kirjoitat: euref-ip.net
Caster Port/portti tai vastaavaan kohtaan kirjoitat: 2101
Mountpointiksi/alustuspisteeksi jne kirjoitat esim: TUO200FIN0
Käyttäjätunnus ja salasana niin kuin ne lomakkeella annoit.

AOG:n sisäänrakennettu NTRIP-sovellus ei välttämättä tunnista euref-ip.net osoitetta vaan sinne pitää syöttää osoitteeksi kyseisen DNS-serverin ipv4 osoite, kirjoitushetkellä 157.90.249.44 Tämä saattaa joskus vaihtua, vaikka domain-nimi pysyisi samana, tämän voi tarkistaa vaikkapa ping-komennolla.