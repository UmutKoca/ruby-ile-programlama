# Diziler (Arrays)

Bir veri topluluğunu tek çatı altında toplayarak kolay ulaşılabilir hale getirdiğimiz yapılardır.

## Dizi oluşturma

``` ruby
num_array = [1, 2, 3, 4, 5]
str_array = ["This", "is", "a", "small", "array"]
```

Yukarıdaki örnekte num_array numeric tipte verilerin tutulduğu, str_array ise string tipinde verilerin bir arada tutulduğu dizilerdir.

Peki hem numeric hem de string tipinde verileri bir arada tutan bir dizi oluşturabilir miydik ? Evet. Örneğin aşağıdaki de bir dizi örneğidir:

```ruby
array = ['This',1,'is',2,'array',3] # ["This", 1, "is", 2, "array", 3]
```

Dizileri başka nasıl oluşturabiliriz ? 

```ruby
Array.new               #=> []
Array.new(3)            #=> [nil, nil, nil]
Array.new(3, 7)         #=> [7, 7, 7]
Array.new(3, true)      #=> [true, true, true]
```

Yukarıdaki örnekte Array.new(3,7) diyerek "3 elemanlı bir dizi oluştur ve her bir eleman 7 olsun" demiş olduk.

## Dizinin elemanlarına erişme

Dizilerde indeks adı verilen ve dizinin her bie elemanının pozisyonunu gösteren yapılar vardır. Dizilerin indexi 0 ile başlar.

Dizinin elemanlarına array[indeks] ile erişilir.

```ruby
str_array = ["This", "is", "a", "small", "array"]

str_array[0]            #=> "This"
str_array[1]            #=> "is"
str_array[4]            #=> "array"
str_array[-1]           #=> "array"
str_array[-2]           #=> "small"
```

Dizi indeksinin dışına çıkıldığında nil değer döner. Herhangi bir parametre verilmezse ArgumentError dönerç

```ruby 
str_array = ["This", "is", "a", "small", "array"]
str_array[30] # nil 
str_array[] # ArgumentError (wrong number of arguments (given 0, expected 1..2))
```
İki indeks parametresi verilerek dizinin istenen kısmı döndürülebilir:

```ruby
str_array = ["This", "is", "a", "small", "array"]
str_array[1,3]  # ["is", "a", "small"]
```

first ve last metotlarıyla dizinin baştan n. ve sondan n. elemanları alınabilir.

```ruby
str_array = ["This", "is", "a", "small", "array"]

str_array.first         #=> "This"
str_array.first(2)      #=> ["This", "is"]
str_array.last(2)       #=> ["small", "array"]
```

## Diziye eleman ekleme ve çıkarma

push metodu ve << operatörü verilen elemanı dizinin sonuna ekler ve dizinin yeni halini döndürür.

pop metodu dizinin son elemanını diziden çıkarır ve çıkarılan son elemanı döndürür.

```ruby
num_array = [1, 2]

num_array.push(3, 4)      #=> [1, 2, 3, 4]
num_array << 5            #=> [1, 2, 3, 4, 5]
num_array.pop             #=> 5
num_array                 #=> [1,2,3,4]
```

unshift metodu aldığı parametreyi dizinin başına ekler. 

shift dizinin ilk elemanını diziden çıkarır ve çıkarılan elemanı döndürür.


```ruby
num_array = [2, 3, 4]

num_array.unshift(1)      #=> [1, 2, 3, 4]
num_array.shift           #=> 1
num_array                 #=> [2,3,4]
```

pop ve shift metotları parametre alabilirler:

```ruby
num_array = [1, 2, 3, 4, 5, 6]

num_array.pop(3)          #=> [4, 5, 6]
num_array.shift(2)        #=> [1, 2]
num_array                 #=> [3]
```

## Dizileri birbirine ekleme ve çıkarma

Diziler + operatörü veya concat metodu ile birleştirilebilirler

```ruby
a = [1, 2, 3]
b = [3, 4, 5]

a + b         #=> [1, 2, 3, 3, 4, 5]
a.concat(b)   #=> [1, 2, 3, 3, 4, 5]
```

a.concat(b) ile b dizisi a dizisine eklenir ve a dizisi güncellenir. concat metodu ile a dizisi genişletildikten sonra a dizisini çağırırsanız [1,2,3,3,4,5] dizisi dönecektir.

Peki iki dizi birbirinden çıkarılabilir mi ?

```ruby
[1, 1, 1, 2, 2, 3, 4] - [1, 4]  #=> [2, 2, 3]
```

Evet. - operatörü ile ilk dizideki tüm 1 ve 4 elemanları diziden çıkarılmış oldu.

Ruby array manipulasyonu için 150 dan fazla metoda sahiptir.

```ruby
my_array = [1,2,3]

my_array.methods
```

Yukarıdaki komut ile array'imi manipule etmek için kullanabileceğim tüm metotları listeyebilirim.

İşe yarar birkaç metot:

```ruby
[].empty?               #=> true
[[]].empty?             #=> false
[1, 2].empty?           #=> false

[1, 2, 3].length        #=> 3

[1, 2, 3].reverse       #=> [3, 2, 1]

[1, 2, 3].include?(3)   #=> true
[1, 2, 3].include?("3") #=> false

[1, 2, 3].join          #=> "123"
[1, 2, 3].join("-") 
```

Tüm array metotlarına;

https://ruby-doc.org/core-2.7.1/Array.html

adresinden ulaşılaiblir.


