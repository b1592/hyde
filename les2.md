---
layout: default
title: Les 2
---

# Les 2: priemgetallen
In deze les gaan we bepalen of een getal priem is of niet. Een getal is priem als het alleen deelbaar is door 1 en door zichzelf. De eerste paar priemgetallen zijn:

    2, 3, 5, 7, 11, 13, 17, ...

Jullie gaan een _algoritme_ schrijven. Dat is een set instructies die tot een duidelijke conclusie leiden: is het gegeven getal een priemgetal, ja of nee?

## Booleans: waar of niet waar?
Ruby kent verschillende _datatypen_. `String` kennen jullie al. Gehele getallen zijn van het type `Integer`. Maar we hebben ook nog een ander datatype nodig: `Boolean`. Dit datatype heeft twee mogelijke waarden: `true` of `false`.

## Logische uitspraken
In bijna elk programma moeten er keuzes worden gemaakt: als dít waar is, doe dan dát. Dit soort _logische uitspraking_ leveren `true` of `false` op. Een paar voorbeelden (testen met `irb`!)

{% highlight ruby %}
8 > 5   # => true
6 < 6   # => false
6 <= 6  # => true

naam = "Piet"
naam == "Piet"  # => true
{% endhighlight %}    

## De modulo-operator
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

## While-loop
Het if-statement kennen jullie al. Hier wordt een eenmalige beslissing gemaakt.

## Bestanden

    prime.rb
    prime_test.rb
    les2.html

