# Les 5.1 Feedbacksessie, Drag n' Drop

## 1. Drag 'n drop met vanilla JS

### 1.1 Inleiding

Drag-and-drop is een functionaliteit die je in staat stelt om elementen binnen een webpagina te verplaatsen door ze te slepen en te laten vallen. Dit kan zeer nuttig zijn voor het implementeren van interactieve en gebruiksvriendelijke interfaces. In deze uitleg gaan we door een voorbeeld waarin je een citaat kunt slepen en neerzetten in een favorieten-sectie. We gaan de belangrijkste onderdelen van de code bespreken die de drag-and-drop-functionaliteit mogelijk maken.

### 1.2 Uitleg van de Code

Hieronder vind je de uitleg van de specifieke JavaScript-code die nodig is voor het slepen en neerzetten van een citaat naar een favorieten-sectie.

#### 1.2.1 Dragstart Evenement

```javascript
quoteElement.addEventListener("dragstart", (event) => {
  event.dataTransfer.setData("text/plain", event.target.textContent);
});
```

**Beschrijving**: Dit evenement wordt geactiveerd wanneer je begint met het slepen van het citaat. In deze functie:
- `event.dataTransfer.setData("text/plain", event.target.textContent)` stelt de data in die overgedragen moet worden tijdens het slepen. Hier stellen we de tekstinhoud van het citaat in als de data die wordt overgedragen.

#### 1.2.2 Dragover Evenement

```javascript
favorites.addEventListener("dragover", (event) => {
  event.preventDefault();
  favorites.classList.add("dragover");
});
```

**Beschrijving**: Dit evenement wordt voortdurend geactiveerd wanneer een gesleept element over het `favorites`-gebied beweegt. In deze functie:
- `event.preventDefault()` is noodzakelijk om te voorkomen dat het standaard gedrag plaatsvindt, wat ervoor zorgt dat de drop-actie wordt toegestaan.
- `favorites.classList.add("dragover")` voegt een CSS-klasse toe om visuele feedback te geven dat het element een geldig drop-gebied is.

#### 1.2.3 Dragleave Evenement

```javascript
favorites.addEventListener("dragleave", () => {
  favorites.classList.remove("dragover");
});
```

**Beschrijving**: Dit evenement wordt geactiveerd wanneer een gesleept element het `favorites`-gebied verlaat. In deze functie:
- `favorites.classList.remove("dragover")` verwijdert de visuele feedback wanneer het element niet langer boven het drop-gebied zweeft.

#### 1.2.4 Drop Evenement

```javascript
favorites.addEventListener("drop", (event) => {
  event.preventDefault();
  const quote = event.dataTransfer.getData("text/plain");
  const quoteElement = document.createElement("p");
  quoteElement.textContent = quote;
  quoteElement.classList.add("quote");
  favorites.appendChild(quoteElement);
  favorites.classList.remove("dragover");
});
```

**Beschrijving**: Dit evenement wordt geactiveerd wanneer het gesleepte element wordt losgelaten in het `favorites`-gebied. In deze functie:
- `event.preventDefault()` is opnieuw noodzakelijk om het standaard gedrag te voorkomen en de drop-actie toe te staan.
- `const quote = event.dataTransfer.getData("text/plain")` haalt de overgedragen data (het citaat) op.
- `const quoteElement = document.createElement("p")` creëert een nieuw `p`-element om het citaat weer te geven.
- `quoteElement.textContent = quote` stelt de tekstinhoud van het nieuwe `p`-element in op het citaat.
- `quoteElement.classList.add("quote")` voegt een CSS-klasse toe aan het nieuwe `p`-element voor styling.
- `favorites.appendChild(quoteElement)` voegt het nieuwe `p`-element toe aan het `favorites`-gebied.
- `favorites.classList.remove("dragover")` verwijdert de visuele feedback na het loslaten.

### 1.2.5 Conclusie

Met deze code kun je elementen binnen een webpagina slepen en neerzetten, wat bijdraagt aan een meer interactieve en dynamische gebruikerservaring. Probeer dit voorbeeld zelf uit en experimenteer met verschillende stijlen en functionaliteiten om vertrouwd te raken met de kracht van drag-and-drop in webontwikkeling.






## 2. Drag and drop met Sortable

### Bronnen en tools
- library: **[SortableJS - voor drag en drop](http://sortablejs.github.io/Sortable/)** (www)

### Oefeningen
- code: **[Oefening lijstjes en libs - drag-n-drop](https://codepen.io/shooft/pen/ZEMXKxp)** (Codepen)
- code: **[Oefeningen - API drag-and-drop](https://codepen.io/shooft/pen/gOdepNo)** (Codepen)

### Uitwerkingen
- uitwerking: **[Oefening lijstjes en libs - drag-n-drop](https://codepen.io/shooft/pen/eYLGWMB)** (Codepen)
- uitwerking: **[Oefeningen - API drag-and-drop](https://codepen.io/shooft/pen/NWLYqZL)** (Codepen)


## 3. Carousels en swipen

### Bronnen en tools
- library: **[Swiper - voor carousels](https://swiperjs.com/demos)** (www)
- library: **[Hammer.js - swipen en andere touch events](https://hammerjs.github.io/)** (www)

### Oefeningen
- code: **[Oefening lijstjes en libs - carousel](https://codepen.io/shooft/pen/RwYLgrm)** (Codepen)

### Uitwerkingen
- uitwerking: **[Oefening lijstjes en libs - carousel](https://codepen.io/shooft/pen/GRXMEoV)** (Codepen)

 
 
