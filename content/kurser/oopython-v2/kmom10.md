---
author: aar
revision:
    "2018-02-21": (A, aar) Först utgåva till V2.
...
Kmom10: Projekt och examination
==================================
[WARNING]

**Översikt pågår**

Kursmomentet är under översyn inför vårterminen 2019.

[/WARNING]

[INFO]
**Gör `dbwebb selfupdate` och `dbwebb update` innan du börjar med projektet.**
[/INFO]

Detta kursmoment avslutar och examinerar kursen.

Upplägget är enligt följande:

* Projektet och redovisning (20-80h)

Totalt omfattar kursmomentet (07/10) ca 20+20+20+20 studietimmar.



Projektidé och upplägg {#upplagg}
--------------------------------------------------------------------

Du frilansar som python-utvecklare och har precis tackat ja till ett uppdrag att utveckla ett bokningssytem för restauranger.

Utveckla ett objektorienterat system där det går att skapa användare och boka bord på restauranger. Du har möjligheten att själv välja om man ska använda systemet via terminalen eller om du vill ha en webbsida.

Innan du börjar med programmeringen ska du göra en analys över systemet du vill bygga och dokumentera det med klassdiagram.

Fråga i forumet om du känner dig osäker.


Bedömning och betygsättning {#bedomning}
--------------------------------------------------------------------

När du lämnat in projektet bedöms det tillsammans med dina tidigare redovisade kursmoment och du får ett slutbetyg på kursen. Läs om [grunderna för bedömning och betygsättning](kurser/bedomning-och-betygsattning).



Projektspecifikation {#projspec}
--------------------------------------------------------------------

Utveckla och leverera projektet enligt följande specifikation. Saknas info i specen kan du själv välja väg, dokumentera dina val i redovisningstexten.

De tre första kraven är obligatoriska och måste lösas för att få godkänt på uppgiften. De tre sista kraven är optionella krav. Lös de optionella kraven för att samla poäng och därmed nå högre betyg.

Varje krav ger max 10 poäng, totalt är det 60 poäng.



###Krav 1: Grunden {#k1}

Placera din kod i katalogen `me/kmom10/booking`. Filen som startar programmet skall heta `main.py`.


Gör ett program där en användare kan boka bord på olika restauranger. Tänk onlinepizza fast för att boka bord istället. Programmet ska användas via terminalen, som ni gjorde i kmom04 och 05.

####Kravspec:
Ska finnas:

* En restaurang ska ha ett namn, address och X antal bord.
* Ett bord ska ha X antal sittplatser. Borden ska kunna ha olika antal platser var.
* En användare ska ha ett namn och historik över vilka bord på vilka restauranger den har bokat.

Funktionalitet:

* Det ska gå att lägga till nya restauranger och bord till restaurangen.
* Det ska gå att lägga till/ta bort bord på existerande restauranger.
* Det ska gå att lägga till nya användare.
* En användare ska kunna boka ett eller flera bord på en restaurang.
* Det ska gå att välja en användare och se vilka bord och på vilken restaurang den har bokat.
* Det ska gå att se alla restauranger som finns.
* Det ska gå att se alla bord som finns på en restaurang.
    * Ska även kunna välja att bara se obokade eller bokade bord.
    * Det ska gå att se vem som har bokat borden.
* Det ska gå att söka efter en specifik restaurang.
* En användare ska kunna avboka bord.


Skapa minst två egna exceptions och använd i din kod. Beskriv dem i din redovisningstext.

Det ska inte finnas några "lösa" funktioner i din kod. Allt ska vara i klasser.



###Krav 2: Testning {#k2}

Skriv enhetstester för dina klasser. Spara testerna i filen `test.py`.

Minst tre tester för varje klass. Testa inte bara positiva utfall, testa även när saker går fel.
I dina enhetstester ska du ha en TestCase klass för varje klass du testar. Alltså lägg inte alla tester i en och samma TestCase klass.



###Krav 3: Klassdiagram {#k3}

**Innan du börjar programmera** ska du analyser och planera vad du ska koda. Tänkt ut vilka klasser du behöver och vilka attribut och metoder de ska.

Skapa klassdiagram för alla klasser du tänker att du behöver. Klassdiagrammen ska innehålla attribut, metoder och relationer mellan klasserna.

Klassdiagrammet ska lämnas in före du börjar koda projektet. Det finns en separat inlämmning på It's Learning för klassdiagrammet. **Du behöver inte vänta på att få godkänt innan du fortsätter med att programmera, det viktiga är att du har lämnat in det före.**

Så gör ett klassdiagram, lämna in det och sen börjar du koda projektet.

Det gör inget om koden skiljer sig från diagrammen när du är klar med projektet. Det blir inte alltid som man tänker sig.

När du har kodat klart projektet, jämför hur din kod faktiskt blev med hur du tänkte dig att det skulle fungera. I redovisningstexten skriver du hur din kod förhåller sig till diagrammet.


Spara som `classdiagrams.png`. Ladda upp filen på It's inlämningsuppgiften.


Se till att din kod validerar.

```bash
# Ställ dig i kurskatalogen
dbwebb publish kmom10
```



###Krav 4: Binary search (optionell) {#k4}

Implementera en Binary search algoritm och använd den när man ska söka efter en restaurang i programmet.

Kolla in [Khan Academy](https://www.khanacademy.org/computing/computer-science/algorithms/binary-search/a/binary-search) för en förklaring av hur algoritmen fungerar.



###Krav 5 och 6: Grafiskt gränssnitt på webben (optionell) {#k5}

Skapa en webbsida i Flask för ditt program. Om du gör detta kravet behöver ditt program inte fungera i terminalen. Du gör antingen webbsidan eller terminalen. Webbsidan ska uppfylla kravspecen från Krav 1.

Webbsidan ska även fungera på studentservern!  
Problemet vi har med studentservern och Flask är att CGI startar upp ditt program vid varje request och stänger ner det igen när  requestet är behandlat. Det gör att all data försvinner från minnet, ex alla värden du har sparat i listor och variabler, mellan requesten CGI skickar. Det gör att listorna och variablerna återställs till default vid varje request. Så när du har ändrat eller lagt till någon data, tex en ny restaurang eller gjort en bokning, måste du spara det till fil som du sedan läser upp vid varje request.

Kortfattat: Vid varje request läser du upp data från fil och när du ändrat eller lagt till/tagit bort data sparar du till filen.

Skapa filen `booking/db/data.json` och spara data i den.

I [example/read_write](https://github.com/dbwebb-se/oopython/tree/master/example/flask/read_write) finns kod som visar hur du kan jobba med att läsa och skriva till fil.

Koden som finns i app.py, som har med Flask att göra, behöver inte vara i en klass.



Redovisning {#redovisning}
--------------------------------------------------------------------

1. På din [redovisningssida](oopython-v2/redovisa), skriv följande:

    1. För varje krav du implementerat, dvs 1-6, skriver du ett textstycke om ca 5-10 meningar där du beskriver vad du gjort och hur du tänkt. Poängsättningen tar sin start i din text så se till att skriva väl för att undvika poängavdrag. Missar du att skriva/dokumentera din lösning så blir det 0 poäng. Du kan inte komplettera en inlämning för att få högre betyg.

    2. Skriv ett allmänt stycke om hur projektet gick att genomföra. Problem/lösningar/strul/enkelt/svårt/snabbt/lång tid, etc. Var projektet lätt eller svårt? Tog det lång tid? Vad var svårt och vad gick lätt? Var det ett bra och rimligt projekt för denna kursen?

    3. Avsluta med ett sista stycke med dina tankar om kursen och vad du anser om materialet och handledningen (ca 5-10 meningar). Ge feedback till lärarna och förslå eventuella förbättringsförslag till kommande kurstillfällen. Är du nöjd/missnöjd? Kommer du att rekommendera kursen till dina vänner/kollegor? På en skala 1-10, vilket betyg ger du kursen?

2\. Ta en kopia av texten på din redovisningssida och kopiera in den på Its/redovisningen. Glöm inte länka till din me-sida och projektet.

3\. Ta en kopia av texten från din redovisningssida och gör ett inlägg i [kursforumet](forum/utbildning/oopython) och berätta att du är klar.

4\. Se till att samtliga kursmoment validerar.

```bash
# Ställ dig i kurskatalogen
dbwebb publish me
```
