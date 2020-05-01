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
- Kameraefektit  

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
