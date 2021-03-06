---
author: lew
revision:
    "2018-06-13": "(A, lew) Första versionen."
...
HTML {#html}
=======================

Jag tänker att vi börjar med en sida och tillhörande CSS-fil, dess stylesheet. Start filen döper jag till `index.html` då de flesta webbläsare automatiskt letar efter en fil med just det namnet. Filändelsen kan variera men nu är det HTML vi ska skriva. Enklaste sättet att skapa filen är via sin texteditor eller via terminalen med kommandot `touch index.html`. Grundstrukturen är ett flertal HTML-taggar som behövs för att sidan ska fungera som tänkt. Följande kod skapar en bra grund:

```html
<!doctype html>
<html lang="en">
<head>
    <meta charset="utf-8">
    <title>Stormtrooper Murphy</title>
</head>
<body>

</body>
</html>
```

**&lt;!doctype html&gt;** är egentligen ingen HTML-tagg, utan en deklarering eller instruktion till webbläsaren att dokumentet innehåller HTML kod.

**&lt;html&gt;** representerar roten av dokumentet och verkar som en behållare för alla andra element som sidan behöver.

**&lt;html lang&gt;** talar om för webbläsaren vilket språk som kommer användas. Innehåller kommer tillslut vara på engelska.

**&lt;head&gt;** visas inte på sidan utan innehåller övrig information som vilken teckenkodning som ska användas eller titel på sidan (Den som syns uppe i fliken i webbläsaren).

**&lt;body&gt;** är själva stommen och ska husera allt innehåll som visas.

**&lt;title&gt;** är ganska självförklarande, det är titeln som ska visas i flikens topp.
