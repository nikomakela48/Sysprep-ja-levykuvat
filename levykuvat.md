
 # Valmiin levykuvan ottaminen Windowsista
 ##### Windowsin asennuksen automatisointia

-  Aloitetaan Windowsin asennus normaalisti asennusmediasta, valitaan alueasetukset ja mille levylle asennetaan.
 
- Kun ensiasennusvelho aukeaa jossa aletaan kyselemään että kuka olet ja mistä tulet, painetaan *CTRL+SHIFT+F3*
 >Tällä päästään Audit-tilaan, jossa päästään tekemään haluttuja muokkauksia.
 
- Tässä tilassa voidaan asentaa laiteajureita, ohjelmia joita halutaan tietokoneessa olevan ns. automaattisesti, päivityksiä ja mahdollisesti esim. bginfo jolla saadaan tietokoneesta tietoja työpöydälle.

##### Vastaustiedostot
- Vastaustiedostojen tarkoitus on automatisoida tietokoneen käyttöönottoa.
- Niiden tekemiseen voidaan käyttää Windows System Image Manageria, tai yksinkertaisiin vastaustiedostoihin on olemassa myös nettisivuja, joissa voidaan luoda vastaustidostoja.
> Vastaustiedostoihin voidaan määrittää erilaisia asetuksia, sen avulla saadaan luotua automaattisesti useita käyttäjiä ja ohitettua OOBE, eli ensiasennusvelho.

##### Sysprepin käyttö
- Syspreppiä voidaan käyttää joko graafisen käyttöliittymän tai komentokehotteen kautta. Jos ei tarvita käyttää vastaustiedostoa, voidaan käyttää graafista käyttöliittymää. Tämä aukeaa Audit-tilassa jokaisen käynnistyksen yhteydessä, tai avaamalla sysprep.exe ohjelma.
> Jos tietokoneessa on keskeneräisiä päivityksiä, ei sysprep suostu toimimaan.
- Jos tulevaa levykuvaa aiotaan käyttää muissakin tietokoneissa tai halutaan tehdä uusia virtuaalikoneita levykuvalla, tulee käyttää _Generalize_ vaihtoehtoa, joka poistaa yksilölliset tiedot levykuvasta pois.
- Jos käytetään vastaustiedostoa, se siirretään C:\Windows\System32\Sysprep hakemistoon, jonka jälkeen avataan komentokehote tässä kansiossa.
- Ajetaan komento sysprep.exe /generalize /shutdown /oobe /unattend:haluttutiedosto.xml

##### Levykuvan ottaminen Virtualboxissa

- Sysprep ohjelman ajamisen jälkeen kone sammuu, **älä käynnistä**. Virtualboxissa klikataan konetta hiiren oikealla ja klikataan Export to OCI. valitaan muodoksi Open Virtualization Format 2.0 ja valitaan minne levykuva halutaan tallentaa. Painetaan next jolloin voidaan halutessaan lisätä tietoja koneesta. Sen jälkeen voidaan painaa Export. Saat valitsemaasi sijaintiin levykuvan.

##### Levykuvan käyttäminen Virtualboxissa

- Virtualboxissa klikataan File -> Import Appliance. Valitaan levykuva ja halutut asetukset. Kone ilmestyy virtuaalikoneiden listaan.
- Kun kone käynnistetään, siinä pitäisi olla valmiina asennetut ohjelmat ja muut muokkaukset, ja jos käytettiin vastaustiedostoa, pitäisi koneen ikäänkuin itsestään mennä lukitusnäytölle josta päästään kirjautumaan kuin mitään ei olisi koskaan tapahtunut.
 