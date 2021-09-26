# Hashes (Hash Yapısı)

Bu yapı dizilerin kuzenidir.Ruby'deki hashler daha gelişkin bir koleksiyon yapısıdır. Javascriptteki obje ve Pythondaki sözlük yapısına benzer.

Key,value yapısı üzerine kurulmuştur. Birbiri ile alakasız veri gruplarını bir arada tutabilirler.

Örneğin:

```ruby 
my_hash = { 
  "a random word" => "ahoy", 
  "Mahmut's math test score" => 94, 
  "an array" => [1, 2, 3],
  "an empty hash within a hash" => {} 
}
``` 

Aynı arrayler gibi new metodu ile de oluşturulabilirler:

```ruby
my_hash = Hash.new
my_hash               #=> {}
```

Eskiden şöyle de tanımlanırlarmış:

```ruby
old_syntax_hash = {:name => 'bob'}
```

ama modern tanımlama şekli şöyle:

```ruby
new_hash = {name: 'bob'}
```

Her iki yötem de çalışır tabii.

Genel olarak formül şu :

```ruby
hash_name = {key: value}
```

burada key dediğimiz kısım string olmak zorunda değil, sembol veya sayı da olabilir. 

Örneğin aşağıdaki örnek de doğru bir tanım içeriyor:

```ruby
hash = { 9 => "nine", :six => 6 }
```

Bir insanı yüzeysel olarak şu şekilde tanımlayabilirdim:

```ruby
 person = { name:'Emre' , height: '175cm'}
```

## Değerlere erişme

Örneğin yukarıdaki insanın adına erişmek için 

```ruby 
person[:name]
```

kullanabilirim. Fakat,

```ruby
person["name"]
```
ile isim değerine erişmek istediğimde nil değeri dönüyor.

Peki hash'i şu şekilde tanımlasaydım ne olurdu? 

```ruby 
person = {
    "name" => "Emre",
    "height" => "175cm"
}
```

```ruby
person["name"] # Emre dönüyor
person[name] # NameError (undefined local variable or method `name' for main:Object) dönüyor
``` 

Örneğin şu şekilde bir tanım yapmaya çalıştığımda:

```ruby
person = {
    name => 'Emre',
    height => '175cm'
}
#NameError (undefined local variable or method `name' for main:Object) hatası alıyorum
``` 

Kullanım alanlarına göre ayakkabıları içeren bir yapı kurgulayalım:

```ruby

shoes = {
  "summer" => "sandals",
  "winter" => "boots"
}

shoes["summer"]   #=> "sandals" 
```

Peki doğa yürüyüşü ayakkabısını bu hashten çağırmak istersem ? 

```ruby
shoes["hiking"]   #=> nil 
```

Nil değeri döndü çünkü böyle bir tanım yapmadık.

Bazen bu şekilde sessiz sedasız nil değeri dönmesi programlarda problemlere yol açabiliyormuş. Bu nedenle hahs'te olmayan bir anahtara erişmeye çalıştığımızda böyle bir keyin hashin içinde olmadığına dair bilgi dönen fetch adında bir metot geliştirmişler.

```ruby
shoes.fetch("hiking") # KeyError (key not found: "hiking") şeklinde bir hata dönüyor
```
Alternatif olarak, bu yöntem, verilen anahtar bulunamazsa bir hata oluşturmak yerine varsayılan bir değer döndürebilir. 

```ruby
shoes.fetch("hiking", "hiking boots") #=> "hiking boots"
```

## Veri Ekleme ve Değiştirme

```ruby
shoes["fall"] = "sneakers"
``` 

ile yeni bir anahtar değer tanımı eklemiş olduk.

```ruby
{"summer"=>"sandals", "winter"=>"boots", "fall"=>"sneakers"}
```

Mevcut bir anahtarın değerini değiştirebilirdik:

```ruby
shoes["summer"] = "flip-flops"
shoes     #=> {"summer"=>"flip-flops", "winter"=>"boots", "fall"=>"sneakers"}
```

## Veri silme 

delete metodunu kullanarak verileri silebiliyoruz:

```ruby
shoes.delete("summer")    #=> "flip-flops"
shoes                     #=> {"winter"=>"boots", "fall"=>"sneakers"}
```

## Metotlar

keys ve values metotları anahter ve değerleri döner.


```ruby
books = { 
  "Infinite Jest" => "David Foster Wallace", 
  "Into the Wild" => "Jon Krakauer" 
}

books.keys      #=> ["Infinite Jest", "Into the Wild"]
books.values    #=> ["David Foster Wallace", "Jon Krakauer"]
```

## İki Hash'i Birleştirme

merge metodu iki hash'i birleştirmek için kullanılabilir.

```ruby
hash1 = { "a" => 100, "b" => 200 }
hash2 = { "b" => 254, "c" => 300 }
hash1.merge(hash2)      #=> { "a" => 100, "b" => 254, "c" => 300 }
```

Görüldüğü üzere hash2 deki b anahtar değeri hash1 deki b anahtar değerini ezdi. Merge metodu iki hash'i birleştirip değeri dönüyor fakat hashlerin içeriğini tamamen değiştirmiyor. Merge işleminden sonra hash1'i tekrar çağırırsak:

```ruby
{"a"=>100, "b"=>200}
```

değerine ulaşırız.

## Hash yapılarında sembol kullanımı

Yukarıda örneklerini görmüştük. Ruby'de hash tanımı için birden fazla yol var. Bunlar rocket syntax ve symbol syntax olarak geçiyor.

```ruby
# 'Rocket' syntax 
american_cars = { 
  :chevrolet => "Corvette", 
  :ford => "Mustang", 
  :dodge => "Ram" 
}
# 'Symbols' syntax
japanese_cars = { 
  honda: "Accord", 
  toyota: "Corolla", 
  nissan: "Altima" 
}
```

symbol syntax daha fazla tercih edilen bir yöntemmiş çünkü Ruby'de semboller stringlerden daha performanslı çalışmaktaymış. Fakar symbol syntaxı sadece semboller ile çalışıyor. Yukarıda aldığımız hataların sebebi de buydu. Yani  { 9: “value” } gibi bir tanım yapamıyoruz. Ayrıca symbol syntax'ında tanımladığımız hashlerin anahtar değerlerine : ile ulaşabiliyoruz.

Örneğin:

```ruby
japanese_cars = { 
  honda: "Accord", 
  toyota: "Corolla", 
  nissan: "Altima" 
}

japanase_cars[honda] # çalışmaz (NameError)
japanase_cars[:honda] # Accord değeri döner


