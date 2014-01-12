---
layout: default
title: Les 1
---

#Les 1: Hallo

In de eerste les maken we kennis met Ruby en het gebruik van Sublime Text. We praten tegen de computer en laten de computer terugpraten.

* This will become a table of contents (this text will be scraped).
{:toc}

##De bestanden

Net zoals in de rest van de cursus vind je in de map van deze opdracht een aantal bestanden:

    hallo.rb - het script waar je in gaat werken
    opdracht.html - deze beschrijving

##Informatie

###Command line

Als je een Rubyprogramma draait zit je in de commandline. Dit is een zwart scherm in Windows (ook in Mac/Linux) waarin je commando's kunt typen. Je start dit op door op Start te klikken en dan `cmd` te typen.  
Nu moeten we naar de map met alle bestanden van de cursus, die je eerder hebt gedownload. Op de regel waarop je kunt typen staat links voor de `>` de map waarin je nu zit. Je kunt nu naar een andere map met het commando `cd`, wat staat voor "change directory". (Een directory is een bestandsmap.)

Als in je scherm bijvoorbeeld staat:

    C:/>

dan kun je als je typt `cd Programmeren` gaan naar:

    C:/Programmeren>

Dit is al een soort programmeren: je praat direct met de computer in plaats van je muis te gebruiken. Probeer te gaan naar de map "Programmeren" die je hebt gedownload en dan door naar "Les 1".

Als je een map te ver bent gegaan, kun je een stap terug gaan met `cd ..`. Je kunt ook meerdere stappen tegelijk zetten: `cd map1/map2/../map3/`. Door op tab te drukken kun je commando's aanvullen, waardoor je minder hoeft te typen.

Probeer nu eens het commando `ruby hallo.rb`. Als het goed is zie je nu

    Hallo!

in beeld. Je laat de computer het script `hallo.rb` uitvoeren. Dit is het script waar we in gaan werken. Telkens als je je script wilt uitvoeren moet je het commando `ruby <scriptnaam>` intypen. Dit kun je makkelijk herhalen door op het pijltje omhoog op je toetsenbord te drukken. Je kunt gewoon je commandline open laten staan en steeds als je wat hebt veranderd in je script teruggaan en het laten uitvoeren.

###Het commando `puts`

Laten we beginnen met Ruby zelf. Open de map Programmeren in Sublime Text (`File -> Open Folder...`). Links zie je allerlei mappen (Les1, Les2 etc.) staan. Open nu het bestand `hallo.rb` in de map "Les1". Als alles goed gaat zie je nu

{% highlight ruby %}

puts "Hallo"

{% endhighlight %}

Dit is het scriptje dat je eerder in de commandline in actie zag. Het commando `puts` zorgt dat wat je erachter zet op het scherm verschijnt. Zo laat je de computer iets tegen jou zeggen. Maar hoe praat je nou terug? Daar is `gets` voor:

{% highlight ruby %}

naam = gets

{% endhighlight %}

Wat gebeurt hier? `naam` is een *variabele*. Dat is een soort opslagplaats voor informatie. Als je bijvoorbeelt zegt:

{% highlight ruby %}

geluksgetal = 1

{% endhighlight %}

dan sla je `1` op als `geluksgetal`. Later kun je dan bijvoorbeeld typen:

{% highlight ruby %}

puts geluksgetal

{% endhighlight %}

en dan geeft Ruby `1` als output.

Maar terug naar `gets`. Dit is een commando dat de gebruiker om *input* vraagt: je kunt dan dus iets intypen. Wat er gebeurt bij `naam = gets` is dat de computer wat je invoert opslaat als `naam`.

###Het commando `if`

Je wilt niet altijd dat de computer simpelweg een rij commando's achter elkaar uitvoert. Het moet slimmer worden. Hier zijn extra commando's voor nodig, en een van de krachtigste is `if`. Hiermee geef je aan dat de computer alleen iets moet uitvoeren onder een bepaalde voorwaarde en anders niet.

Neem bijvoorbeeld:

{% highlight ruby %}

if naam == "Jan"
    puts "De naam is Jan!"
end

{% endhighlight %}

Je kunt vast wel raden wat hier gebeurt: alleen als de variabele `naam` gelijk is aan "Jan", dan zegt de computer iets. Voor het vergelijken van twee waarden gebruik je `==`, een dubbel is-teken. Het enkele is-teken wordt al gebruikt om een waarde aan een variable toe te kennen. Vergeet het `if`-statement niet af te sluiten met `end`.

Maar stel nou dat de naam iets heel anders is, hoe zeg je dan wat de computer moet doen? Hiervoor heb je `else`:

{% highlight ruby %}

if naam == "Jan"
    puts "De naam is Jan!"
else
    puts "De naam is niet Jan!"
end

{% endhighlight %}

En om het nog iets mooier te maken: je kunt ook nog vragen of `naam` misschien iets anders is. Dit doe je met `elsif`:

{% highlight ruby %}

if naam == "Jan"
    puts "De naam is Jan!"
elsif naam == "Piet"
    puts "De naam is Piet!"
else
    puts "De naam is niet Jan!"
end

{% endhighlight %}

Je kunt er net zoveel `elsif`'s achter zetten als je wilt.

##De opdracht

Je weet nu alles wat je nodig hebt om zelf aan de slag te gaan met je eerste script. Je eerste script gaat over het communiceren met de computer. Schrijf een programma dat de volgende dingen doet:

* Begroet de gebruiker
* Vraagt de naam van de gebruiker
* Verwerkt de naam in een antwoord en vraagt de gebruiker om `jongen` of `meisje` in te typen
* Maakt een persoonlijke begroeting, waarin je de gebruiker aanspreekt met "Meneer" of "Mevrouw" en dan de naam, allemaal bepaald door wat de gebruiker eerder heeft ingetypt


