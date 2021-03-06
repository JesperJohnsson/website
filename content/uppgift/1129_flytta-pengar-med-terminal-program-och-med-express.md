---
author: mos
category:
    - javascript
    - nodejs
    - mysql
    - express
    - kursen dbjs
    - kursen databas
revision:
    "2018-01-09": (A, mos) Första utgåvan.
...
Flytta pengar med terminalprogram och med Express
==================================

Du skall bygga två klienter mot en databas, den ena klienten är textbaserad och körs i terminalen med ett menysystem och kommandon. Den andra klienten är webbaserad och använder Express som server.

Databasen innehåller en tabell som simulerar bankkonton och du skall via båda klientern utföra funktionen att flytta pengar mellan kontona.

Flytten av pengar skall utföras inom ramen av en transaktion.

<!--more-->



Förkunskaper {#forkunskaper}
-----------------------

Du har jobbat igenom "[Transaktioner i databas](kunskap/transaktioner-i-databas)" och du har tillgång till databasen från exemplet.

Du har jobba igenom artikeln "[Koppla appservern Express till databasen MySQL](kunskap/koppla-appservern-express-till-databasen-mysql)" och du har en kodbas från artikeln som ger dig en webbklient.

Du har löst uppgiften "[Node.js terminalprogram mot MySQL med kommandoloop](uppgift/nodejs-terminalprogram-mot-mysql-med-kommandoloop)" och har därmed ett terminalprogram att utgå ifrån.



Introduktion {#intro}
-----------------------

Du har skapat en webbklient där du kan visa innehållet från databasen i en tabell.

Du har sedan tidigare skapat en terminalklient där du kan utföra kommandon via ett menysystem i en kommandoloop.

Du skall nu utföra funktionen att flytta pengar mellan två konton och man skall kunna göra det via terminalklienten och via webbklienten.

I båda klienterna så hårdkodar vi att 1.5 pengar flyttas från ena kontot till det andra. Användaren kan i detta läget inte bestämma hur mycket pengar som flyttas eller från vilket konto och till vilket konto. 

I nästa kmom gör vi flytten mer flexibel så man kan bestämma konto och antal pengar.

Utseendet på webbklienten kan vara så här.

[FIGURE src=image/snapvt18/bank-move-to-adam.png caption="Adam har precis fått 1.5 pengar."]

Utseendet på terminalklienten kan vara så här.

[FIGURE src=image/snapvt18/bank-terminal-move.png caption="Via terminalklienten kan du flytta pengar till Eva, i skydd av en transaktion."]

Tänk på din kodstruktur, här finns kod som går att återanvända och dela mellan klienterna. Ett visst fokus i uppgiften är att finna en struktur där du kan dela kod mellan de båda klienterna.



Flera SQL frågor inuti en {#flera}
-----------------------

I [npm-modulen mysql](https://www.npmjs.com/package/mysql) finns möjligheten att utföra en [multiquery](https://www.npmjs.com/package/mysql#multiple-statement-queries), ett anrop till databasen som består av flera SQL-satser. Det är något som passar bra i denna uppgiften där vi vill använda transaktioner för att säkerställa flytten av pengar.

I länken ovan visas hur du enablar multiquery i modulen, det är avstängt från början. Sätter du inte på det så får du ett felmeddelande på andra SQL-satsen.

Du sätter enkelt på funktionen genom att lägga till följande i din `config/db/bank.json`.

```json
{
    "multipleStatements": true
}
```


Krav {#krav}
-----------------------

1. Inloggningsdetaljer till databasen skall sparas i `config/db/bank.json` och delas mellan webbklient och terminalklient.

1. Flytten av pengar skall utföras inom ramen för en transaktion.

1. Bygg vidare på din webbklient och lägg till en sida `bank/move-to-adam`. Varje gång man går in på den sidan skall det flyttas 1.5 pengar till Adam från Eva. Sidan visar bara ett tackmeddelande från Adam som tackar för pengarna.

1. Sidlayouten skall vara gemensam och innehålla en navigeringsmöjlighet mellan de sidor som är relaterade till banken.

1. Bygg ett terminalprogram och spara main-funktionen i `cli.js`. Eventuell övrig kod lägger du i moduler under katalogen `src/`. Terminalprogrammet skall startas med `node cli.js`.

1. Ditt terminalprogram skall fungera som en oändlig kommandoloop där man kan skriva in kommandon som programmet utför. Det skall finnas ett kommando `menu` som visar menyn med samtliga kommandon. När man skriver kommandot `exit` skall programmet avslutas.

1. I terminalprogrammet, skapa kommandot `move` som flyttar 1.5 pengar från Adam till Eva.

1. Validera din kod.

```bash
# Flytta till kurskatalogen
dbwebb validate express-sql
```

Rätta eventuella fel som dyker upp och publisera igen. När det ser grönt ut så är du klar.



Extrauppgift {#extra}
-----------------------

Gör följande om du har tid och ro.

1. Lägg till kommandot `balance` i terminalen så att du kan se balansen på konton, på liknande sett man gör i webbklienten.

1. Jobba på din kodstruktur så att du bli nöjd. Se till att du kan återanvända databaskoden mellan de båda klienterna. Strukturera koden i funktioner och moduler.



Tips från coachen {#tips}
-----------------------

Lycka till och hojta till i forumet om du behöver hjälp!
