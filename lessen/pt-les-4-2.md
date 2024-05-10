# Les 4.2 Frontend optimalisatie

## Responsive design

### Relative units

- [Relatieve eenheden in CSS](https://bnieskens.notion.site/Eenheden-CSS-60c85e9c54b940299a7ef6d446e643cd?pvs=4)

### Media Queries

- [MDN media queries](https://developer.mozilla.org/en-US/docs/Web/CSS/@media)
- [MDN using media queries](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_media_queries/Using_media_queries)

### Flexbox

- [A complete guide to CSS Flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
- [CSS Flexbox tutorial](https://www.youtube.com/playlist?list=PLqYFXd9GTRVXlSvi1DeY34BAq5ATZCqY2)

### CSS Grid

- [A complete guide to CSS Grid](https://css-tricks.com/snippets/css/complete-guide-grid/)
- [Beginner tutorial](https://www.youtube.com/watch?v=br-0i3U1VCA)

## Progressive enhancement / graceful degradation

- [Progressive Enhancement (Video2Brain)](https://www.youtube.com/watch?v=U38dyJhpUnA)

### Voorbeeld PE (Sparkbox)

- [Progressive Enhancement HTML (Sparkbox)](https://www.youtube.com/watch?v=INZto6rlSeM)
- [Progressive Enhancement CSS (Sparkbox)](https://www.youtube.com/watch?v=INZto6rlSeM)

## Coding standards

- [Clean Code (Ryan McDermott)](https://github.com/ryanmcdermott/clean-code-javascript)
- [DTT style guide](./bronnen/DTT_style_guide.docx)
- [Google JavaScript style guide](https://google.github.io/styleguide/jsguide.html)

### ES6

- [ES6 JavaScript Tutorial](https://www.javascripttutorial.net/es6/)

### Linters

Er bestaan allerlei tools die je kunnen helpen 'nette' code te schrijven. Je hebt misschien al gewerkt met een _formatter_ als Prettier, die helpt code netjes te formatteren. Met een _linter_ kun je nog een stap verder gaan, deze controleert je code ook op inhoudelijke fouten. Er bestaan verschillende Linters. Tijdens dit project gaan we oefenen met **ESLint**.

**Opdracht: ESLint**

1. Denk eerst na over de coding standards die je wilt gebruiken. Tijdens het installeren moet je hierover namelijk een aantal vragen beantwoorden. Het is later altijd nog mogelijk je keuzes te wijzigen.
2. Installeer ESLint in de folder van je project volgens de instructies op [Getting Started with ESLint](https://eslint.org/docs/latest/use/getting-started) en beantwoord zorgvuldig de vragen over je gewenste configuratie.
3. Als alles goed is gegaan, heeft ESLint in de folder van je project een configuratiefile gemaakt met de naam `.eslintrc.*` Afhankelijk van je keuze is dit een JavaScript, JSON, of YAML bestand. Als je later je keuzes nog wilt aanpassen, kun je wijzigingen aanbrengen in dit bestand of nog een keer opnieuw de configuratie doorlopen
4. Je kunt ervoor kiezen om je `.eslintrc.*` configuratiefile toe te voegen aan je `.gitignore`, want feitelijk is dit geen onderdeel van de code van je project. Maar als je als team samenwerkt, kun je er ook voor kiezen de configuratie juist wel aan je repository toe te voegen, want dan werken jullie allemaal volgens dezelfde standaard
5. Als je configuratie voltooid is, gebruik dan ESLint om je eigen JavaScript code te _linten_. Volg ook hiervoor de instructies op Getting Started with ESLint.
6. Je kunt ESLint ook als extensie toevoegen in VSCode. Je ziet dan direct alle problemen in je editor en hoeft niet apart ESLint te gebruiken vanuit je Terminal. Let er op dat deze extensie alleen werkt voor je project, als je eerst binnen dat project ESLint hebt geinstalleerd en geconfigureerd volgens bovenstaande stappen.

Pro-tip: je hebt gemerkt dat je tijdens de configuratie van ESLint hebt moeten aangeven of je code draait op Node.js (en dan waarschijnlijk `require` gebruikt om modules in te laden) of in de browser (met `import` statements). Je kunt in aparte mappen van je project ook verschillende `.eslintrc.*` configuratiebestanden maken. In het ene mapje maak je dan regels om je frontend code te checken, en in een ander mapje kun je regels plaatsen voor je back-end code.


