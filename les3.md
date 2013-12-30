---
layout: default
title: Les 3
---

#Les 3: Cipher

Al duizenden jaren proberen mensen elkaar berichten te versturen die niet door anderen mogen worden gelezen. Deze versleutelen ze op een manier die zo moeilijk mogelijk te kraken is. Een van de oudste manieren zou door Julius Caesar zelf zijn gebruikt en is redelijk eenvoudig. Hij schoof elke letter in een bericht een vast aantal plaatsen door in het alfabet. Dus hij maakte bijvoorbeeld van een 'a' een 'd', van een 'b' een 'e' etc. Met deze methode gaan we in deze opdracht aan de slag.

* This will become a table of contents (this text will be scraped).
{:toc}

##Bestanden

In deze map vind je de volgende bestanden:

    readme.html - deze beschrijving
    cipher.rb - het script waar je in gaat werken
    encrypted_message.txt - het versleutelde bestand met shift 12
    encrypted_brute_force.txt - voor de laatste opdracht

## Informatie

### Arrays
Een `Array` is een geordende collectie.

{% highlight ruby %}
namen = ["Harrie", "Maria", "Evelien", "Piet"]
{% endhighlight %}

Je spreekt een voorwerp uit een array aan met de index. Het eerste voorwerp uit de array correspondeert met index 0. 

{% highlight ruby %}
namen[0]    # => "Harrie"
namen[2]    # => "Evelien"
{% endhighlight %}

-1 correspondeert met het laatste element uit de array.

{% highlight ruby %}
namen[-1]   # => "Piet"
{% endhighlight %}

N.B. Je kunt ook strings op deze manier aanspreken!

{% highlight ruby %}
naam = "Jan"
naam[0]     # => "J"
{% endhighlight %}

### For Loops
Als je een opdracht een vast aantal keer uit moet voeren, gebruik je een for loop. Stel dat je elk element uit een array wilt aanspreken:

{% highlight ruby %}
for naam in namen do
    puts "Hallo, #{naam}!"
end
# => "Hallo, Harrie!"
# => "Hallo, Maria!"
# => "Hallo, Evelien!"
# => "Hallo, Piet!"
{% endhighlight %}

Je kunt ook over een bepaalde _range_ itereren. Experimenteer met de volgende loops in `irb`.

{% highlight ruby %}
for number in (0..100) do
    puts number
end

for letter in ("a"..."z")
    puts letter
end
{% endhighlight %}

Wat is het verschil tussen `(0..10)` en `(0...10)`?

### Hashes
Een `Hash` lijkt erg op een array, maar je spreekt een waarde uit de collectie niet met een index, maar met een _key_. Een key kan van elk datatype zijn. De volgende hash verbindt landen met hun hoofdsteden:

{% highlight ruby %}
hoofdsteden = {
    "Nederland" => "Amsterdam",
    "Frankrijk" => "Parijs",
    "Slowakije" => "Bratislava"
    }

hoofdsteden["Nederland"]    # => "Amsterdam"   
{% endhighlight %}

`"Nederland"` en `"Amsterdam"` worden samen een _key, value pair_ genoemd.

### File Input/Output
Stel dat je `bericht.txt` wilt inlezen. Dat gaat als volgt:

{% highlight ruby %}
contents = File.read('bericht.txt')
{% endhighlight %}

`contents` is nu een (hele lange) string.

Naar bestanden schrijven kan ook.

{% highlight ruby %}
file = File.open("test.txt", "w")
file.write("hallo!")
file.close
{% endhighlight %}

### Ruby Documentation
Nu jullie een aantal basisbegrippen hebben leren kennen, wordt het belangrijk dat jullie de documentatie van de ruby-taal leren lezen. Ook wij zoeken nog dagelijks dingen op.

* [http://www.ruby-doc.org/core-1.9.3/String.html](http://www.ruby-doc.org/core-1.9.3/String.html)
* [http://www.ruby-doc.org/core-1.9.3/Array.html](http://www.ruby-doc.org/core-1.9.3/Array.html)
* [http://www.ruby-doc.org/core-1.9.3/Hash.html](http://www.ruby-doc.org/core-1.9.3/Hash.html)

De volgende functies kunnen van pas komen: 

* `string.split`
* `array.join` 

Gebruik de bovenstaande documentatie (of gebruik google) om uit te vinden hoe je ze gebruikt.

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

###De functie `decrypt`

Als je iets codeert, wil je het natuurlijk ook weer terug kunnen vertalen. Hiervoor heb je deze functie nodig. We gaan er hier van uit dat je de 'sleutel' (dus de shift) weet. Denk goed na, je hoeft hiervoor niet veel nieuwe code te schrijven!

### (Extra) Leestekens

Je programma kan nu allerlei stukken tekst, zo lang als je maar wilt, versleutelen en weer decoderen. Maar je zult merken dat het niet meer werkt wanneer er andere tekens, zoals `; , . ! ?` in voor komen. Probeer een manier te bedenken om dit probleem te omzeilen en schrijf in `cipher_test.rb` een extra test om dit te testen.

### (Extra) Kraken zonder shift

Natuurlijk willen mensen de gecodeerde berichten proberen te ontcijferen. Dit is al snel erg lastig, maar ook hier kan een computer heel sterk zijn. Je kunt natuurlijk proberen de shift te achterhalen, maar als dit niet lukt zit er niks anders op dan gewoon alle mogelijkheden langs gaan. Dit wordt 'Brute Force' genoemd. Omdat een computer in staat is om heel snel achter elkaar mogelijkheden te testen, is dit een optie.

Probeer nu het andere bestand, waarvan je de shift niet weet, te kraken met behulp van brute force. Maak hierbij gebruik van de woordenlijst die ook in de map staat. Hoeveel mogelijkheden voor shift zijn er? En als je een shift probeert en daarmee het versleutelde bestand probeert te ontcijferen, waar zoek je dan naar? Met andere woorden, hoe weet de computer dat hij het goed ontcijferd heeft (en dus de juiste shift heeft gevonden)? Veel succes!
