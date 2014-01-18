---
    layout: default
title: Les 4
---

#Les 4: Tictactoe

Wie kent het niet: boter, kaas en eieren? Het werd al rond 100 jaar voor Christus gespeeld door de Romeinen en nu nog steeds. We gaan in deze les het spel aan de computer uitleggen, zodat je het digitaal kunt spelen. En in de extra opdracht kun je zelfs de computer tegen jou laten spelen!

In deze les behandelen we:

* This will become a table of contents (this text will be scraped).
{:toc}

##Bestanden

In deze map vind je de volgende bestanden:

    readme.html - deze beschrijving
    tictactoe.rb - het script waar je in gaat werken

## Informatie

###2D-array

Je hebt al kennis gemaakt met arrays. Nu gaan we een stapje verder: tweedimensionale arrays. Dit zijn eigenlijk arrays in arrays. Het spelbord dat je straks zal gebruiken is precies dat:

{% highlight ruby %}
[["X", "X", "O"], ["O", "O", "X"], [" ", " ", "O"]]
{% endhighlight %}

Als je hier even goed naar kijkt, zie je dat er een grote array is met daarin drie kleine arrays. Deze kleine arrays met elk drie elementen vormen de rijen van de tabel. Deze 2D-array ziet er zo uit in tabelvorm:

     X | X | O 
    ---|---|---
     O | O | X 
    ---|---|---
       |   | O 

Probeer zelf eens een paar van dit soort arrays te maken in `irb`, zodat je echt begrijpt hoe ze werken.

##De opdracht

Je gaat beginnen met de computer de regels van het spel te leren. Zo moet hij weten wie er aan de beurt is, welke zetten er mogelijk zijn en wanneer het spel klaar is.

Om je op gang te helpen, hebben wij het spelbord voor je gemaakt. Als je het bestand `tictactoe.rb` opent, zie je een paar functies staan, waarvan vooral `drawboard` voor jou van belang is.

Het bord wordt opgeslagen als een `array` met rondjes en kruisjes. Bekijk eens het voorbeeld in het script:

{% highlight ruby %}
voorbeeldbord = [[" ", "X", " "], 
                 ["O", "X", " "], 
                 [" ", " ", "O"]]
{% endhighlight %}

Als je deze wilt tekenen, typ je in: 

{% highlight ruby %}
puts drawboard(voorbeeldboard)
{% endhighlight %}

Kijk maar wat je dan krijgt! Als het goed gaat, zie je nog een bord ernaast met cijfers. Deze cijfers geven de plaats op het bord aan.

