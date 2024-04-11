# Les 1.2 Backend basis
In deze les leren we meer over de techniek die komt kijken bij het opzetten van een dynamisch web-project: hoe werkt precies HTTP, hoe kun je de command line gebruiken voor geavanceerde instructies en wat is het verschil tussen een site met functionaliteit in de frontend en één met functionaliteit in de backend? Ook leren we meer over Node.js en NPM.

Na al deze theorie is het ook tijd een begin te maken met het eindproduct. Je brainstormt over het concept voor de matching-app die je wilt bouwen en documenteert dit in je wiki.

## 1. HTTP request en response
🎦 Bekijk de [video over HTTP](https://www.youtube.com/watch?v=IS3HRyUXJX0) requests en responses.

## 2. Command line
Gedurende dit blok zullen we regelmatig gebruik maken van de Terminal. Neem een moment om deze op je computer gereed te maken en de basis te leren.

*Windows:*  
Nieuwe versies van Windows gebruiken PowerShell als command line interface. Type 'PowerShell' in de zoekbalk van je start-menu of taakbalk. Je start PowerShell standaard als gewone gebruiker, maar je kunt er ook voor kiezen het te starten als administrator. Normaal gesproken is het verstandig PowerShell uit te voeren als gewone gebruiker. Je hebt dan iets minder rechten, maar ook minder kans per ongeluk dingen kaport te maken.

Standaard heeft PowerShell een aantal beveiligingsinstellingen, waarbij het bijvoorbeeld niet mogelijk is scripts te runnen zonder permissie. Dit kan later in dit blok een probleem worden, als je bijvoorbeeld nodemon wilt starten en het werkt niet. Je kunt je huidige instellingen controleren in PowerShell met het commando: 
```sh
Get-ExecutionPolicy -List
```
en deze eventueel iets versoepelen met het commando:
```sh
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

*MacOS:*  
Apple heeft ook een ingebouwde command line interface. Zoek naar `terminal` met **spotlight** of kijk in je applications folder. Ook op Mac voer je in de Terminals standaard commando's uit met de rechten van een gewone gebruiker. De meeste dingen kun je hiermee doen, met minder risico belangrijke zaken kapot te maken. Voor sommige instellingen of het installeren van software heb je soms administrator rechten nodig. Je kunt dan `sudo` voor een commando zetten. Stel dat je geen toegang hebt tot een bepaalde directory, en `ls` geeft daarom een foutmelding, dan zou `sudo ls` wel kunnen werken.

> 💡 Op Macs met MacOS Catalina (of nieuwer) is de standaard shell `zsh`, daarvoor was het `bash`. Als je `bash` hebt als standaard instelling, raden we aan dat aan te passen volgens de instructie in dit [Apple support article](https://support.apple.com/en-us/HT208050).

Veel mensen vinden het ook fijn de [Integrated Terminal](https://code.visualstudio.com/docs/editor/integrated-terminal) direct vanuit VSCode te gebruiken.

**Theorie Command Line**

Gebruik onderstaande resources om meer te leren over de commando's die je kunt gebruiken in de terminal:
* Voor Windows gebruikers: Lees [Working with files and folders](https://learn.microsoft.com/en-us/powershell/scripting/samples/working-with-files-and-folders?view=powershell-7.3) en kijk de video: [Powershell for Beginners](https://www.youtube.com/watch?v=Jfvg3CS1X3A)
* Voor Mac gebruikers: volg [A Designer’s Guide to the Terminal](https://react.design/terminal) en kijk de video: [Command Line Basics video](https://www.youtube.com/watch?v=DP218aBHm1Q) van CLI cursus door Wes Bos

**Opdracht - Oefenen met de Command Line** 

Maak de volgende opdrachten om de basis van de command line onder de knie te krijgen
* Zoek de folder met je documenten voor Project Tech in je verkenner of finder. Open nu een terminal venster en zoek daar dezelfde folder op. Tip: gebruik `cd` en `pwd`
* Vraag een lijst op van de bestanden in deze folder. Tip: gebruik `ls`
* Maak een kopie van een van deze bestanden.
* Maak in de folder een nieuwe lege directory aan
* Verplaats de kopie die je net gemaakt had, naar de nieuwe directory
* Verwijder de nieuwe directory inclusief het gekopieerde bestand
* Kijk of je in de folder van je project zogenaamde `dotfiles` kunt vinden. Dit zijn bestanden of folders waarvan de filenaam begint met een . (punt), zoals bijvoorbeeld `.gitignore`, `.DS_Store`, `.git` of `.env`. Dit zijn bestanden met systeeminstellingen, die standaard verborgen zijn (niet getoond worden). Op de Mac kun je ze laten zien met het commando `ls -a` en op Windows met `ls -hidden`. Op Windows is het ook handig in de verkenner onder het menu Weergeven de verborgen items aan te vinken.

## 3. Node.js en NPM
Bekijk onderstaande video's:
* [De browser versus Node.js](https://www.youtube.com/watch?v=ZpiHUOM_Y-0)
* [NPM](https://www.youtube.com/watch?v=X8D5Ijpp824)
* [Live demo NPM en packages](https://www.youtube.com/watch?v=shSB9BbK1gU).

Installeer nu op je eigen computer Node (inclusief NPM)

### Node - installeren op Mac

Open je **terminal**, en installeer [nvm](https://github.com/creationix/nvm) als volgt:

```sh
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.3/install.sh | bash
```

Controleer of `nvm` goed is geinstalleerd:
```sh
nvm --version # Should print a version number
```

> Zie je de foutmelding `nvm command not found`? Dan is NVM niet goed geïnstalleerd. Lees  [troubleshouting section on nvm](https://github.com/nvm-sh/nvm#troubleshooting-on-macos) zorgvuldig om dit op te lossen. 

**Sluit je terminal af en start deze opnieuw**. Type vervolgens:

```sh
nvm install stable
```

Node en NPM zijn nu geïnstalleerd. Check dit met:

```sh
node -v # Should print v18.12.1 (or a higher version)
npm -v # Something like 9.2.0 (or a higher version)
```

[🎦 Video over het intalleren van Node op MacOS](https://www.youtube.com/watch?v=EQWyWQhphGw)

> Als je in plaats van bovenstaande instructies gebruik maakt van de Node [installer](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm), kun je geconfronteerd worden met een [`eaccess`](https://docs.npmjs.com/resolving-eacces-permissions-errors-when-installing-packages-globally) probleem. Om die reden raden wij bovenstaande werkwijze met nvm aan. De node installer installeert npm in een directory met local permissions, wat problemen zal geven als je npm packages global wilt gebruiken.

### Node - installeren op Windows
Er is geen NVM voor Windows. We gaan daarom naar de [node.js website](https://nodejs.org/) om node.js voor Windows te downloaden en installeren. Kies de LTS (Long-Term Support) versie, dit is de nieuwste stabiele versie. 

Node en npm zijn nu geinstalleerd. Dit kun je als volgt in PowerShell controleren:

```sh
node -v # Should print 18.13.0 (or a higher version)
npm -v # Something like 8.19.0 (or a higher version)
```

## 4. Node modules
Kijk eens rond op de [npm registry](https://www.npmjs.com/) of je packages kunt vinden, die handig zouden kunnen zijn voor je (backend) project. Daarnaast kun je kijken of je handige 'developer dependencies' op NPM kunt vinden, die straks je leven als developer makkelijk kunnen maken. Een goed voorbeeld is [nodemon](https://nodemon.io/), die automatisch je server herstart als je je code hebt aangepast. Super handig, dus dit is een goed moment om die vast te installeren.
