# Les 4.3 Animeren, feedbacksessie

## 1. Instructie feedbacksessie

## 2. Animeren: theorie
### 2.1 CSS selectoren
Naslagwerk **[CSS selectoren en properties - almanac](https://css-tricks.com/almanac/)** (CSS-tricks)

### 2.2 HSL-kleuren
Lees **[Using HSL colors in CSS](https://www.smashingmagazine.com/2021/07/hsl-colors-css/)** (CSS-tricks)

#### Samenvatting
HSL staat voor Hue, Saturation en Lightness (tint, verzadiging en helderheid). Dit zijn drie kenmerken waarmee je elke kleur kunt beschrijven. Het is een hanidge manier om kleuren aan te passen in je CSS, omdat je er makkelijker dan met RGB- of HEX-codes een kleurenpalet mee kan samenstellen.
Als je bijvoorbeeld een bepaalde kleur hebt gekozen voor een button, en voor de _hover_ kleur deze iets lichter wilt, of misschien wat minder verzadigd, dan hoef je alleen maar de waarden van de helderheid en de verzadiging aan te passen naar een waarde tussen 0 en 100.

##### Hoe gebruik je het?
``` 
body {
  background-color: hsl(210, 60%, 70%);
}
```
Hue (Tint): Dit is de basis kleur. De waarde is een hoek op de kleurencirkel (denk aan een kompas), en gaat van 0 tot 360. Bijvoorbeeld, 0 of 360 is rood, 120 is groen, en 240 is blauw.

Saturation (Verzadiging): Dit zegt iets over hoe 'kleurrijk' de kleur is. 0% betekent een grijstint, terwijl 100% de volle, pure kleur geeft.

Lightness (Helderheid): Dit gaat over hoe licht of donker de kleur is. 0% is helemaal zwart, 50% is de 'normale' kleur, en 100% is wit.


##### Alternatieven voor HSL (verdieping)
[Guide to Modern CSS Colors](https://www.smashingmagazine.com/2021/11/guide-modern-css-colors/) (CSS-tricks)


### 2.3 Contrast ratio checker

[**Contrast-ratio-checker**](https://contrast-ratio.com/)

Als je jouw website niet alleen mooi maar ook meer toegankelijk wil maken, dan is het controleren van de contrastverhouding tussen de kleuren op je site een essentiële stap. 

#### Waarom is contrast belangrijk?
Contrast — het verschil in visuele eigenschappen die elementen van elkaar onderscheidbaar maakt — is cruciaal voor het creëren van een toegankelijke website. Goed contrast zorgt ervoor dat tekst en interactieve elementen duidelijk zichtbaar zijn, niet alleen voor mensen met een goed gezichtsvermogen, maar vooral ook voor slechtzienden. Ongeveer 1 op de 12 mannen en 1 op de 200 vrouwen wereldwijd hebben een vorm van kleurenblindheid, en miljoenen anderen hebben andere visuele beperkingen die het lezen van tekst met slecht contrast moeilijk of onmogelijk maken.

#### Wat doet een Contrast Ratio Checker?
Een contrast ratio checker is een tool waarmee je kunt meten hoe de kleuren van tekst en achtergrond op je website zich tot elkaar verhouden. Deze tools evalueren of je kleurcombinaties voldoen aan de toegankelijkheidsstandaarden, zoals vastgelegd in de Web Content Accessibility Guidelines (WCAG). WCAG beveelt een minimum contrast ratio aan van 4.5:1 voor normale tekst en 3:1 voor grote tekst.

#### Hoe gebruik je een Contrast Ratio Checker?
Het gebruik van een contrast ratio checker is vrij eenvoudig:
1. **Kies je kleuren:** Selecteer de voorgrond- en achtergrondkleuren die je wilt testen. Dit kunnen kleuren zijn die je al gebruikt of kleuren die je overweegt voor je design.
2. **Voer de kleuren in:** Gebruik een online contrast ratio checker en voer de Hex-codes, RGB-waarden, of HSL-waarden van je gekozen kleuren in.
3. **Analyseer het resultaat:** De tool zal je een contrast ratio getal geven. Als dit getal onder de aanbevolen waarde ligt, overweeg dan om je kleuren aan te passen om beter contrast en daarmee grotere toegankelijkheid te bieden.

Het optimaliseren van het contrast ratio in je ontwerpproces is een goede stap richting een meer inclusieve digitale wereld. Elk element op je website duidelijk en leesbaar maken is iets waar niet alleen mensen met een visuele beperking profijt van hebben. Je website wordt er voor iedereen beter van.

## 2.4 Keyframe animaties

CSS keyframe animaties bieden een manier om elementen op je webpagina tot leven te brengen en de bezoeker van feedback te voorzien wanneer er interactie plaatsvindt. 

Met deze techniek kun je gedetailleerde animaties creëren door te specificeren wat er op verschillende momenten tijdens de animatie gebeurt. Dit doe je met het `@keyframes` at-rule, waar je de stappen van de animatie definieert. Onderstaand vind je drie praktische voorbeelden om je op weg te helpen:

### 1.1 Pulse Effect
Dit is een simpele animatie waarbij een element groter en kleiner wordt, wat een kloppend effect geeft. Handig voor het benadrukken van belangrijke knoppen of iconen.

```css
@keyframes pulse {
  0%, 100% {
    transform: scale(1);
  }
  50% {
    transform: scale(1.1);
  }
}

.pulseElement {
  animation: pulse 2s infinite;
}
```

### 1.2 Fading In and Out
Fade-in en fade-out effecten zijn ideaal voor het zacht laten verschijnen en verdwijnen van elementen op de pagina, zoals alerts of banners.

```css
@keyframes fadeInOut {
  0%, 100% {
    opacity: 0;
  }
  50% {
    opacity: 1;
  }
}

.fadeElement {
  animation: fadeInOut 5s infinite;
}
```

### 1.3 Sliding In
Een schuifeffect kan erg nuttig zijn voor het tonen van menu's of panelen. Dit voorbeeld laat zien hoe je een element van links naar rechts kunt laten glijden.

```css
@keyframes slideIn {
  from {
    transform: translateX(-100%);
  }
  to {
    transform: translateX(0);
  }
}

.slideElement {
  animation: slideIn 0.5s forwards;
}
```

Met deze voorbeelden heb je een goed startpunt om te experimenteren met keyframe animaties in je eigen project. 


## 2.5 Animaties activeren
### 2.5.1 hover
De makkelijkste manier om een _keyframe_ animatie te triggeren is door de aanroep van de code in een _hover_ te laten plaatsvinden.
```
.element:hover {
  animation: slideIn 0.5s forwards;
}
```
### 2.5.2 click (of ander event)
Wil je een animatie laten starten door een klik op een element, dan kun je daarvoor _addEventListener_, de eigenschap _classlist_ en diens functies _add_, _remove_ en _toggle_ voor gebruiken. 

#### a. Animatie aan
In het geval van bovenstaand voorbeeld (1.3 Slide In) zou het klikken op een button om de animatie te starten er als volgt uit zien. 
```
document.getElementById('slideButton').addEventListener('click', function() {
  menu.classList.add('slideElement');
});

```
In het JavaScript-bestand haal je de klikbare button (slideButton) op met behulp van _getElementById_. Vervolgens koppel je een _event listener_ aan deze button die controleert of erop geklikt wordt. 

Tenslotte definieer je de _event handler_ (die in dit geval een anonieme functie is) met daarin het starten van de animatie. 


#### b. Animatie uit
Als je een menu het beeld in laat schuiven, kun je daarin een button opnemen die het menu weer doet verdwijnen, zoals je vaak ziet in de vorm van een kruisje. 
```
document.getElementById('closeButton').addEventListener('click', function() {
  menu.classList.remove('slideElement');
});
```
De animatie in de class .slideElement wordt nu ongedaan gemaakt. 

#### c. Animatie toggle
Als je dezelfde knop wil gebruiken voor het in- en uitschakelen van de animatie, dan kun je in plaats van _add_ en _remove_ ook volstaan met één _event listener_ die gebruik maakt van _classlist.toggle().

```
document.getElementById('toggleButton').addEventListener('click', function() {
  menu.classList.toggle('slideElement');
});

```
#### d. Animatie automatisch stoppen
Uitdaging: Zoek het event '_animationend_' op en probeer de getriggerde animatie automatisch te laten stoppen wanneer deze eenmaal voltooid is. Let er wel op dat dit niet werkt bij _infinite_ animaties. 




## 3. Extra oefeningen

- code: **[Animeren - Sample](https://codepen.io/shooft/pen/RwBOVjE)** (Codepen)
- uitwerking: **[Animeren - Sample](https://codepen.io/shooft/pen/NWBmjXP)** (Codepen)
- uitwerking: **[Animeren - Sample fancy](https://codepen.io/shooft/pen/yLqrbpa)** (Codepen)
- uitwerking : **[Animeren - Oefening springen maar](https://codepen.io/shooft/pen/jOpRmzq)** (Codepen)




