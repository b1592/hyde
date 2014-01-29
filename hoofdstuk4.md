---
    layout: default
title: Les 4
---

#Hoofdstuk 4: Tic Tac Toe

*nog in ontwikkeling!*

<p><iframe width="420" height="315" src="//www.youtube.com/embed/F7qOV8xonfY"
  frameborder="0" allowfullscreen="allowfullscreen">  </iframe></p>

Wie kent het niet: boter, kaas en eieren? Het werd al rond 100 jaar voor Christus gespeeld door de Romeinen en nu nog steeds. We gaan in deze les het spel aan de computer uitleggen, zodat je het digitaal kunt spelen. En in de extra opdracht kun je zelfs de computer tegen jou laten spelen.

In deze les behandelen we:

* This will become a table of contents (this text will be scraped).
{:toc}

##Bestanden

In deze map vind je de volgende bestanden:

    readme.html
    tictactoe.rb
    game.rb

## Informatie

### Objecten

Om de echte wereld zo begrijpelijk mogelijk te vatten in code, gebruiken veel programmeertalen objecten (`Objects`). Ook Ruby. In onderstaand voorbeeld willen we boeken modelleren:

{% highlight ruby %}
class Book
    def initialize(author, title, content)
        @author = author
        @title = title
        @content = content
    end
end
{% endhighlight %}

Een klasse (`Class`) is de blauwdruk van een object.

`initialize` is een speciale functie, die wordt uitgevoerd zodra er een object van klasse `Book` wordt aangemaakt. Je maakt een object door `new` aan te roepen:

{% highlight ruby %}
book1 = Book.new("Lord of the Rings", "J. R. R. Tolkien", "Three Rings for the Elven-kings ...")
book2 = Book.new("Titaantjes", "Nescio", "Jongens waren we - maar aardige jongens. Al zeg ik 't zelf...")
{% endhighlight %}

Elk boek heeft dezelfde structuur, die wordt bepaalde door de klasse `Book`. Het is een container van de variabelen `author`, `title` en `content`. Variabelen die bij een object horen --- _instance variables_ --- beginnen met een `@`.

Deze variabelen zijn afgeschermd van de code buiten de klasse:

{% highlight ruby %}
book1.title # => NoMethodError: undefined method `title'
{% endhighlight %}

Als je bepaalde variabelen beschikbaar wilt maken, doe je dat met `attr_accessor`:

{% highlight ruby %}
class Book
    attr_accessor :title, :author, :content

    def initialize(author, title, content)
        @author = author
        @title = title
        @content = content
    end
end
{% endhighlight %}

Nu kunnen we aan het boek vragen wat zijn titel is:

{% highlight ruby %}
book1.title # => "Lord of the Rings"
book1.author # => "J. R. R. Tolkien"
{% endhighlight %}

En we kunnen attributen veranderen:

{% highlight ruby %}
book2.title = "De uitvreter"
book2.content = "Behalve den man, die de Sarphatistraat ..."

book2.title # => "De uitvreter"
{% endhighlight %}

So far so good.

Stel dat we willen bijhouden waar we zijn gebleven met lezen. Bij elk nieuw boek dat we maken, zetten we de variable `@current_page` op 1. Dit gebeurt dus in `initialize`. We schrijven een functie `flip_page`:

{% highlight ruby %}
class Book
    attr_accessor :title, :author, :content, :current_page

    def initialize(author, title, content)
        @author = author
        @title = title
        @content = content
        @current_page = 1
    end

    def flip_page
        @current_page = @current_page + 1
    end
end
{% endhighlight %} 

We kunnen nu dit doen (niet vergeten `:current_page` toe te voegen aan `attr_accessor`):

{% highlight ruby %}
book1.current_page # => 1
book1.flip_page 
book1.current_page # => 2
{% endhighlight %}

Als we de woorden van een boek nodig hebben, dan definiëren we gewoon een functie `words`!

{% highlight ruby %}
class Book
    attr_accessor :title, :author, :content, :current_page

    def initialize(author, title, content)
        @author = author
        @title = title
        @content = content
        @current_page = 1
    end

    def flip_page
        @current_page = @current_page + 1
    end

    def words
        @content.split(" ")
    end
end
{% endhighlight %}

{% highlight ruby %}
book1.words # => ["Three", "rings", "for", ...
{% endhighlight %}

Wat is het voordeel van objecten? Zodra we de blauwdruk hebben gespecificeerd, kunnen we precies vragen aan het object wat we nodig hebben. Niets meer en niets minder. Dit geeft overzicht, en maakt software hergebruiken makkelijk.

Nu weten jullie wat hier gebeurt:

{% highlight ruby %}
getallen = [1, 2, 3, 4, 5]
getallen.max # => 5
{% endhighlight %}

`getallen` is een object, van de klasse `Array`! `max` is een functie die in deze klasse staat gedefinieerd. Stiekem is alles in Ruby een object:

{% highlight ruby %}
"Obama".reverse # => "amabO"
{% endhighlight %}

`"Obama"` is een object van klasse `String`, met een functie `reverse`.

Laat je niet overdonderen. Het kost de meeste mensen minstens een half jaar om aan _objectgeörienteerd_ programmeren gewend te raken.

Voor het spel Tic Tac Toe gaan jullie een `Game`-object maken. Dit object bevat alle spellogica. Uiteindelijk is de bedoeling dat we aan het `Game`-object kunnen vragen wie er aan de beurt is, of het spel al over is, hoe het huidige bord eruit ziet, enzovoort. 

{% highlight ruby %}
game = Game.new
game.over? # => false
game.current_player # => "Player 1"
game.play(1)
game.current_player # => "Player 2"
{% endhighlight %}

### `require` en `require_relative`
Je hoeft het wiel niet opnieuw uit te vinden. Voorbeeld: je wilt random strings genereren. Daar heeft Ruby al iets op bedacht. Je "leent" het bestand `securerandom` uit de _standard library_. Hier staan alle files die standaard bij de Ruby-taal geleverd worden. Dat gaat zo:

{% highlight ruby %}
require "securerandom"

puts SecureRandom.hex
# => "eb693ec8252cd630102fd0d0fb7c3485"
{% endhighlight %}

Nu kun je alle code uit `securerandom` aanroepen, zonder te weten wat er precies in dat bestand staat. In de documentatie lees je wat je er allemaal mee kunt doen.

Grote programma's worden vaak gesplitst in meerdere bestanden. Dit geeft overzicht. Als je code uit je eigen mappen wilt aanroepen, moet je `require_relative` gebruiken.

In de map `Hoofdstuk4` staat `tictactoe.rb`. Dit bestand willen we uitvoeren om het spel te starten. Maar om het overzicht te bewaren, zetten we alle code van de klasse `Game` in `game.rb`. In `tictactoe.rb` roepen we vervolgens `game.rb` aan:

{% highlight ruby %}
# tictactoe.rb
require_relative "game"

game = Game.new
{% endhighlight %}

Zoals je ziet, kun je `.rb` weglaten uit de bestandsnaam.

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

Nu het spel zelf. Schrijf eens, zonder computer, voor jezelf op wat voor functies je nodig gaat hebben. Je mag zelf weten hoe je je programma gaat opbouwen. Een mogelijkheid is om te beginnen met een functie waar je aan kunt vragen of het spel al voorbij is (3 op een rij of bord vol).

###De speelbeurten

Nu schrijf je een functie die vraagt om een zet (met `gets`) en dan het spelbord bijwerkt. En dit moet natuurlijk afwisselend voor speler 1 en speler 2. Maak hierbij gebruik van de cijfers voor de plekken op het bord zoals in de functie `drawboard`.

Controleer wel of een ingevoerde zet mag en of dan het het spel nog verder gaat of dat het voorbij is. Laat dan de functie stoppen en zeg wie er heeft gewonnen, of dat het gelijkspel is.



