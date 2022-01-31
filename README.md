# AgOpenGps-ohje

[AgOpenGPS](https://github.com/farmerbriantee/AgOpenGPS) on avoin ohjelmisto- ja laitteistokokonaisuus maatalouskoneiden ohjaamisen avustamiseen ja automatisointiin. Tarkoitus on ohjata pellolla kulkevaa traktoria tai muuta työkonetta suoria ajouria tai työleveyden verran kasvavaa etäisyyttä pellon reunaa seuraten. Tämä parantaa työn jälkeä kun kone pystyy GPS-ohjatusti tarkempaan seurantaan kuin ihminen.

Avoin ratkaisu on huomattavasti edullisempi kuin kaupalliset toteutukset ja mahdollista sovittaa myös vanhempiin traktoreihin ja sitä kautta välttyä toimivan koneen korvaamisella uudemmalla. Traktorin lisäksi järjestelmää on toki mahdollista hyödyntää muidenkin työkoneiden, esimerkiksi puimurin kanssa, vaikka pääasiassa jatkossa tässä käytän termiä traktori ohjattavasta laitteesta.

Tämä sivusto on [Fuugin](https://fuug.fi/) säätiön [tuella](https://fuug.fi/2021/elokuussa-2021-myonnetyt-apurahat/) työn alla oleva (1/2022) suomenkielinen ohjepaketti järjestelmään ja sen käyttöönottoon. Tavoitteena on koota oman traktorin automatisointiin tarvittava tietopaketti, jossa pohjatiedoiksi riittää perusteet sähköistä ja tietotekniikasta, sekä toki halu harrastaa, oppia ja rakentaa työtä helpottava kokonaisuus.

Tämä dokumentaatio on vapaa käytettäväksi ja edelleen muokattavaksi, kuhan alkuperäinen tekijä Teppo Rekola mainitaan ja versiot jaetaan samalla lisenssillä. Lisenssi CC-BY SA 4.0 https://creativecommons.org/licenses/by-sa/4.0/deed.fi

Kommentteja ja ehdotuksia tähän versioon otetaan mielellään vastaan, etunimi . sukunimi @iki.fi


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
	* vaihtoehtoinen asennus muunlaiselle tietokoneelle
	* olemassa olevan tukiasemaverkoston käyttäminen



* [Komponentit traktorissa](traktori.md)
	* Gps:n firmware-asetukset

	* Piirilevyn tilausprosessi

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
	* Windows-asetukset
	* Traktorin mitat
	* Työkoneen asetukset
	* Ohjauksen parametrit
