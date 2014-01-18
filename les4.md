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

###Globale variabelen

Je weet nu al veel van variabelen, maar we gaan er nog iets aan toevoegden. Daarvoor moet je begrijpen hoe ruby de variabelen inperkt. Stel dat je twee functies hebt:

{% highlight ruby %}
def functieA 
    functienaam = "A"
end

def functieB
    functienaam = "B"
end
{% endhighlight %}

Je ziet dat in beide functies variabelen staan met dezelfde naam. Misschien voel je al aan dat hier iets mis kan gaan: twee keer dezelfde variabele gebruiken gaat immers niet goed. Maar ruby beperkt de variabelen tot de functie waar ze in staan, dit noem je *lokale variabelen*.

Maar misschien wil je juist een variabele waar je in elke functie bij kan. Deze noem je *globale variabelen* en in ruby geef je deze aan met een dollarteken: `$variabele`. Overal in je script kun je deze variabelen oproepen en veranderen. Dit kan handig zijn, maar je moet er ook voorzichtig mee zijn. Gebruik dus nooit te veel globale variabelen.

##De opdracht

Je gaat beginnen met de computer de regels van het spel te leren. Zo moet hij weten wie er aan de beurt is, welke zetten er mogelijk zijn en wanneer het spel klaar is.

###Het bord

Om je op gang te helpen, hebben wij het spelbord voor je gemaakt. Als je het bestand `tictactoe.rb` opent, zie je een paar functies staan, waarvan vooral `drawboard` voor jou van belang is.

Het bord wordt opgeslagen als een 2D-array met rondjes en kruisjes. Bekijk eens het voorbeeld in het script:

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

###Spelregels

Het bord is nu geregeld. We slaan het bord op in de variabele `$board` (is dit een lokale of globale variabele?).

Nu het spel zelf. Schrijf eerst een functie die kijkt of het spel klaar is.




