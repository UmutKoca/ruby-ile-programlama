# Veri Tipleri

Ruby nesne yönelimli bir programlama dilidir. Ruby'de hemen her şey (en temel veri tipleri bile) birer nesnedir.

Bu kısımda Ruby'nin basit veri tiplerini inceleyeceğiz. Bunlar :

- Numbers (integer, float)
- Strings
- Symbols 
- Booleans (true,false,nil)

## Numbers (Sayılar):

Aslında sayıların ne olduğunu biliyoruz. Ruby'de matematiksel işlemleri şu şekilde yapabiliriz:

```ruby
# Toplama
1 + 1   #=> 2

# Çıkarma
2 - 1   #=> 1

# Çarpma
2 * 2   #=> 4

# Bölme
10 / 5  #=> 2

# Üs alma
2 ** 2  #=> 4
3 ** 4  #=> 81

# Mod (Bölümden kalanı bulma )
8 % 2   #=> 0  (8 / 2 = 4; kalan sıfır)
10 % 4  #=> 2  (10 / 4 = 2 kalan 2)
```

## Integers and Floats (Tam Sayılar, Virgüllü Sayılar):

Ruby'de iki çeşit sayısal tip var. Integer tam sayıları (10, 5 gibi) float ise virgüllü sayıları (10,2 ; 9,6 gibi) ifade eder.

```ruby
17 / 5    #=> 3
17 / 5.0  #=> 3.4
```

## Sayı tiplerini birbirine dönüştürme:

```ruby
# integer bir değeri float tipine dönüştürelim:
13.to_f   #=> 13.0

# float bir değeri integera dönüştürelim:
13.0.to_i #=> 13
13.9.to_i #=> 13
```

## Bazı işe yarar metotlar:


### even?

Bir sayının çif olup olmadığını kontrol eder.

```ruby
2.even? #=> true
5.even? #=> false
```

### odd? 

Bir sayının tek olup olmadığını kontrol eder.

```ruby
2.odd? #=> false
5.odd? #=> true
```

## Strings (Karakter Dizisi):

Ruby'de karakter dizileri çift tırnak veya tek tırnak ile ifade edilebilir. İkisi de aynı işi görür. Fakat çift tırnak kullanımının bazı avantajları vardır. Bunu ilerleyen kısımlarda göreceğiz.

```ruby
"Hello World!"
'Hello World!'
```

### Concatenation(String yapıları birleştirme):

Ruby'de stringleri birleştirmenin birden fazla yolu var:

```ruby
# + operatörü ile 
"Welcome " + "to " + "Github!"    #=> "Welcome to Github!"

# << operatörü ile 
"Welcome " << "to " << "Github!"  #=> "Welcome to Github!"

# concat metodu ile 
"Welcome ".concat("to ").concat("Github!")  #=> "Welcome to Github!"
```

## Substrings 

String bir ifadenin içerisinden istediğimiz kısmı çekebiliriz. Örneğin : 

```ruby 
"hello"[0]      #=> "h"

"hello"[0..1]   #=> "he"

"hello"[0, 4]   #=> "hell"

"hello"[-1]     #=> "o"
```

## Escape Characters (Kaçış Dizileri)


Burada kaçış dizileri hakkında bilgi verilecek.


## Interpolation (Enterpolasyon)

Bir cümlenin içinde değişken kullanabilmemizi sağlar. Örneğin:

```ruby 
name = "Odin" # Burada name adlı bir değişken tuttuk ve bu değişkene Odin ismini atadık.

puts "Hello, #{name}" #=> "Hello, Odin"
puts 'Hello, #{name}' #=> "Hello, #{name}"
```
Yukarıdaki örnekten de anlaşılacağı üzere bu yapıyı kullanmak için çift tırnak kullanmak gerekir.

## Sık Kullanılan String Metotları

### capitalize
### include? 
### upcase 
### downcase 
### empty?
### length 
### reverse 
### split 
### strip 

## Objeleri Stringe Çevirme:

to_s metodu ile hemen hemen her şey stringe çevrilebilir. Örneğin:

```ruby
5.to_s        #=> "5"

nil.to_s      #=> ""

:symbol.to_s  #=> "symbol"
```

## Symbols (Semboller):

Bu konuyu anlamadan önce Ruby'de bulunan object_id metoduna bakalım.

Ruby'de hemen her şey birer nesnedir ve her nesnenin dışarıya açık (public) metotları vardır. object_id metodu da bunlardan biri. 

Her nesneye var olduğu sürece değişmeyen hafızada depolandığı yerin adresini veren kendine has bir sayı veriliyor. object_id metodu da bu değeri döndürüyor.

Örneğin:

```ruby
number = 23
number.object_id # 47
users = {"carl": [1,2,3], "paul": [3,4,5]}
users.object_id # 70342844770580
numbers = (0..10).to_a
numbers.object_id  # 70342856985540
person = Person.new("person1")
person.object_id  # 70342819709960
```

Şimdi name1 ve name2 adlı iki string değişken oluşturup bunların hafızadaki adreslerine bakalım:

```ruby 
name1 = "Emre"
name2 = "Emre"
```

name1 ve name2 değişkenlerimin ikisi de "Emre" şeklinde bir string tutuyor. Bakalım bunların hafızadaki adresleri neymiş:

```ruby 
name1.object_id # 47409220393720
name2.object_id # 47409220365740
name1.object_id == name2.objectid # false 
```

name1 ve name2 değişkenlerimin her ikisi de "Emre" olmasına rağmen bu iki değişkenin hafızadaki adresleri birbirinden farklı.

Peki string yerine symbol kullansak ne olacaktı ? Aynı örneği bir de bu şekilde deneyelim:

```ruby
name1 = :Emre
name2 = :Emre

puts name1 # Emre
puts name2 # Emre

name1.object_id # 1281503
name2.object_id # 1281508

name1.object_id == name2.object_id # true
```

Bu sefer "Emre" değişkenini string değil symbol olarak tuttuk ve hafızadaki adreslerinin aynı olduğunu gördük.

Symboller daha çok hash yapıları içerisinde kullanılıyor. Hafızada kapladığı yer ve performans olarak string yapısının yerine tercih ediliyor.

## True, False ve Nil 

True ve False Boolean veri tipi olarak geçer ve adlarından da anlaşılabileceği üzere True doğru, False yanlış durumları temsil eder.

Nil ise "hiçbir şey" i temsil eder. Ruby'de her şey her zaman bir değer döner. Eğer bir kod hiçbir şey döndürmüyorsa Nil değeri döner.






