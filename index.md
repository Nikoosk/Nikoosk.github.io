# Ticorporate DemoLab - Kevät 2020

## 1. Johdanto

Tämän dokumentin tarkoitus on kuvata ja havainnollistaa kevään aikana oppimaani sekä tuottamaani sisältöä peliprojektiimme. Projekti kulkee nimellä [Nihonshoki Teien](http://nihonshokiteien.ticorporate.fi/ "Nihonshoki Teien kotisivut"). Projektissa kannoin vastuun koodista, sekä kaikesta mikä tapahtuu Unityn päässä. Tässä dokumentissa keskityn erityisen tarkasti toteutuksiin, jotka ovat olleet minulle täysin uusia, tai olen niistä erityisen tyytyväinen. DemoLabin aikana pääsin haistelemaan hieman UI-suunnittelua, mutta pääsääntöisesti olen tuottanut koodia, vastannut Unityn päässä työskentelystä, sekä opetellut käyttämään [YarnSpinner](https://yarnspinner.dev/) -työkalua osana tarinankerrontaa sekä pelilogiikkaa.  

Kurssin alussa osaamiseni koskien Unityä sekä koodaamista olivat todella rajalliset. Unityn kanssa aikasemmat kokemukset olivat lähinnä netistä löytyvien ohjeiden seuraamista sekä valmiiden palasten käyttämistä. Projektin alussa totesin että dialogin näyttäminen pelissä onkin suurempi haaste, mitä osasin aavistaa. Edellä mainittu YarnSpinner on ollut korvaamaton apu Unity-integraatiollaan sekä helppokäyttöisellä web-editorillaan. ![Kuva editorista](https://Nikoosk.github.io/yarnEditor.png)  

## 2. Oppimistavoitteet 

Yksinkertaisuudessaan halusin oppia pelien toiminnasta sekä niiden tekemisestä. pääsääntöisesti koodin puolelta. Tavoitteenani oli oppia tuottamaan toimivia ominaisuuksia, jotka tarvittaessa ovat skaalautuvia sekä uudelleenkäytettävissä. Ehdottomasti tärkein tavoite oli päästä irti kovakoodaamisesta, sekä tuottaa selkeää ja suht helposti ymmärrettävää koodia.   

## 3. Oppiminen
Projektin alussa minulla oli paha tapa kommentoida koodia huonosti tai ei lainkaan. Ajattelin, kun kerta olen ainoa joka tämän koodin kanssa työskentelee, kommentointi olisi turhaa sillä kyllähän minä omaa koodiani ymmärrän. Olin väärässä, ja koodin kommentointi on erittäin tärkeää ja helpottaa myöhemmin projektin aikana vanhojen toiminnallisuuksien parantamista/korjaamista. Ja onhan se myös hyvä käytäntö.  
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

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/Nikoosk/Nikoosk.github.io/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
