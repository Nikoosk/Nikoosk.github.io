# Ticorporate DemoLab - Kevät 2020

## 1. Johdanto

Tämän dokumentin tarkoitus on kuvata ja havainnollistaa kevään aikana oppimaani sekä tuottamaani sisältöä peliprojektiimme. Projekti kulkee nimellä [Nihonshoki Teien](http://nihonshokiteien.ticorporate.fi/ "Nihonshoki Teien kotisivut"). Projektissa kannoin vastuun koodista, sekä kaikesta mikä tapahtuu Unityn päässä. Tässä dokumentissa keskityn erityisen tarkasti toteutuksiin, jotka ovat olleet minulle täysin uusia, tai olen niistä erityisen tyytyväinen. DemoLabin aikana pääsin haistelemaan hieman UI-suunnittelua, mutta pääsääntöisesti olen tuottanut koodia, vastannut Unityn päässä työskentelystä, sekä opetellut käyttämään [YarnSpinner](https://yarnspinner.dev/) -työkalua osana tarinankerrontaa sekä pelilogiikkaa.  

Kurssin alussa osaamiseni koskien Unityä sekä koodaamista olivat todella rajalliset. Unityn kanssa aikasemmat kokemukset olivat lähinnä netistä löytyvien ohjeiden seuraamista sekä valmiiden palasten käyttämistä. Projektin alussa totesin että dialogin näyttäminen pelissä onkin suurempi haaste, mitä osasin aavistaa. Edellä mainittu YarnSpinner on ollut korvaamaton apu Unity-integraatiollaan sekä helppokäyttöisellä web-editorillaan. ![Kuva editorista](https://Nikoosk.github.io/yarnEditor.png)  

### Päätyön osuus  

Päätyönä tein kurssin aikana pelitekniikkaa, eli vastasin koodista ja Unitystä. Tätä portfoliota kasatessa olen käyttänyt **400** tuntia yhteensä kurssin aikana työskentelyyn, joista ehdottomasti suurin osa on mennyt koodaamiseen ja muun tiimin tekemien tuotoksien integroimiseen osaksi projektiamme. Omaa koodia olen tuottanut yhteensä noin **2200** riviä, joista suuri osa (**n. 470**) on yksinään *YarnCommands.cs*-skriptissä. *YarnCommands.cs* sisältää kaikki custom-komennot joita peli käyttää dialogin aikana, ja erilaisia komentoja on yhteensä toteutettu 11 kappaletta.  

### Sivutyö  

Sivutyönä oli alunperin testaaminen, mutta projektin ainoana pelitekniikka -ihmisenä työmäärä päätyön parissa oli niin valtaisa, että aikaa sivutyölle ei vain löytynyt.  



## 2. Oppimistavoitteet 

Yksinkertaisuudessaan halusin oppia pelien toiminnasta sekä niiden tekemisestä. pääsääntöisesti koodin puolelta. Tavoitteenani oli oppia tuottamaan toimivia ominaisuuksia, jotka tarvittaessa ovat skaalautuvia sekä uudelleenkäytettävissä. Ehdottomasti tärkein tavoite oli päästä irti kovakoodaamisesta, sekä tuottaa selkeää ja suht helposti ymmärrettävää koodia.   

## 3. Oppiminen
Projektin alussa minulla oli paha tapa kommentoida koodia huonosti tai ei lainkaan. Ajattelin, kun kerta olen ainoa joka tämän koodin kanssa työskentelee, kommentointi olisi turhaa sillä kyllähän minä omaa koodiani ymmärrän. Olin väärässä, ja koodin kommentointi on erittäin tärkeää ja helpottaa myöhemmin projektin aikana vanhojen toiminnallisuuksien parantamista/korjaamista. Ja onhan se myös hyvä käytäntö.  

Tavoitteiden ulkopuolelta olen oppinut pyytämään apua ongelmatilanteissa, sekä toimimaan osana tiivistä ryhmää, jossa jokaisella on tietty vastuualue ja projektin eteneminen on kiinni kaikkien panostuksesta.Etätyöskentelyyn asennoituminen oli aluksi hankalaa, mutta jahka sai muodostettua rutiinin arkeen, alkoi työntekeminen rullata. Huomasin olevani kotona työskennellessä huomattavasti tehokkaampi, ja jopa tupakointi vähentyi kun ketään ei tullut puolen tunnin välein toimiston ovelle kysymään tupakkaseuraksi.  

Projektin aikana fiilis siitä, että haluaisin tehdä pelejä jatkossa ammatikseni ja oppia uutta kehittäjänä ovat vahvistuneet. Itselle uuden ominaisuuden ja toiminnallisuuden löytäminen täyttää mieleni ideoilla, miten voisin hyödyntää tätä pelissä ja millaisia mekaanikoita voisin luoda niillä.  
### 3.1 Oivallukset
Projektin lopun häämötellessä tajusin, että toiminnallisuutta olisi voinut hajauttaa useampaan skriptiin ns bloatin välttämiseksi. Projektissa on useita skriptejä, joiden pituus on reippaasti yli 300 riviä. Ongelmakohtien löytäminen vaikeutuu skriptien pidetessä ja yhden virheen seuraukset ovat suurempia pitkässä "spagettikoodissa" kuin täsmätoimintaskriptissä.  

Ominaisuudet, jotka ajattelin projektin alussa olevan lähes mahdottomia toteuttaa, sain loppua kohden ratkaistua yleensä päivässä tai parissa.  

Tallennussysteemi aiheutti todella paljon tuskaa ja turhautumista. Skriptit olivat alunperin tehty ilman ajatusta tallentamisesta ja niiden uudelleentekeminen olisi ollut liian iso urakka projektin aikapuitteissa. Käytin yhteensä kaksi viikkoa "oikeaoppisen" tallentamisen tutkimiseen, sekä yrityksiin toteuttaa. Lopulta luovutin ja tein "huonon tavan" mukaisesti järjestelmän, joka tallentaa tarinan etenemisen Player.Prefseihin.  

Työkalujen valinta on myös ollut todella tärkeää, esimerkkinä animaatiot sekä kameratehosteet. Unityn oma animaattori on hankala käyttää, joten [Ilkan](https://github.com/Lefti90) suosituksesta otin käyttöön [LeanTweenin](https://github.com/dentedpixel/LeanTween), jolla yksinkertaisten tehosteiden ja animaatioiden tekeminen on ollut todella helppoa ja nopeaa.
## 4. Suuret osa-alueet
Kaikki Unityn päässä tehty työ on omaa, mutta pyrin poimimaan tärkeimmät kokonaisuudet tähän ja kertomaan niistä laajemmin.

- Tallentaminen 
- Dialogi 
- Yarn komennot 
- Onnenpyörä 
- Taistelumekaanikka  



### 4.1 Tallentaminen
Tallentaminen oli alunperin tarkoitus tehdä kerralla oikeaoppisesti käyttäen BinaryFormatteria ja Filestreamia. Mutta kahden viikon tuskailun jälkeen tuloksena syntyi vain tyhjä tiedosto sekä kasoittain virheilmoituksia. Lopulta päätin luovuttaa ja tehdä "huonolla tavalla" käyttäen Player.Prefs.  

Etenemisen tallentaminen tapahtuu Yarn-dialogin sisällä olevaa itsetehtyä komentoa "Save" ```<<Save Player #sceneID>>```, jossa ```Save``` on komennon nimi, ```Player``` viittaa GameObjectiin, jossa YarnCommands.cs -skripti on kiinni, ja viimeisenä osana ```#sceneID``` on numero, joka on määritetty vastaamaan tiettyä Nodea YarnDialogissa. Komento kutsuu YarnCommands.cs -skriptissä olevaa metodia ```SaveProgress(string _value)```, joka yksinkertaisuudessaan on seuraavanlainen:
```csharp
[YarnCommand("Save")]
public void SaveProgress(string _value)
   {
      PlayerPrefs.SetInt("DCP", int.Parse(_value));
   }
```
Etenemisen automaattinen lataus on monimutkaisempi toteutus, jossa SaveLoad.cs -skriptin ```Awake()``` -metodissa haetaan pelin käynnistyessä Player.Prefseistä "DCP"-avain (DCP = **D**ialogue**C**om**P**leted) ja sen arvoa verrataan ennaltamäärittettyihin dialogi Nodeihin:
```csharp
void Awake()
   {
      if (PlayerPrefs.HasKey("DCP"))
         {
            Debug.Log("Found saved dialogue with id: " + PlayerPrefs.GetInt("DCP"));
            SavedID = PlayerPrefs.GetInt("DCP");

            switch (SavedID)
                {
                    case 1:
                        VariableLoader.StartNode = "Start";
                        break;
                    case 2:
                        VariableLoader.StartNode = "Tenko";
                        break;
                    case 3:

                        break;
                }
                DialogueRunner.GetComponent<DialogueRunner>().startNode = VariableLoader.StartNode;
                Debug.Log("Node name: " + VariableLoader.StartNode);
                

            }
        }
```
Pelin asetukset sekä pelaajan nimi tallennetaan vastaavalla tavalla Player.Prefs -avaimiin ```textSpeed``` (tallentaa dialogin tekstin vieritysnopeuden), ```ASDelay``` (tallentaa dialogin automaattisen siirtymisen seuraavaan riviin viiveen sekunteina) sekä ```name``` (tallentaa pelin alussa pelaajan asettaman nimen kirjoituskentästä).  

### 4.2 Dialogi
Narratiivi-tiimiltä tullut valmis dialogi ei sellaisenaan käy suoraan Yarniin, vaan siihen pitää lisätä komennot, tehosteet sekä kohtauksesta riippuen erilaiset muuttujat ja siirtymät Nodejen välillä. Kaikkiaan itseluomiani dialogin sisällä käytettäviä komentoja on yhteensä 12 kappaletta, ja ne vastaavat mm. puhujan nimen vaihtamisen nimilaatikkoon, hahmojen ilmeiden vaihtamisen, taustan vaihtamisen, kameran zoomauksen jne.  

Kaikki efektit ja siirtymät dialogin aikana on toteutettu YarnCommandeilla, joita ketjuttamalla saadaan aikaan erilaisia efektejä, kuten esimerkiksi taustan vaihto.
<video alt="Video from Gyazo" muted playsinline controls><source src="https://i.gyazo.com/d3be3540e7b79efa2366ff141509a104.mp4" type="video/mp4" /></video>
Taustan vaihtoon on ketjutettu yhteensä 5 komentoa:  
```
<<effect Player full_fade>>
<<wait 2>>
<<bgchange Player bg2>>
<<effect Player full_unfade>>
<<wait 1>>
```
```<<effect Player full_fade>>``` laittaa koko ruudun peittävän mustan kuvan alpha-arvon yhteen, tehden ruudusta mustan, ```<<wait 2>>``` pysäyttää Yarnin / dialogin kahdeksi sekunniksi, jonka jälkeen ```<<bgchange Player bg2>>``` vaihtaa taustakuvan, ```<<effect Player full_unfade>>``` laittaa ruudun peittävän kuvan taas läpinäkyväksi ja lopulta ```<<wait 1>>``` odottaa yhden sekunnin ennenkuin dialogi jatkuu. Tuloksena on sulava taustanvaihto ilman, että pelaajalta jää yhtään dialogia näkemättä.  

"Kameran" liikutus ja zoomaus on toteutettu hieman erikoisella tavalla. Itse kamera ei oikeasti tee mitään, vaan kuvaa liikutellaan ja venytetään tarpeen mukaan.  

<video alt="Video from Gyazo" width="428" muted playsinline controls><source src="https://i.gyazo.com/fdcdf0894a9298b1ba73e94dfcfaaed0.mp4" type="video/mp4" /></video>

### 4.3 Yarn custom komennot
Yarnin sisäiset komennot toimivat seuraavalla tavalla: ```<<komento Objekti arvo>>```, jossa ```komento``` on skriptissä määritetty seuraavanlaisesti: 
```csharp
[YarnCommand("Komento")]
public void Metodi(string arvo)
{
        // mitä komento tekeekään
}
```
Komennossa ```Objekti```-kohta täsmentää, mistä Unityn GameObjectista YarnSpinner etsii skriptiä. Viimeisenä ```arvo``` on stringinä annettu muuttuja, joka välitetään skriptille.  

Monimutkaisin komento on ehdottomasti kameraefekteistä vastaava ```<<effect Player #efekti>>```, joka yksinään vastaa 11 eri efektistä.
Komento kokonaisuudessaan on tällainen: 
```csharp
[YarnCommand("effect")]
public void CameraEffect(string effect)
{
   int _topbg = BackgroundHolder.transform.childCount - 1; 
   var _background = BackgroundHolder.transform.GetChild(_topbg).GetComponent<RectTransform>();
   var _fullscreen = FullScreenFade.GetComponent<RectTransform>();
   // Pan camera left
   if (effect == "pan_left")
   {
      LeanTween.moveX(_background, 575f, 1f);
   }
   // Pan camera rigth
   else if (effect == "pan_right")
   {
      LeanTween.moveX(_background, 0, 1f);
   }
   // Zoom camera in
   else if (effect == "zoom_in")
   {
      LeanTween.scale(_background, _background.localScale * 1.5f, 1f);
   }
   // Zoom out effect
   else if (effect == "zoom_out")
   {
      LeanTween.scale(_background, _background.localScale / 1.5f, 1f);
   }
   // Short shake, only once
   else if (effect == "shake_short")
   {
      LeanTween.moveX(_background, 50f, 0.5f).setEasePunch();          
   }
   // Long shake, multiple times
   else if (effect == "shake_long")
   {
      LeanTween.moveX(_background, 70f, 0.6f).setEasePunch().setLoopPingPong(2);
   }
   // Turn background darker by halving RGBA-values
   else if (effect == "darker")
   {
      LeanTween.color(_background, Color.gray, 2f);
   }
   // Turn background black by setting RGBA-values to zero
   else if (effect == "fade_black")
   {
      LeanTween.color(_background, Color.black, 2f);
   }
   // Turn background normal
   else if (effect == "unfade")
   {
      LeanTween.color(_background, Color.white, 2f);
   }
   // Fades full screen to black
   else if (effect == "full_fade")
   {
       Image r = FullScreenFade.GetComponent<Image>();
       LeanTween.value(FullScreenFade, 0, 1, 1).setOnUpdate((float val) =>
       {
          Color c = r.color;
          c.a = val;
          r.color = c;
          });
       }
    // Unfades full screen
    else if (effect == "full_unfade")
    {
       Image r = FullScreenFade.GetComponent<Image>();
       LeanTween.value(FullScreenFade, 1, 0, 1).setOnUpdate((float val) =>
       {
          Color c = r.color;
          c.a = val;
          r.color = c;
          });
       }
   }
```
### 4.4 Onnenpyörä
<video alt="Video from Gyazo" muted playsinline controls><source src="https://i.gyazo.com/1228e6e9bbc1d40457d16866bd1634e0.mp4" type="video/mp4" /></video>  

Onnenpyörä on toteutettu käyttäen ```LeanTween.rotate(...)``` -metodia, jossa pyörän pyörimä astemäärä on satunnainen luku väliltä 1440 - 4320. Pyörä pyörii siis vähintään 4 kierrosta ja maksimissaan 12.  

Kuten videossa näkyy, pelaaja saa 8h välein vapaan pyöräytyksen sekä päivittäin uusiutuvat kaksi pyöräytystä.  

Onnenpyörän palkinnot on jaettu 62:een osaan, joiden todennäköisyydet ovat:  
- Common, 30/62 
- Uncommon, 18/62 
- Rare, 10/62 
- Legendary, 4/62  

Pyörän pyöräytyksestä vastaa seuraava koodipätkä  
```csharp 
...
// Generates random value for degrees of turn
float random = Random.Range(1439, 4321);
Debug.Log(System.DateTime.Now);
Debug.Log(random);
RewardRoll = random;
// Rotate the wheel
LeanTween.rotate(Wheel.GetComponent<RectTransform>(), random, 5f).setEaseOutExpo();
GetComponent<Timer>().SaveSpinTime();
TextLeft.text = "Next spin at: " + VariableLoader.spinTime;
SpinReward();
...
```  
### 4.5 Taistelu
<video alt="Video from Gyazo" muted playsinline controls><source src="https://i.gyazo.com/dd525096fa0f855bc00ecf353ed40208.mp4" type="video/mp4" /></video>  
Taistelun alussa peli katsoo pelaajahahmon sekä vihollisen nopeusarvot, ja päättää niiden perusteella kumpi liikkuu ensin. Taistelulogiikka on todella yksinkertainen "lyö toista kunnes se kuolee" -tyylinen.  
```csharp
// Combat coroutine
        IEnumerator HitS()
        {
            CR_Running = true;
            CharacterStats mcStats = player.gameObject.GetComponent<CharacterStats>();
            Enemy enemy = enemyHolder.GetComponentInChildren<Enemy>();
           
            // Compares speeds and decides who goes first in combat
            if (enemy.Speed < mcStats.Speed)
            {
                LeanTween.moveX(Hyvis.GetComponent<RectTransform>(),700f, 1f).setEasePunch();
                enemy.Hit(mcStats.AtkPhys);
                yield return new WaitForSecondsRealtime(1);
                mcStats.Hit(enemy.AtkPhys);
                LeanTween.moveX(enemyHolder.transform.GetChild(0).GetComponent<RectTransform>(), 0f, 1f).setEasePunch();
                yield return new WaitForSecondsRealtime(1);
                CR_Running = false;
            }
            else
            {
                LeanTween.moveX(enemyHolder.transform.GetChild(0).GetComponent<RectTransform>(), 0f, 1f).setEasePunch();
                mcStats.Hit(enemy.AtkPhys);
                yield return new WaitForSecondsRealtime(1);
                LeanTween.moveX(Hyvis.GetComponent<RectTransform>(), 700f, 1f).setEasePunch();
                enemy.Hit(mcStats.AtkPhys);
                yield return new WaitForSecondsRealtime(1);
                CR_Running = false;
            }
        }
```
Taistelun aikaset lyöntianimaatiot on tehty LeanTweenillä, ja vihollisen idle-animaatio on tehty [DragonBones](https://docs.egret.com/dragonbones)illa.  

Pelaaja voi myös avata inventaarionsa, ja valita käytettäviä esineitä taistelun ajaksi. Esineet antavat bonusta hahmon statseihin, kuten nopeuteen, elämäpisteisiin, puolustukseen sekä hyökkäykseen.  
<video alt="Video from Gyazo" muted playsinline controls><source src="https://i.gyazo.com/bd399f11b60a2d9ea6198354d2d71f36.mp4" type="video/mp4" /></video>  

Valitettavasti pelin scopen kaventuessa, sekä ajan loppuessa taistelu, sekä inventaario jäivät viimeistelemättä. Inventaario on toteutettu listana, ja esineet on Scriptable Objecteja, joita siirretään passiivisesta listasta (inventaario) aktiiviseen (valitut esineet). Inventaario on toteutettu seuraamalla [MVCode](https://www.mvcode.com/lessons/unity-rpg-inventory-system-jamie)n tutoriaalia, ja muokkaamalla siitä omaan käyttöön sopiva. Tutoriaali ei suoraan antanut haluamaani ratkaisua, vaan jouduin muokkaamaan siitä tarvitsemani. Aktiivisten esineiden lista on pohjimmiltaan sama kuin itse inventaario, mutta logiikka esineiden siirtämiseksi listalta toiseen on itse tehty. Esineitä ei myöskään voi olla kuin 3 valittuna kerrallaan. 

## 5. Muut hienot ominaisuudet

__Kosketuksen visuaalinen havainnollistaminen__  

![Image from Gyazo](https://i.gyazo.com/16f8bc0c3c78b28c9354669dfb12b353.png)  
Tämä pieni läpinäkyvä pallo on aktiivinen ainoastaan kun peli tunnistaa puhelimen näytöltä kosketuksen, ja se seuraa kosketusta näytöllä. TouchIndicator.cs -skriptin ```Update()```-loopissa on metodi, joka tarkistaa, että tunnistaako puhelin kosketusta. Jos kosketus tunnistetaan, se laittaa indikaattoripallon aktiiviseksi ja siirtää sen sijainnin kosketuksen koordinaatteihin. Vastaavalla tavalla kosketuksen loppuessa indikaattoripallo deaktivoituu.  
```csharp
// Check for touch
if (Input.touchCount > 0)
{
   Touch touch = Input.GetTouch(0);
   Vector2 TouchPos = Input.GetTouch(0).position;
   // Move touch indicator to coordinates of touch position
   if (touch.phase == TouchPhase.Moved)
   {
      position.y = TouchPos.y;
      position.x = TouchPos.x - 0.7f;
      touchIndicator.transform.position = position;
   }
   
   // Set touch indicator active when detecting touch input
   if (touch.phase == TouchPhase.Began)
   {
      touchIndicator.SetActive(true);
      position.y = TouchPos.y;
      position.x = TouchPos.x;
      touchIndicator.transform.position = position;
   }
   // Deactive touch indicator when touch has ended
   if (touch.phase == TouchPhase.Ended)
   {
      touchIndicator.SetActive(false);
   }

}
```
__Kuvanvaihto yhdistettynä kameraefektiin tarinan visualisoimiseksi__  

<video alt="Video from Gyazo" muted playsinline controls><source src="https://i.gyazo.com/d4bf59d92819cc35b1ff29e9017f43db.mp4" type="video/mp4" /></video>  
```
<<bgchange Player bg3>>
<<effect Player shake_short>>
```  


Kyseinen efekti on saatu aikaan ketjuttamalla taas Yarn -komentoja ```<<bgchance Player bg3>>``` vaihtaa kuvan ja heti perään ```<<effect Player shake_short>>``` täräyttää juuri vaihdettua kuvaa.  

__Tekstin nopeus ja automaattisen vierityksen asetukset__  

<video alt="Video from Gyazo" muted playsinline controls><source src="https://i.gyazo.com/580c6f5691f8bcd98d1904a81724f85b.mp4" type="video/mp4" /></video>  

Tekstin nopeutta sekä automaattisen vierityksen viivettä voidaan säätää joko dialogin aikana asetusikkunasta, jonka saa auki PC -buildissa painamalla _Escape_-näppäintä ja Androidilla _Takaisin_-painikkeella, tai pelin käynnistäessä päävalikon asetuksista. Käyttäjän valitsemat asetukset tallentuvat Player.Prefseihin ja latautuvat sieltä automaattisesti pelin käynnistyessä.  

<video alt="Video from Gyazo" muted playsinline controls><source src="https://i.gyazo.com/1ed89c2e712b30c65ec6073a0f37dfa0.mp4" type="video/mp4" /></video>  

__Puhujan nimen vaihto tekstikenttään dialogissa__  

<video alt="Video from Gyazo" muted playsinline controls><source src="https://i.gyazo.com/7bb24c62fbc4ddc9811b4378f3534a5b.mp4" type="video/mp4" /></video>  

Pelin alussa pelaajan asetettava hahmolleen nimi, joka näkyy hahmon puhuessa, sekä pelin hahmojen puhutellessa pelaajaa. Dialogikentän yläpuolella on pieni tekstikenttä, joka kuvastaa puhujaa. Pelihahmon ajatellessa, kenttä on tyhjä. Nimen vaihtaminen tapahtuu Yarnin dialogin sisältä itsetehdyllä komennolla ```<<speaking Player #nimi>>```.  

```csharp
[YarnCommand("speaking")]
public void SetSpeaker(string name)
{

   if(name == "MC")
   {
      name = PlayerPrefs.GetString("name");
      Debug.Log("Speaker name set to " + name);
      SpeakerName.text = name;
   }
   else if(name == "Boss")
   {
      SpeakerName.text = "Mr. Ashiya";
      Debug.Log("Speaker name set to " + SpeakerName.text);
   }
   else if (name == "clear")
   {
      SpeakerName.text = null;
   }
   else
   {
      SpeakerName.text = name;
      Debug.Log("Speaker name set to " + name);
   }
}
```  
Komentoa luodessa piti ottaa kaksi poikkeusta huomioon. Pelaajan nimi ei ole ennaltamääritelty, joten dialogin keskeltä sitä kutsutaan arvolla __MC__. Pelaajan nimi haetaan Player.Prefseistä, mihin se on tallennettu pelaajan asettaessa nimensä. Tarinan päähahmon pomon nimi piti myös tehdä erityistapauksena, sillä Yarn yritti palauttaa välilyönnillä erotetun nimen string-taulukkona. Pomoa kutsutaan dialogista arvolla __Boss__.  
Viimeinen poikkeus on arvo __clear__, jolla tyhjennetään nimikenttä narratiivin kerrontaa varten.  

__Overworld Map__  

<video alt="Video from Gyazo" muted  playsinline controls><source src="https://i.gyazo.com/7f63e9f43db5c41f0f2f4ae6803f4206.mp4" type="video/mp4" /></video>  
Kartta koostuu on neljästä napista, ja taustasta. Nappien highlight on toteutettu OnPointerEventeillä, ja nappien animaatio LeanTweenillä. Nappien korostamisen koodi on yksinkertaisuudessaan tässä:  
```csharp
 public void OnPointerEnter (PointerEventData eventData)
    {
        mouser_over = true;
        Debug.Log("Mouse over");
        LeanTween.scale(gameObject, scale, 0.2f);
    }

    public void OnPointerExit(PointerEventData eventData)
    {
        mouser_over = false;
        Debug.Log("Mouse exit");
        LeanTween.scale(gameObject, downscale, 0.2f);
    }
```  


__Kette__  

![Kette](https://Nikoosk.github.io/phTenko_Scene1_smile.png)  
Kette oli alunperin vain placeholderiksi tarkoitettu nopea piirros, mutta kehkeytyi meemiksi, projektimme maskotiksi sekä lopulta tyyliteltynä versiona t-paitaan kuvastamaan projektiamme. Kette on myös ansainnut maailmanlaajuista tunnustusta.  
![Image from Gyazo](https://i.gyazo.com/fc935024c0e980fe1bba650025a4a6e7.png)  


## 5. Tulevaisuus  

Pyrin kehittymään koodajana ja pelikehittäjänä jatkossakin, suunnitelmissa olisi toteuttaa kesän aikana oma peliprojekti itsenäisesti hyödyntäen DemoLabin aikana oppimiani taitoja. Mitään valmista ideaa ei vielä ole, mutta mielessäni on nippu mielenkiintoisia mekaniikoita joita haluan hyödyntää ja kokeilla, vaikka edes TechDemon muodossa. Unelmana on tehdä peli, jonka jokainen ominaisuus ja mekaniikka ovat minulle ylpeydenaihe, ja josta mielellään myös muut ihmiset olisivat innoissaan.  

Projektista jäi käteen pelikehityksestä varsin hajanainen osaamisalue. Projektin aikana ei tarvinnut tehdä perinteisiä peliin liittyviä toiminnallisuuksia, kuten hahmon tai kameran liikkumista, vuorovaikutusta pelimaailman ja objektien kanssa, tai itse pelikentän suunnittelua. Osaamista kertyi vahvasti narratiivin linkittämisestä osaksi pelin kulkua, dialogien lisääminen YarnSpinnerillä, valikoiden ja asetusten tekeminen ja suunnittelu, sekä kanvaksien toiminta ja manipulointi skripteistä.  



## Ota yhteyttä  

L4234@student.jamk.fi  
[Instagram](https://www.instagram.com/nikoosk/)  
[Twitter](https://twitter.com/TheNikoosk)  
[Steam](https://steamcommunity.com/id/nikoosk/)  
Discord: Nikoosk#1904  
