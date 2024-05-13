# Les 4.1 Vervolg formulieren

## 1. Vervolg formulieren (backend)
Deze les werken we verder aan de onderwerpen waar we tijdens de vorige les backend verdieping mee begonnen zijn: formulieren verwerken met Node.js, .env en de database verbinding.

Na het doorlopen van deze les, zou je hier moeten staan:
* Je hebt een eigen Node.js webserver die op enkele verschillende URL's verschillende pagina's kan serveren, doordat je enkele *routes* hebt aangemaakt.
* De pagina's worden gegenereerd door je templating engine, daarvoor heb je een paar *views* aangemaakt
* Je webserver kan *static content* zoals plaatjes en stylesheets serveren
* Je server geeft een *404 error* als een niet bestaande pagina wordt opgevraagd
* Je server is in staat informatie uit de *database* op te halen en te tonen in een view.
* Je server is in staat informatie uit een ingevuld *formulier* op te slaan in de database
* Je inloggegevens voor de database staan in een *.env* file en dat file heb je toegevoegd aan je *.gitignore*

**Theorie**

Voor je verder gaat, is het goed meer te leren over MongoDB:
* [Introduction to MongoDB](https://www.mongodb.com/docs/manual/introduction/)
* [Introduction to documents](https://www.mongodb.com/docs/manual/core/document/)
* MongoDB gebruiken vanuit Node.js met de [MongoDB module](https://www.npmjs.com/package/mongodb)

**Opdracht: Formulier opslaan in de database**

* Als het goed is, heb je inmiddels een eigen database in je Mongo account aangemaakt en de inloggegevens daarvan toegevoegd aan een .env file. Het is daarbij belangrijk dat je je .env file ook hebt toegevoegd aan je .gitignore
* Je kunt nu code toevoegen aan je node.js webserver om een verbinding met je database te openen. Gebruik hierbij het voorbeeld uit de les en uit de [boilerplate code](/verdieping-backend/server-boilerplate.js) die we hebben gedeeld.
* Maak met de hand wat testdata aan in je database. Dat kan rechtstreeks in de webinterface van MongoDB, maar het kan ook handig zijn de [MongoDB GUI compass](https://www.mongodb.com/products/tools/compass) te downloaden en gebruiken.
* Maak een nieuwe route aan in je node.js server en doe daarin een find. Vervolgens kun je de gevonden data naar de console loggen. Als je dan in de terminal een javascript object ziet wat overeenkomt met de inhoud van je database, is het mission accomplished.
* Vorige week heb je een route aangemaakt om de informatie uit het geposte formulier te ontvangen. Deze route liet de ontvangen formulier-data zien. Je kunt nu deze route verder uitbreiden en zorgen dat de ontvangen gegevens uit het formulier ook worden opgeslagen in de database.

**Opdracht: werk verder aan je component**

Je hebt nu alle informatie om je component te kunnen bouwen. Je server kan informatie sturen en ontvangen en die informatie kan permanent worden opgeslagen in een database, zodat deze ook bewaard blijft als je de server uitzet. Je kunt nu verder werken aan de volgende zaken:
1. **URL structuur**: welke URL's heeft je component voor de verschillende pagina's en hoe zijn de URL's opgebouwd? Met welke routes in Node.js komt dit overeen en zijn er ook route parameters zoals ```profiel/:gebruikersnaam```?
2. **Data modelling**: welke soorten objecten wil je opslaan in de database? Misschien zijn er meerdere soorten objecten, zoals bijvoorbeeld gebruikers, sportscholen, games, artiesten, katten, fashion-styles etc. Dit zouden verschillende collecties in je database kunnen worden. Welke informatie ga je precies opslaan voor een object? Heeft een gebruiker bijvoorbeeld een naam, of een voornaam en een achternaam? Welke datatypes ga je gebruiken? Een like kan bijvoorbeeld een boolean (true or false) zijn. Is een telefoonnummer een getal of een string?
3. Welke **CRUD operaties** van MongoDB heeft je component nodig? Bijvoorbeeld find om data uit een collectie te lezen, insert om nieuwe data toe te voegen, of update om bestaande data te wijzigen.

Tip: probeer weer zoveel mogelijke kleine stapjes te zetten. Voeg een klein stukje functionaliteit toe en check of het werkt. Zo nee, dan is het vinden van het probleem relatief overzichtelijk. Werkt het wel, dan kun je verder naar de volgende kleine stap.

