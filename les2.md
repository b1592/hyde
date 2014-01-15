---
layout: default
title: Les 2
---

# Les 2: priemgetallen
In deze les gaan we bepalen of een getal priem is of niet. Een getal is priem als het alleen deelbaar is door 1 en door zichzelf. De eerste paar priemgetallen zijn:

    2, 3, 5, 7, 11, 13, 17, ...

Jullie gaan een _algoritme_ schrijven. Dat is een set instructies die tot een duidelijke conclusie leiden: is het gegeven getal een priemgetal, ja of nee?

* This will become a table of contents (this text will be scraped).
{:toc}

## Bestanden

    prime.rb - jullie code
    prime_test.rb
    les2.html

## Informatie

### Booleans: waar of niet waar?
Ruby kent verschillende _datatypen_. `String` kennen jullie al. Gehele getallen zijn van het type `Integer`. Maar we hebben ook nog een ander datatype nodig: `Boolean`. Dit datatype heeft twee mogelijke waarden: `true` of `false`.

### Logische uitspraken
In bijna elk programma moeten er keuzes worden gemaakt: als dít waar is, doe dan dát. Deze _logische uitspraken_ leveren `true` of `false` op. Een paar voorbeelden (testen met `irb`!)

{% highlight ruby %}
8 > 5   # => true
6 < 6   # => false
6 <= 6  # => true

naam = "Piet"
naam == "Piet"  # => true
{% endhighlight %}    

### De modulo-operator
Een belangrijke operator voor deze opdracht is `%`, de modulo-operator. Deze geeft de rest terug van deling van twee getallen.

{% highlight ruby %}
10 % 3  # => 1
17 % 7  # => 3
8 % 2   # => 0

# is 14 deelbaar door 3?
14 % 3 == 0 # => false
# is 12 deelbaar door 4?
12 % 4 == 0 # => true
{% endhighlight %} 

### While-loop
Een if-statement is een eenmalige beslissing. Maar soms wil je met een opdracht doorgaan zolang als _(while)_ een bepaalde uitspraak waar is. Haal een ei uit de doos, zolang er nog eieren zijn. Wat komt hier uit?

{% highlight ruby %}
counter = 0
while counter < 10 do
    counter = counter + 1
end
puts counter
{% endhighlight %}

### Functies
Een functie is één van de belangrijkste wapens die een programmeur tot zijn beschikking heeft. Wat voorbeelden (test zoals altijd met `irb`.)

{% highlight ruby %}
# Een functie begint met def, en wordt niet direct uitgevoerd.
def f(x)
    return x + 1
end

f(4)    # => 5

def greet(naam)
    return "Hallo, #{naam}!"
end

greet("Bob")    # => "Hallo, Bob!"

# Meerdere variabelen.
def multiply(a, b)
    return a * b
end

multiply(5, 8)  # => 40
{% endhighlight %} 

Een functie geeft overzicht en scheelt behoorlijk wat typwerk. Stel dat je drie mensen wilt begroeten.

{% highlight ruby %}
greet("Anna")
greet("Bert")
greet("Chloe")
{% endhighlight %}

Als je nu de groet wilt veranderen, hoef je alleen maar de functiedefinitie aan te passen (`def ... end`). Dan worden Anna, Bert en Chloe meteen op de juiste manier begroet.

## De opdracht
Jullie gaan een functie schrijven die `false` teruggeeft als het getal niet priem is, en `true` als het getal wel priem is. Dit is de bedoeling:

{% highlight ruby %}
def prime?(number)
    # Algoritme ...
end

prime?(8)   # => false
prime?(13)  # => true
prime?(104729)  # => true 
{% endhighlight %}

### Tests
We hebben een programma geschreven dat je functie aan een paar simpele tests onderwerpt. Dit programma voer je uit met:

    ruby prime_test.rb

Aan de slag!
