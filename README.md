# AgOpenGps-ohje

[AgOpenGPS](https://github.com/farmerbriantee/AgOpenGPS) on avoin ohjelmisto- ja laitteistokokonaisuus maatalouskoneiden ohjaamisen avustamiseen ja automatisointiin. Tarkoitus on ohjata pellolla kulkevaa traktoria tai muuta työkonetta suoria ajouria tai työleveyden verran kasvavaa etäisyyttä pellon reunaa seuraten. Tämä parantaa työn jälkeä kun kone pystyy GPS-ohjatusti tarkempaan seurantaan kuin ihminen.

Avoin ratkaisu on huomattavasti edullisempi kuin kaupalliset toteutukset ja mahdollista sovittaa myös vanhempiin traktoreihin ja sitäkautta välttyä toimivan koneen korvaamisella uudemmalla. Traktorin lisäksi järjestelmää on toki mahdollista hyödyntää muidenkin työkoneiden, esimerkiksi puimurin kanssa, vaikka pääasiassa jatkossa tässä käytän termiä traktori ohjattavasta laitteesta.

Tämä sivusto on [Fuugin](https://fuug.fi/) säätiön [tuella](https://fuug.fi/2021/elokuussa-2021-myonnetyt-apurahat/) työn alla oleva (11/2021) suomenkielinen ohjepaketti järjestelmään ja sen käyttöönottoon. Tavoitteena on koota oman traktorin automatisointiin tarvittava tietopaketti, jossa pohjatiedoiksi riittää perusteet sähköistä ja tietotekniikasta, sekä toki halu harrastaa, oppia ja raketentaa työtä helpottava kokonaisuus.

Tämä dokumentaatio on vapaa käytetäväksi ja edelleen muokattavaksi, kuhan alkuperäinen tekijä Teppo Rekola mainitaan ja versiot jaetaan samalla lisenssillä. Lisenssi CC-BY SA 4.0 https://creativecommons.org/licenses/by-sa/4.0/deed.fi

Komentteja ja ehdotuksia tähän versioon otetaan mielellään vastaan, etunimi . sukunimi @iki.fi


## sisältö

Dokumentaatio on tuotettu pääasiassa ohjelmiston versiolle 5 (syksy 2021), mutta suurin osa laitteistoon ja rakentamiseen liittyvästä sisällöstä on lähes versioriippumatonta. Toki laitteistokin kehittyy versioiden myötä, joten tuoreet yksityiskohdat on aina syytä tarkistaa.

* [Linkkejä ja lisätietoa](linkit.md)
	* järjestelmän oma dokumentaatio
	* käyttäjäryhmät
	* komponenttien hankintapaikat

* [Osaluettelo](osat.md)

* [GPS-tukiasema ja paikannus](RTK-GPS.md)
	* RTK-paikannuksen perusteet
	* Antennin asennuspaikka
	* Softa, RaspberryPi-image
	* rtk2go
	* Poe-sähkönsyöttö tukiasemalle
	* Gps:n asetukset
	* Tukiaseman paikan määritys
	* Rtk2go oikeat parametrit, lähettävät viestityypit



* [Komponentit traktorissa](traktori.md)
	* Gps:n firmware-asetukset
	* Windows-asetukset

	* Piirilevyn tilausprosessi
	* Komponenttien hankinta

	* Anturien sijoitus
	* Akselianturin vivusto
	* Gps-antennin paikka
	* Rattirulla
	* Liittimet
	* Asennusjärjestys
	* Arduinon ohjelmointi
	* Testausvaiheet

	* Traktorin omat anturit, canbus, hydrauliikka

* [Ohjelmisto ja käyttö](ohjelmisto.md)
	* Ntrip asetukset
	* Traktorin mitat
	* Työkoneen asetukset
	* Ohjauksen parametrit
	* Status-näkymä
