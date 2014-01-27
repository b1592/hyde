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

    readme.html - deze beschrijving
    tictactoe.rb - het script waar je in gaat werken

## Informatie

### Objecten

Om de echte wereld zo begrijpelijk mogelijk te modelleren, kennen veel programmeertalen objecten (`Objects`). Een klasse (`Class`) is de blauwdruk van een object. Dat kan er zo uit zien:

{% highlight ruby %}
class Book
    def initialize(author, title, content)
        @author = author
        @title = title
        @content = content
    end
end
{% endhighlight %}

`initialize` is een speciale functie, die wordt uitgevoerd zodra er een object van klasse `Book` wordt aangemaakt. Je maakt een object door `new` aan te roepen.

{% highlight ruby %}
book1 = Book.new("Lord of the Rings", "J. R. R. Tolkien", "Three Rings for the Elven-kings ...")
book2 = Book.new("Titaantjes", "Nescio", "Jongens waren we - maar aardige jongens. Al zeg ik 't zelf...")
{% endhighlight %}

Zoals je ziet heeft elk boek dezelfde structuur. Het is een soort container van de variabelen `author`, `title` en `content`. Variabelen die bij een object horen, zogenaamde _instance variables_, beginnen met een `@`.

Deze variabelen zijn afgeschermd van de code buiten de klasse. Je kunt er van buitenaf niet bij:

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

Stel dat we de pagina's willen bijhouden die we hebben gelezen. Bij elk nieuw boek dat we maken, zetten we de variable `@current_page` op 1. Dit gebeurt dus in de initialize. Vervolgens kunnen we de functie `flip_page` aanroepen:

{% highlight ruby %}
class Book
    attr_accessor :title, :author, :content, :@current_page

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

We kunnen nu dit doen:

{% highlight ruby %}
book1.current_page # => 1
book.flip_page 
book.current_page # => 2
{% endhighlight %}

Wat is het voordeel van objecten? Zodra we de blauwdruk eenmaal hebben gespecificeerd, kunnen we precies vragen aan het object wat we nodig hebben. Niets meer en niets minder.

Voor het spel Tic Tac Toe gaan jullie een `TicTacToe`-object maken. Dit object bevat alle spellogica. Uiteindelijk is de bedoeling dat we aan het `TicTacToe` object kunnen vragen wie er aan de beurt is, of het spel al over is, hoe het huidige bord eruit ziet, enzovoort. 

{% highlight ruby %}
game = TicTacToe.new
game.over? # => false
game.current_player # => "Player 1"
{% endhighlight %}

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

Nu het spel zelf. Schrijf eens, zonder computer, voor jezelf op wat voor functies je nodig gaat hebben. Je mag zelf weten hoe je je programma gaat opbouwen. Een mogelijkheid is om te beginnen met een functie waar je aan kunt vragen of het spel al voorbij is (3 op een rij of bord vol).

###De speelbeurten

Nu schrijf je een functie die vraagt om een zet (met `gets`) en dan het spelbord bijwerkt. En dit moet natuurlijk afwisselend voor speler 1 en speler 2. Maak hierbij gebruik van de cijfers voor de plekken op het bord zoals in de functie `drawboard`.

Controleer wel of een ingevoerde zet mag en of dan het het spel nog verder gaat of dat het voorbij is. Laat dan de functie stoppen en zeg wie er heeft gewonnen, of dat het gelijkspel is.



