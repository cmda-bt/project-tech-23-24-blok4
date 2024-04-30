# Les 3.2 Github voor teams, Formulieren verwerken

## 1. Git(Hub) voor teams

Git en GitHub bevatten diverse features om een team te helpen samen te werken aan een project. Je wilt liever niet dat alle teamleden tegelijkertijd in dezelfde code werken, want dan zit je elkaar snel in de weg. In plaats daarvan kun je werken in een _branch_, een aparte kopie van de code, waarin je ongestoord aan je feature kunt werken. Zodra de feature gereed is, kan de branch weer worden ge*merge*d (samengevoegd) met de main branch midddels een zogenaamd _Pull Request_.

- 🎦 Bekijk een video over [de GitHub flow en branches](https://www.youtube.com/watch?v=7-q9B6HRbEQ)
- Maak de interactieve oefening over [Reviewing Pull Requests](https://github.com/skills/review-pull-requests) op GitHub Skills
- Maak de interactieve oefening over [Managing Merge Conflicts](https://github.com/skills/resolve-merge-conflicts) op GitHub Skills
- 🎦 Bekijk een video over [Branch protection](https://www.youtube.com/watch?v=rY6IxlkKF30)

Daarnaast heeft GitHub nog meer features die je team kunnen helpen het werk te organiseren:

- 🎦 Bekijk een video over [Projects en Issues](https://www.youtube.com/watch?v=L9e3_YDqNN8)
- 🎦 Bekijk een video over [Samenwerken op GitHub](https://www.youtube.com/watch?v=S4LRwbNjLWY)

Tenslotte is het een goed moment om eens stil te staan bij de vraag hoe je de code voor je hele project logisch en overzichtelijk in een folderstructuur gaat organiseren. Waar komt de front-end code en waar komt de back-end code?

- Het kan handig zijn je node.js webserver een naam te geven die duidelijk maakt dat dit de backend-server is. Iets als server.js kan een goede keuze zijn, app.js zie je ook wel eens. Noem je je server index.js, dan is het makkelijk te verwarren met front-end code die in de browser zou moeten draaien.
- Plaatjes, stylesheets maar ook front-end JavaScript die in de browser moet draaien, kan een plek vinden in je folder met static content
- Statische HTML pagina's die door de front-enders worden gemaakt, kunnen ook worden neergezet in de folder met static content. Maar nog mooier is het de statische pagina's dynamisch te maken door de aangeleverde HTML om te bouwen naar een EJS view in deze dan als een .ejs bestand in de folder met je views te plaatsen.


## 2. Formulieren verwerken met NodeJS en MongoDB

### Boilerplate
Verspreid over de lessen en opdrachten kom je verschillende stukken code tegen die je nodig hebt om je webserver aan de praat te krijgen. Deze zijn verzameld in een [boilerplate voor je Node.js webserver](/verdieping-backend/server-boilerplate.js), zodat je niet de sheets hoeft over te typen ;)

### Formulieren verwerken
Tot nu toe hebben we met onze server alleen informatie (HTTP responses) naar de client gestuurd. Een eenzijdige conversatie. We gaan nu ook gegevens ontvangen van onze gebruikers, bijvoorbeeld uit formulieren die ze invullen. Denk aan een fornulier om een nieuw account aan te maken, in te loggen, je profiel bij te werken, etc.

Er zijn twee manieren om in een HTTP request van de client naar de server data mee te sturen:
1. In de querystring als onderdeel van de URL. Bijvoorbeeld:
```productoverzicht.html?producttype=laptops&pagina=5```
De variabelen zijn nu zichtbaar in de URL, zowel voor gebruikers als zoekmachines. Soms is dit handig, zoals in het voorbeeld hierboven, maar vaak ook niet. Bovendien beperkt zich dit tot een kleine hoeveelheid korte informatie. Een profielfoto of lange beschrijving kun je hier niet in kwijt.
2. In de body van de HTTP request. De informatie wordt nu 'onder water' mee gestuurd in de HTTP request. Dit is bijvoorbeeld wat er gebeurt als we een formulier posten. Dit heb je trouwens ook gedaan toen je eerder met Postman requests stuurde naar onze Data API en daarbij JSON meegaf. Met deze methode is er ruimte voor meer uitgebreide informatie.

We gaan vandaag verder aan de slag met optie 2. Hierbij vult de gebruiker een formulier in en drukt op de submit knop. Op dat moment stuurt de browser een HTTP request naar de server, naar de URL die als *action* in het formulier is opgegeven. De te gebruiken HTTP request *method* wordt ook in het formulier aangegeven. Normaal gesproken is dit **POST**.

**Opdracht: Formulier posten**

Breid je node.js server uit met code om een gepost formulier te verwerken. Je kunt hiervoor het inlogformulier uit de vorige les gebruiken, als je daaruit eerst de (front-end) JavaScript weghaalt. We gaan deze functionaliteit nu immers in de back-end bouwen. 
1. Maak in je node.js server een route en een view om je formulier te tonen
2. Geef het formulier een action en de method POST
3. Maak een route om de POST request af te handelen als het formulier wordt verstuurd
4. Maak een view om een HTTP response op de POST request te sturen. Laat in deze view de ontvangen formulier data zien. De ingevulde formulier velden zijn beschikbaar als eigenschappen van **req.body** als je in Express de juiste middleware hebt aangezet met ```app.use(express.urlencoded({extended: true}))```

Als dit gelukt is, kun je zien dat de verstuurde formulier data op de server is aangekomen. Op dit moment wordt deze daar nog niet bewaard. Daarvoor hebben we de volgende stap nodig: het maken van een verbinding met een database. Daar werken we volgende week verder aan.

Tips:
* Begin klein. Kijk eens of je een formulier met 1 input veld aan de praat kunt krijgen. Daarna kun je het altijd nog uitbreiden met meer. Bouw je werk stap voor stap op.
* Commit regelmatig en push je werk naar GitHub. De eerste versies hoeven niet perfect te zijn, probeer zo ver te komen als je kunt
* Bekijk voorbeelden in onze slides, op Internet en kijk vooral ook hoe je mede-studenten het aanpakken.

### Database
In dit project gebruiken we MongoDB als database. De eerste stap is het aanmaken van een MongoDB Atlas account met daarin een eigen database.

[MongoDB Atlas](https://www.mongodb.com/atlas/database) is een DBaaS, oftewel database as a service. Dit is een dienst die via de cloud wordt aangeboden, zodat we niet zelf een database hoeven te installeren op onze laptop. Voor dit project kunnen we gebruik maken van een gratis account. Voor grotere projecten in een productieomgeving zou je waarschijnlijk wel een betaald abonnement willen afsluiten. 

Het aanmaken van je database is niet moeilijk, maar er is wel een flink aantal stapjes voor nodig. Volg de instructies daarom zorgvuldig, want als je een stap overslaat, gaat de rest ook niet werken. En stel vooral je vragen op Teams in het #back-enders kanaal als je vastloopt.

**Opdracht: aanmaken van je database**

Volg de instructies in de officiele [MongoDB start with guide](https://www.mongodb.com/docs/guides/atlas/account/). Hierin staan de volgende stappen:
1. Create MongoDB account
2. Create a cluster
3. Add a database user
4. Configure a network connection
5. Load sample data (optioneel, misschien vind je het fijner zelf testdata aan te maken die past bij je eigen project)
6. Get connection string

Bij stap 4 geef je aan vanaf welke IP adressen je node.js server straks verbinding mag maken met de database. Je kunt hier je huidige IP-adres toevoegen, maar als je op verschillende plekken werkt met een laptop, zal je IP-adres ook steeds veranderen. Op de HvA krijg je bijvoorbeeld elke keer een ander IP-adres toegewezen als je inlogt op Eduroam. Je kunt alle HvA adressen toevoegen met een [*subnetmask*](https://www.youtube.com/watch?v=yK__SdS2meo) door als IP-adres ```145.0.0.0/8``` toe te voegen. Voeg daarnaast ook je IP-adres thuis toe en eventueel andere adressen die je wilt gebruiken. Als je node.js server geen verbinding wil maken met de database, is het altijd goed om even te checken wat je [huidige IP-adres](https://showip.net/) is en dit toe te voegen aan de whitelist.

🚨 Zet nooit je gebruikersnaam, wachtwoord en URL van de database in je code. Als dit eenmaal op GitHub staat (al is het in een oudere commit) is het een kwestie van tijd voordat hackers je database over zullen nemen. Zet daarom dit soort info in een los ```.env``` file en voeg dit toe aan je ```.gitignore```.

🎦 [Bekijk een video over .env](https://www.youtube.com/watch?v=17UVejOw3zA)


### OPDRACHT
Nu kun je je formulier om nieuwe accounts te registeren werkend krijgen, door de onderstaande stappen te volgen. Dit is een uitgebreider stappenplan dan voor de front-enders, omdat we eerst het inlogformulier uit de vorige les gaan overzetten naar onze backend server.

Het onderstaande is best een uitgebreide opdracht. Neem er rustig de tijd voor, het hoeft niet in één keer af. Onthoud ook dat deze oefening bedoeld is om de techniek in de vingers te krijgen. De formulieren en bevestgingspagina's mogen er voor nu best simpel uitzien. En als je een gebruiker met twee eigenschappen in de database weet op te slaan, kun je het in principe ook met 10 eigenschappen. Dus begin klein.

1. Verwijder de (front-end) JavaScript uit het inlogformulier, want deze functionaliteit gaan wij nu in de backend realiseren.
2. Maak in je node.js webserver een nieuwe route en een view om het inlogformulier te tonen
3. Geef in het inlogformulier de ```<form>``` een geschikte action (door jou te kiezen URL) en method (POST) als attributen.
4. Maak in je webserver een nieuwe route aan om de POST request op deze URL te kunnen afhandelen
5. Laat deze route in eerste instantie een bevestigingspagina tonen met daarin de informatie die is ontvangen uit het inlogformulier
6. Breid de code in je route voor de bevestigingspagina uit met een stuk logica. Kies voor nu één vaste gebruikersnaam met een wachtwoord. Als de in het inlogformulier ingevulde gegevens daarmee overeenkomen, toon dan een welkomstpagina. Had de gebruiker iets anders ingevuld, toon dan een foutmelding.
7. Zodra je je database werkend hebt, kun je daarin met de hand een aantal testgebruikers aanmaken.
8. Je kunt nu in de code voor je route actuele informatie over je gebruikers uit de database halen. In plaats van de inloggegevens te vergelijken met één vaste waarde, kun je nu kijken of de gebruiker voorkomt in de database en zo ja, of het wachtwoord overeenkomt.
9. Maak vervolgens in je node.js webserver nog een nieuwe route en view om je formulier voor het aanmaken van een nieuw account te tonen
10. Geef ook dit formulier een geschikte action (door jou te kiezen URL) en method (POST).
11. Maak in je webserver een nieuwe route aan om de POST request op deze URL te kunnen afhandelen
12. Voeg code toe aan deze route om de ontvangen gebruikersgegevens op te slaan in de database en een bevestigingspagina te tonen
13. Kijk op dit moment eens zelf in database door in te loggen op MongoDB of via hun GUI. Staat de nieuwe gebruiker er tussen en kloppen alle gegevens?
14. Kijk tenslotte of je nu het inlogformulier kunt gebruiken om in te loggen als je nieuwe gebruiker


