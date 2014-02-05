---
layout: post
title: Overzicht les 1
---

Hoi iedereen,

Bedankt voor de interesse gisteren! Wij kijken uit naar volgende week. Hier een overzicht van de eerste les:

* This will become a table of contents (this text will be scraped).
{:toc}

## Voor thuis
* [Installeer](/installatie/) Ruby en Sublime Text.
* Probeer de eerste paar bladzijden van de [command line crash course](http://cli.learncodethehardway.org/book/). In plaats van `cmd` werkt dit boek met `powershell`, maar de verschillen zijn heel klein. Bovendien hebben de computers op het Felisenum ook `powershell` (zoals één van jullie terecht opmerkte.)
* [Ruby Warrior](https://www.bloc.io/ruby-warrior/#/)! Wie komt er langs level 4? Zie onder voor een korte uitleg. De eerste die de code voor level 4 naar ons mailt krijgt een verrassing&hellip;

## Extra informatie hoofdstuk 1

### While loop (voor de extra opdracht)
Je hebt een programma dat "Hoi meneer!" of "Hoi mevrouw" en de juiste naam zegt. Hoe kun je er voor zorgen dat het programma doorgaat tot de gebruiker het _eindelijk_ goed heeft ingevoerd? Met een [while loop](http://localhost:4000/hoofdstuk2/#whileloop)!

Net als bij een [`if-statement`](http://localhost:4000/hoofdstuk1/#het_statement), checkt een while loop een [logische uitspraak](http://localhost:4000/hoofdstuk2/#logische_uitspraken). Welke logische uitspraak moeten we in dit geval checken? Wij hadden zoiets bedacht:

{% highlight ruby %}
correct = false
while correct == false do
    # De code
end
{% endhighlight %}
  
Ergens in de while loop zul je dan `correct = true` moeten zetten, zodat `correct == false` niet meer waar is. Dan stopt de while loop.

### Wat is `gets.chomp`?
Er staat in je programma `naam = gets`. Jij typt `Jan` in. Staat er in `naam` dan de waarde `"Jan"`? Nee! De enter, die je hebt ingetoetst om de input te beëindigen, is ook opgeslagen. `naam` heeft de waarde `"Jan\n"`. `"\n"` is een speciaal karakter dat een _newline_ (nieuwe regel) aangeeft --- een enter dus.

`chomp` haalt de newline aan het eind van een string weg. Lees [hier](http://www.ruby-doc.org/core-1.9.3/String.html#method-i-chomp) de officiële uitleg.

### Wat doet `"Hallo, #{naam}"`?
Hiermee zet je de waarde van `naam` op de juiste plek in de string. Je kunt daarna weer verder typen: `"Wat is #{naam} een mooie naam!"`.

Dit is niet de enige manier om strings aan elkaar te maken. Met `+` lukt het ook:

{% highlight ruby %}
naam = "Jan"
puts "Wat is " + naam + " een mooie naam!"
# => Wat is Jan een mooie naam!
{% endhighlight %}

Maar de eerste methode is in dit geval handiger.

### || (OF) en && (EN)
Als je wilt checken of `geslacht` de waarde `"vrouw"` of de waarde `"meisje"` bevat, moet je de OF-operator gebruiken. Dat gaat zo:

{% highlight ruby %}
if geslacht == "vrouw" || geslacht == "meisje"
    puts "Hallo mevrouw #{naam}!"
end 
{% endhighlight %}

Wat nou als je wilt kijken of de leeftijd groter is dan `10`, maar kleiner dan `20`? Dan gebruik je de EN-operator:

{% highlight ruby %}
if leeftijd > 10 && leeftijd < 20
    puts "Een tiener."
end 
{% endhighlight %}

### `!=` (niet gelijk aan)
Met `!=` eis je dat twee dingen _niet_ gelijk aan elkaar zijn.
{% highlight ruby %}
5 != 10             # => true
"Piet" != "Jan"     # => true
"Jan" != "Jan"      # => false
{% endhighlight %} 







