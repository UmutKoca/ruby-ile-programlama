# Döngüler 

Döngüler (Loops) biz akisi yönde komut verene kadar tekrarlayan yapılardır.

## Loop 

Break komutu ile duracağı yeri belirtene kadar sonsuza kadar aynı işlemi tekrar eden dönü tipidir.

Örneğin:

```ruby
i = 0
loop do
  puts "i is #{i}"
  i += 1
  break if i == 10
end
```

Yukarıdaki kod parçası i değeri 10 olarana kadar i değerini bir artırıp ekrana basar.

```
i is 0
i is 1
i is 2
i is 3
i is 4
i is 5
i is 6
i is 7
i is 8
i is 9
```
## While 

Loop'a benzer fakat nerede duracağını baştan söyleriz:

```ruby
i = 0
while i < 10 do
 puts "i is #{i}"
 i += 1
end

```

Çıktısı şu şekilde olur :

```
i is 0
i is 1
i is 2
i is 3
i is 4
i is 5
i is 6
i is 7
i is 8
i is 9
```

Biz "i'nin değeri 10'dan küçük olduğu sürece" dediğimiz için 9 a kadar çalıştı. 
Burada i+=1 yerine i + 1 gibi bir ifade kullanmış olsaydık bu döngü sonsuza kadar devam edecekti. += bu değere bir ekle ve kendisine ata anlamına geliyor. i + 1 ise değere 1 ekliyor fakat değerin kendisini değiştirmiyor.

Kullanıcı komut satırına "No" komutunu verene kadar kullanıcıya "Do you wanna play a game? " sorusunu soran bir program yazmak istersek:

```ruby
while gets.chomp != "No" do
  puts "Do you wanna play a game? "
end
```

Bu kod parçacığı ile kullanıcıdan No cevabı gelmediği sürece soruyu sormaya devam et demiş olduk.

# Until 

While döngüsünün tam tersidir.While şart koşulu true olduğu sürece devam ederken until koşul false olduğu sürece devam eder.

Örneğin:

```ruby
i = 0
until i >= 10 do
 puts "i is #{i}"
 i += 1
end
```
Yukarıdaki örnekte i 10 dan büyük ya da 10 a eşit olana kadar i değerini bir artırıyoruz. Çıktısı şu şekilde olur:

```
i is 0
i is 1
i is 2
i is 3
i is 4
i is 5
i is 6
i is 7
i is 8
i is 9
```

While ile yukarıda yaptığımız örneği şimdi de until ile yapalım:

```ruby 
until gets.chomp == "No" do
  puts "Do you wanna play a game? "
end
```

Bu kod parçacığı ile kullanıcıdan "No" cevabı gelene kadar soruyu sor demiş olduk.

## Ranges 

Peki ya eğer bir döngüyü kaç kere çalıştırmamız gerektiğini biliyor ve o kadar çalışmasını sağlamak istiyorsak ? 

İşte bu noktada devreye range yapısı giriyor.

Şöyle bir örnek yapalım:

```ruby

(1..5).to_a # [1, 2, 3, 4, 5] 
(1...5).to_a # [1, 2, 3, 4]
('a'..'e').to_a # ["a", "b", "c", "d", "e"]

```

## For 

Bir dizi ya da range'i döngüye sokmak istiyorsak for yapısı yardımımıza yetişiyor. 

Örneğin:

```ruby 
for i in 0..5
  puts "#{i} zombi geliyor !"
end
```

```
0 zombi geliyor !
1 zombi geliyor !
2 zombi geliyor !
3 zombi geliyor !
4 zombi geliyor !
5 zombi geliyor !
```

## Times 

Şu kadar kere yap dediğimiz döngü. Örneğin:

```ruby
5.times do
  puts "Merhaba dünya!"
end
```
```
Merhaba dünya!
Merhaba dünya!
Merhaba dünya!
Merhaba dünya!
Merhaba dünya!
```

```ruby 
5.times do |number|
  puts "Merhaba gakasi #{number}"
end
```
```
Merhaba galaksi 0
Merhaba galaksi 1
Merhaba galaksi 2
Merhaba galaksi 3
Merhaba galaksi 4
```

## Upto ve Downto  

Örnek:

```ruby
5.upto(10) {|num| print "#{num} " }     #=> 5 6 7 8 9 10

10.downto(5) {|num| print "#{num} " }   #=> 10 9 8 7 6 5
```