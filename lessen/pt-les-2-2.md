# Les 2.2 Frontend API basics


## Soorten API
- OS API (MacOS, Windows, etc)
- Browser API
    -- Web Storage (localStorage en sessionStorage)
    -- Geolocation API
    -- ...
- Online Web API

Deze les focussen we op online Web API. 

## Introductie
### API
Een API is een interface waarmee programma's kunnen communiceren met servers via het web. Zo'n server kan de data in verschillende formaten terugsturen. Meestal is dit CSV of JavaScript Object Notation (JSON). Als je zo'n bestand in een text editor of [browser opent](https://www.amiiboapi.com/api/amiibo/?gameseries=Super%20Mario), zie je dat het dezelfde indeling heeft als een JavaScript Object.  

### Fetch
Met behulp van de functie 'fetch' kun je in JavaScript data in JSON-format opvragen van zo'n API. De bron van de data die je wil ophalen (de URL), geef je als argument door aan de functie. Vervolgens handel je het antwoord dat je van de server terugkrijgt (*response*) af met behulp van de functie '.then()'.

```
fetch(url)
  .then(response => response.json()) // zet de response om in JSON
  .then(data => console.log(data)) // doet iets met de data
  .catch(error => console.error('Fout bij het ophalen van de data:', error));
  ```

De *response* die je van de server krijgt, is een Promise object. Om van deze tekstindeling (.json-bestand) een JavaScript Object te maken waar je in vervolgens bewerkingen mee kan doen, is het nodig om dit *response* met behulp van de functie *json()* om te zetten. Dat gebeurt in de tweede regel van bovenstaande code. Let op de puntnotatie waarmee je de functie *then()* koppelt aan *fetch()*. 

Als tweede vervolgstap in het afhandelen van de *response* kun je met een volgende *then()* de data verder verwerken. Hier wordt die gelogd in de console. Maar je wil die natuurlijk tonen in de HTML. Voor dat we die stap gaan maken, is het goed om kennis te maken met een iets eenvoudigere manier van het afhandelen van een API response. 

### Async functie / Await
Met behulp van een asynchrone functie kun je data binnenhalen van een API en afdwingen dat de volgende regels in de functie pas uitgevoerd worden wanneer die data daadwerkelijk binnen is. Daarvoor gebruik je het sleutelwoord *await*. 

```
async function fetchData(url) {
    const response = await fetch(url);
    const data = await response.json();
    console.log(data)
}

fetchData('https://api.example.com/data');
```
In bovenstaand voorbeeld wordt afgedwongen dat 
- eerst de data van de API wordt binnengehaald (daar wordt op gewacht)
- dan de data wordt omgezet naar een JSON-object (daar wordt op gewacht)
- dan pas de data wordt getoond in de console

Als je een synchrone functie zou gebruiken, en zonder *await*, worden de regels in de body van de functie sneller uitgevoerd dan het binnenhalen en omzetten van de data. In de praktijk probeert de functie dan de constante *response* om te zetten in een object, nog voordat die terug is gekomen van de server. Dat duurt namelijk langer dan het uitvoeren van de regel code. 

### Extra bronnen 
Onderstaand vind je nog twee instructievideo's met theorie omtrent fetch en JSON.
- bron: **[Fetch API data voorbeeld](https://www.youtube.com/watch?v=7f2HNadULOs)** (YouTube, 9min)
- bron: **[Learn JSON in 10 minutes](https://www.youtube.com/watch?v=iiADhChRriM)** (YouTube, 12min)

    
## Oefening 1: API data verwerken (met amiibo API)

- Zoek een web API die data in JSON-formaat aanlevert. Bekijk de [Lijst met openbare API's](https://github.com/marcelscruz/public-apis)** - nb. linkjes in README.md (www)
- Kun je geen geschikte vinden, gebruik dan [deze API met Super Mario data](https://www.amiiboapi.com/api/amiibo/?gameseries=Super%20Mario) in JSON-format. Documentatie over deze API vind je hier: [AmiiboAPI documentation](https://www.amiiboapi.com/)
- Schrijf een asynchrone functie die met behulp van het sleutelwoord *await* data uit de API opvraagt en omzet naar een JavaScript object.


### HTML
Wanneer je data van de API hebt binnengehaald, wil je deze natuurlijk weergeven in je HTML. Maak een HTML-pagina met daarin een *ul*. Geef deze als ID bijvoorbeeld 'amiiboList'. 

### JavaScript
Bestudeer het object dat je na het omzetten met .json() hebt opgeslagen in de constante *data*. Je ziet dat dit object slechts 1 waarde bevat, namelijk *amiibo* en dat dit een array is waar alle karakters in zijn opgeslagen als een object. Je verwijst naar die array met *data.amiibo*.

Met behulp van de array-method *forEach* kun je door de *amiibo* array lopen en met elk object in die array iets doen. In dit geval wil je de waarde van *amiibo.character* in een nieuwe *li* toevoegen aan de *ul*

```
const list = document.getElementById('amiiboList');
amiibos.forEach(amiibo => {
        const listItem = document.createElement('li');
        listItem.textContent = `${amiibo.character} - ${amiibo.name}`;
        list.appendChild(listItem);
    });
```
In bovenstaande code wordt voor elk object in de array een nieuw li-item aangemaakt. De *textContent* van die li wordt voorzien van het karakter en meer specifiek wat voor soort amiibo het is. Tenslotte wordt elk li toegevoegd aan de ul die je in de vorige stap aan de HTML-code hebt toegevoegd. 

Ook worden *back ticks* gebruikt om het begin en einde van een *string* aan te geven. Het voordeel daarvan is dat je namen van variabelen makkelijker kan opnemen in zo'n tekenreeks. Dat doe je met behulp van `${variabele}`. Je noemt dit soort tekenreeksen *template strings* of *template literals*.

## Oefening 2: Loading state
Het ophalen van data van een externe server kan vaak wat tijd kosten. Als je dit wat betreft UI/UX gebruiksvriendelijk wil maken, zorg je voor een animatie die de bezoeker duidelijk maakt dat er in de achtergrond een proces is opgestart waarop wordt gewacht. Je ziet dit soort animaties vast wel eens gezien bij het bezoeken van een website die data ophaalt. 

### Loader
Het toevoegen van een zogenaamde *loading state* zit voornamelijk in de CSS-code. 

Maak eerst een *div* aan in het HTML-bestand die wordt gebruikt om de animatie te tonen tijdens het ophalen van de API data. Geef deze een logische *id*, bijv. *loaderDiv*. 

### Opmaak en animatie loader
Geef in CSS deze *div* de vereiste opmaak en inhoud, en liefst ook een (keyframe) animatie die wordt herhaald. 

```
#loaderDiv {
    background-image: url("loading-image.png");
    background-position: center;
    background-repeat: no-repeat;
    background-size: cover;

    /* maak er een ronde afbeelding van */
    border-radius: 50%;

    /* beperk interactie door bezoeker */
    pointer-events:none;
	user-select:none;

    /* verberg de loader, zichtbaar maken gebeurt met eenvoudige transitie  */
    opacity:0;
	transition:.15s;

    /* animatie tijdens tonen */
    animation: rotate 2s linear infinite;
}

@keyframes rotate {
    0% {
        transform: rotate(0deg);
    }
    100% {
        transform: rotate(360deg);
    }
    
}

```

Je zal zelf moeten nadenken over de breedte en hoogte van deze div. Ook over de positie op de pagina. Als je de loader op een bepaalde plek wil plaatsen ten opzichte van waar de data wordt getoond, is het handig om deze `position: absolute` te geven. De parent van *loaderDiv* (waar ook de data in wordt getoond) krijgt dan `position: relative`.

### Loader zichtbaar maken
Het tweede deel van de CSS-code van de loader is het zichtbaar kunnen maken van de div. In bovenstaande code zie je dat `opacity: 0` ervoor zorgt dat deze niet zichtbaar is. 
Voeg daarom aan *#loaderDiv* een class toe met `opacity: 1` die je straks in JavaScript aan de loaderDiv kan toevoegen en weer weghalen wanneer dat nodig is. 


```
#loaderDiv.loading {
    /* wordt toegevoegd aan loaderDiv met classlist.add */
    opacity:1;
    
}
```

### Loader activeren
Het activeren van de loader gebeurt uiteraard in JavaScript. Net voordat je de data uit de API gaat ophalen, activeer je de *loader*. Wanneer het ophalen en het omzetten naar een JavaScript Object is afgehandeld, laat je de *loade* weer verdwijnen. Dit gebeurt met behulp van de functies *add* en *remove* van de *classlist* eigenschap van de *loaderDiv*.

``` 
async function fetchData(url) {
    loaderDiv.classList.add("loading")
    const response = await fetch(...)
    const data = await response.json()
    loaderDiv.classList.remove("loading")
}
```
Bovenstaande code zorgt ervoor dat in de asynchrone functie die de API data binnenhaalt en verwerkt, de loader vooraf wordt getoond en na afloop weer wordt verborgen. 




## Uitgebreide oefening
Onderstaand vind je een uitgebreidere versie van bovenstaande oefeningen en de uitwerkingen daarvan. 

- code: [**Oefeningen - API basics**](https://codepen.io/shooft/pen/vYzROqZ) (Codepen)
- code: [**Oefeningen - API empty & loading state**](https://codepen.io/shooft/pen/mdGxJZB) (Codepen)


### Uitwerkingen

- uitwerking: **[Oefeningen - API basics](https://codepen.io/shooft/pen/OJovVev)** (Codepen)
- uitwerking: [**Oefeningen - API empty & loading state**](https://codepen.io/shooft/pen/BaOrNgx) (Codepen)

