# Les 1.4 Theorie API en "Data API"

## 1. Installeren en uitproberen "Data API"
Voor dit project stellen wij een API beschikbaar. Met deze API kun je data lezen uit een database of opslaan in die database, zonder je zorgen te hoeven maken over de achterliggende techniek. 
* Als je kiest voor de front-end specialisatie, kun je deze API vanuit je code in de browser aanroepen om dynamisch data op te halen of op te slaan.
* Als je kiest voor de back-end specialisatie, vervang je uiteindelijk deze API door een zelfgeschreven backend.

In beide gevallen is het aan de praat krijgen van de API een mooie oefening om de basis van Node.js en NPM onder de knie te krijgen. 

Je kunt onze [API vinden op GitHub](https://github.com/ivo-online/database_api). Volg daar de instructies in de README.md om een kopie te maken van deze API op je eigen computer. Je moet hierbij een aantal persoonlijke toegangsgegevens invullen in een eigen .env file. De benodigde waardes krijg je van je docenten. 

Tip voor de Mac gebruikers: bestanden zoals .env waarvan de naam begint met een . (punt), de zogenaamde dotfiles, worden standaard verborgen. In de terminal kun je ze zien met het commando `ls -a` en in de Finder door de toetsen command-shift-. in te drukken. 

🎦 Bekijk de video over het [ installeren en uitproberen van de API](https://youtu.be/MpDuQBQfJZM).

Zodra je de API succesvol hebt draaien in je terminal, kun je proberen een aantal HTTP requests naar de API te sturen om te kijken wat er gebeurd. De mogelijke requests zijn gedocumenteerd in de [README.md](https://github.com/ivo-online/database_api/blob/main/README.md) van de API. 

Vanuit frontend JavaScript code, die draait in de browser, kun je straks gebruik maken van [fetch](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch) om requests naar de API te sturen. Om, zonder te coderen, al vast een beetje gevoel te krijgen hoe de API werkt, kun je ook handmatig HTTP requests sturen naar de API en de responses zien met een geschikte browser plugin zoals [Tabbed PostMan](https://chromewebstore.google.com/detail/tabbed-postman-rest-clien/coohjcphdfgbiolnekdpbcijmhambjff) voor Chrome.

Voor nu gaan we werken in een gezamenlijke database waarin al wat testdata aanwezig is. Omdat we hier met z'n allen in werken, kan het zijn dat je soms data ziet veranderen of verdwijnen, omdat een andere student iets gewijzigd heeft. Later in het project krijgt elk team toegang tot een eigen database om in te werken.

Oefening: stuur HTTP requests naar de API om het volgende te doen:
* Vraag een overzicht op van alle testdata die in de database aanwezig is.
* Vraag 1 specifiek object op uit de aangemaakte testdata, bijvoorbeeld iemand met een bepaald beroep.
* Update een object uit de testdata, bijvoorbeeld door een beroep te veranderen in een ander beroep.
* Voeg zelf een nieuw object toe aan de database. Dit hoeft geen test-object te zijn. Maak bijvoorbeeld een huis, of een maaltijd, of een student, of een ....
* Probeer de gegevens van je zojuist gemaakte object op te halen uit de database. Was je data goed opgeslagen?
