---
layout: default
title: Les 1
---

#Les 1: Hallo

We maken kennis met Ruby en Sublime Text. We praten tegen de computer en laten de computer terugpraten.

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

Dit is al een soort programmeren: je praat direct met de computer in plaats van je muis te gebruiken. Probeer te gaan naar de map "Programmeren" die je hebt gedownload en dan naar "Les 1".

Als je een map te ver bent gegaan, kun je een stap terug gaan met `cd ..`. Je kunt ook meerdere stappen tegelijk zetten: `cd map1/map2/../map3/`. Door op tab te drukken kun je commando's aanvullen, waardoor je minder hoeft te typen.

Probeer nu eens het commando `ruby hallo.rb`. Als het goed is zie je nu

    Hallo!

in beeld. Je laat de computer het script `hallo.rb` uitvoeren. Dit is het script waar we in gaan werken. Telkens als je je script wilt uitvoeren moet je het commando `ruby <scriptnaam>` intypen. Met pijltje-omhoog en pijltje-omlaag kun je terugzien die je eerder hebt ingetypt. Laat je commandline open staan, dan kun je script steeds uitvoeren als je wat hebt veranderd.

###Het commando `puts`

Naar het script zelf! Open de map Programmeren in Sublime Text. (`File -> Open Folder...`). Links zie je allerlei mappen (Les1, Les2, etc.) staan. Open nu het bestand `hallo.rb` in de map "Les1". Daar staat:

{% highlight ruby %}

puts "Hallo"

{% endhighlight %}

Dit scriptje zag je eerder in de commandline in actie. Het commando `puts` zorgt zet wat er achter staat op het scherm. Zo laat je de computer iets tegen je zeggen. Maar hoe praat je nou terug? Daar is `gets` voor:

{% highlight ruby %}

naam = gets

{% endhighlight %}

Wat gebeurt hier? `naam` is een *variabele*. Dat is een soort opslagplaats voor informatie. Als je zegt:

{% highlight ruby %}

geluksgetal = 1

{% endhighlight %}

dan sla je `1` op als `geluksgetal`. Later kun je typen:

{% highlight ruby %}

puts geluksgetal

{% endhighlight %}

en dan geeft Ruby `1` als output.

Maar terug naar `gets`. Dit is een commando dat de gebruiker om *input* vraagt: je kunt iets intypen. Wat er gebeurt bij `naam = gets` is dat de computer wat je invoert opslaat als `naam`.

###Het `if`-statement

Een programma is meer dan een rij commando's, die achter elkaar worden uitgevoerd. Een computer kan ook keuzes maken. Hier zijn aparte commando's voor nodig, en één van de krachtigste is `if`. Hiermee geef je aan dat de computer alleen iets moet uitvoeren onder een bepaalde voorwaarde en anders niet.

Neem bijvoorbeeld:

{% highlight ruby %}

if naam == "Jan"
    puts "De naam is Jan!"
end

{% endhighlight %}

Je kunt vast wel raden wat hier gebeurt: alleen als de variabele `naam` gelijk is aan "Jan", dan zegt de computer iets. Voor het vergelijken van twee waarden gebruik je `==`, een dubbel is-teken. Vergeet het `if`-statement niet af te sluiten met `end`.

Maar als de naam geen Jan is, hoe zeg je dan wat de computer moet doen? Hiervoor heb je `else`:

{% highlight ruby %}

if naam == "Jan"
    puts "De naam is Jan!"
else
    puts "De naam is niet Jan!"
end

{% endhighlight %}

En om het nog mooier te maken: je kunt ook nog vragen of `naam` misschien Piet is. Dit doe je met `elsif`:

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

Je weet nu alles wat je nodig hebt om zelf aan de slag te gaan. Je eerste script gaat over het communiceren met de computer. Schrijf een programma dat de volgende dingen doet:

* Begroet de gebruiker
* Vraagt de naam van de gebruiker
* Verwerkt de naam in een antwoord en vraagt de gebruiker om `jongen` of `meisje`, of `man` of `vrouw` in te typen.
* Maakt een persoonlijke begroeting, waarin je de gebruiker aanspreekt met "Meneer" of "Mevrouw" en dan de naam, allemaal bepaald door wat de gebruiker eerder heeft ingetypt