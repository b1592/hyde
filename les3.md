---
layout: default
title: Les 3
---

#Les 3: Cipher

## Arrays
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

## For Loops
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

## Hashes
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

## File Input/Output
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

## Ruby Documentation
Nu jullie een aantal basisbegrippen hebben leren kennen, wordt het belangrijk dat jullie de documentatie van de ruby-taal leren lezen. Ook wij zoeken nog dagelijks dingen op.

* [http://www.ruby-doc.org/core-1.9.3/String.html](http://www.ruby-doc.org/core-1.9.3/String.html)
* [http://www.ruby-doc.org/core-1.9.3/Array.html](http://www.ruby-doc.org/core-1.9.3/Array.html)
* [http://www.ruby-doc.org/core-1.9.3/Hash.html](http://www.ruby-doc.org/core-1.9.3/Hash.html)

De volgende functies kunnen van pas komen: 

* `string.split`
* `array.join` 

Gebruik de bovenstaande documentatie (of gebruik google) om uit te vinden hoe je ze gebruikt.