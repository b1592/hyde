---
layout: default
title: Les 3
---

#Les 3: Cipher

Al duizenden jaren proberen mensen elkaar berichten te versturen die niet door anderen mogen worden gelezen. Deze versleutelen ze op een manier die zo moeilijk mogelijk te kraken is. Een van de oudste manieren zou door Julius Caesar zelf zijn gebruikt en is redelijk eenvoudig. Hij schoof elke letter in een bericht een vast aantal plaatsen door in het alfabet. Dus hij maakte bijvoorbeeld van een 'a' een 'd', van een 'b' een 'e' etc. Met deze methode gaan we in deze opdracht aan de slag.

* This will become a table of contents (this text will be scraped).
{:toc}

##De opdracht

###De functie `build_hash`

In deze opdracht ga je computer inzetten om berichten snel te versleutelen en weer te ontcijferen. Hiervoor zul je een aantal functies moeten schrijven. Begin bij een functie `build_hash`, die met een gegeven 'shift' (het aantal plaatsen dat elke letter moet worden verschoven) een hash aanmaakt.  
In deze hash moet elke letter in het alfabet gekoppeld worden aan de letter waar hij door vervangen moet gaan worden. Dus een shift van 3 zou zoiets moeten opleveren:

{% highlight ruby %}

{"a"=>"d", "b"=>"e", "c"=>"f", "d"=>"g", "e"=>"h", "f"=>"i", "g"=>"j", "h"=>"k", "i"=>"l", "j"=>"m", "k"=>"n", "l"=>"o", "m"=>"p", "n"=>"q", "o"=>"r", "p"=>"s", "q"=>"t", "r"=>"u", "s"=>"v", "t"=>"w", "u"=>"x", "v"=>"y", "w"=>"z", "x"=>"a", "y"=>"b", "z"=>"c"}

{% endhighlight %}

Je ziet hier dus dat bijvoorbeeld de "a" drie plaatsen is opgeschoven en in het gecodeerde bericht een "d" wordt.

###De functie `encrypt`

Dit is de functie waar het allemaal om draait. Als je deze functie een bericht en een bepaalde shift geeft, zou het de build_hash functie moeten aanroepen en dan vervolgens het bericht letter *voor* letter (denk hierbij aan een `for`loop) moeten coderen tot een rij tekst waar je niks zinnigs meer in ziet.

##De functie `decrypt`

Als je iets codeert, wil je het natuurlijk ook weer terug kunnen vertalen. Hiervoor heb je deze functie nodig. We gaan er hier van uit dat je de 'sleutel' (dus de shift) weet. Denk goed na, je hoeft hiervoor niet veel nieuwe code te schrijven!

## (Extra) Leestekens

Je programma kan nu allerlei stukken tekst, zo lang als je maar wilt, versleutelen en weer decoderen. Maar je zult merken dat het niet meer werkt wanneer er andere tekens, zoals `; , . ! ?` in voor komen. Probeer een manier te bedenken om dit probleem te omzeilen en schrijf in `cipher.rb` een extra test om dit te testen.

## (Extra) Kraken zonder shift

Natuurlijk willen mensen de gecodeerde berichten proberen te ontcijferen. Dit is al snel erg lastig, maar ook hier kan een computer heel sterk zijn. Je kunt natuurlijk proberen de shift te achterhalen, maar als dit niet lukt zit er niks anders op dan gewoon alle mogelijkheden langs gaan. Dit wordt 'Brute Force' genoemd. Omdat een computer in staat is om heel snel achter elkaar mogelijkheden te testen, is dit een optie.

Probeer nu het andere bestand, waarvan je de shift niet weet, te kraken met behulp van brute force. Maak hierbij gebruik van de woordenlijst die ook in de map staat. Hoeveel mogelijkheden voor shift zijn er? En als je een shift probeert en daarmee het versleutelde bestand probeert te ontcijferen, waar zoek je dan naar? Met andere woorden, hoe weet de computer dat hij het goed ontcijferd heeft (en dus de juiste shift heeft gevonden)? Veel succes!