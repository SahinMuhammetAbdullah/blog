---
title: "Ruby Part 2"
description: "Ruby Programlamanın Temelleri"
date: 2024-08-28 21:30:20 +0530
author: <masahin>
categories:
  - Programlama Dilleri Giriş Seviye
  - Ruby
tags:
  - Ruby
  - Programlama
published: true
media_subpath: /assets/
image:
  path: images/ruby-part-2/ruby-giris-banner.png
---

## Temel Objeler ve Veri Yapıları

Bu bölümde sizlere Ruby'de bulunan temel objelerden ve veri yapılarından bahsedeceğim.

Öncelikle genel olarak başlılar şeklinde inceleyelim;

- puts Metodu
- print Metodu
- p Metodu
- Basit Aritmatik İşlemler
- Yorum Satırları
- Değişkenler
- Sabitler
- String Interpolation
- Nesne ve Class Metodları
- Veri tipi Değiştirme
- Kullanıcıdan Veri Alma
- Boolean Veri Tipi

## puts Metodu

`puts` terminal üzerinden kendisine verilen verileri yazdırarak bize dönüş sağlayan metoddur. Bir örnekle incelemek gerekirse:

```ruby
puts "Bu bir örnektir."
puts
puts "Bu gün alış veriş'e çıktım."

puts 2024

puts 4 + 5
puts "4 + 5"
puts "4" + 5
puts "4" + "5"
```

Bu kodları sırasıyla açıklayalım ve çıktılarını inceleyelim:

1. puts terminalde `Bu bir örnektir.` çıktısı verecek ve alt satıra geçecektir.
2. puts ise bir boşluk dönerek alt satıra geçecek.
3. puts `Bu gün alış veriş'e çıktım.` çıktısı verecek ve alt satıra geçecektir.
4.  puts ise `2024` değerini dönerek alt satıra geçecektir.
5.  puts yer alan toplama işlemini gerçekleştirip `9` değeri döndür ve alt satıra geçer.
6.  puts `4 + 5` çıktısı verecek ve alt satıra geçecektir.
7.  puts asıl değinmek istediklerimden biride bu ki burada hata ile karşılaşmaktayız. Bu hata `no implicit conversion of Integer into String (TypeError)` olacaktır. Yani bir yazı(sitring) ile tam sayı(integer) değer toplanamaz çünkü dönüşüm yapamıyor.
8.  puts da değinmek istediklerimden ama burada 7. puts da karşılaştığımız sorun nedeniyle uygulama çalışmayacaktır o yüzde `puts "4" + 5` satırını dosyamızdan silerek yeniden çalıştıralım. Göreceğiniz sonuç `45` olacak yani 4 ve 5 yazı değerlerini yan yana çıktı vemiş olacktır.

Bura da değinmek istediğim bir konu var ki oda her maddede belirtiğim **`alt satıra geçer`** ifadesi. Buradan şunu fark ediriz `puts` içerisinde yer alan değeri döndğükten sonra popüler bazı dilerden(Örneğin C vb.) farklı olark kaçış karekterlerine ihtiyaç duymadan alt satıra geçebilmektedir.

### Kaçış Karakterleri
Kaçış karakterlerine değinmişken açıklamak isterim:
1. `"\n"`: Bu kaçış karakteri "..." olarak gelen bir ifadenin sonuna konursa alt satıra geç emri vericek ve peşine gelecek olan ifadeler bir alt satyırdan itibaren gelmeye başlayacaktır.
2. `"\r"`: Bu kaçış karakteri "..." olarak gelen bir ifadenin içerisinde kullanıldığı yerde yeni bir satır başuı oluşturur.
3. `"\t"`: Bu kaçış karakteri "..." olarak gelen ifade içirisinde kullanıldığı yerde tab boşluğu oluşturur.

Temel kaçış karakterlerinde bazıları burada yer almaktadır. Diğer kaçış karakterlerini incelemekl isterseniz [buradan](https://vigo.github.io/ruby101-kitap/bolum-04/03-string/) inceleyebilirsiniz.

Bu anlatımdan sonra şunu anlayabiliriz: `puts` `\n` kaçış karaktyeri içermektedir
## print Metodu

`print` terminal üzerinden kendisine verilen verileri yazdırarak bize dönüş sağlayan metoddur. Bir örnekle incelemek gerekirse:

```ruby
print "merhaba "
print "dünya"
```

Eğer bu kodun çıktısını incelerseniz sonuç `merhaba dünya` şeklinde olacaktır. Buradan anlayacağımız üzere `print` metodu `puts` metodundan farklı olrak `\n` kaçış karakterini içermez.

## p Metodu

`print` terminal üzerinden kendisine verilen verileri yazdırarak bize dönüş sağlayan metoddur. Bir örnekle incelemek gerekirse:

```ruby
p "merhaba dünya"
p "merhaba 
dünya"
```

şeklinde iki çıktı görmek istersek ilk `p` metodunun çıktısı `"merhaba dünya"` şeklinde olacak iken ikinci `p` metodunda `"merhaba \ndünya"` şeklinde görüntülemiş oluruz.

Burada şu çıkarıma varırız; `p` metodu içeriğine gelen ifadeleri oldu gibi dönüş verir. Böylelikle bizlerde ikinci `p` motodunun çıktısında gördüğümüz `\n` kaçış karakteri ve her ikisinde de olan `""` işaretini gözlemlemiş olduk.
`p` metodu ile ilgili şunuda söyleyebiliriz **`\n` kaçış karakterini içerir**

## Basit Aritmatik İşlemler

Burada aritmetik işlemleri göreceğiz. Örnekler üzerinden gidelim:

```ruby
puts 4 + 5
puts 7 - 4
puts 2 * 7
puts 8 / 2
puts 11 / 2
puts 11.0 / 2
puts 11 / 2.0
puts 11.0 / 2.0

puts 2 * 2 * 2 * 2 * 2
puts 2 ** 5
puts 6 ** 2

puts 4 % 3
puts 5 % 2
puts 6 % 3
```

Çıktı:

```text
9
3
14
4
5
5.5
5.5
5.5
32
32
36
1
1
0
```

Yukarıdaki çıktılar üzerinden değerlendirmelerimiz yapalım. Sizlerinde gördüğü üzere toplama çıkarma ve çarpma işlemlerinde her şey olması gerektiği gibiyken bölme işleminde `11 / 2 = 5,5` gibi bir değer görmemiz gerekirdi ama burada karşımıza veri tipleri devreye girmekte. Kısaca sayıların veri tiplerine değinelim

- Integer **Tam Sayı** Veri Tipi

Tam sayıları tutan bir veri tipidir. Eğer bir integer değişken oluşturmak istersek `sayi = 10` olarak tanımlamazı yetelidir. Ruby bunu integer değer olarak algılayacaktır.

- Float **Ondalıklı Sayı** Veri Tipi

Ondalıklı sayıları turan bir veri tipidir. Eğer bir float değişkeni oluşturmak istersek `pi = 3.14` olarak tanımlamamız yeterlidir. Ruby bunu float olarak değer olarak algılayacaktır.

Sonuç olarak Ruby'de `11 / 2` işleminin sonucunu `5,5` olarak olarak görmek istersek her hangi bir tarafta ve ya her iki tarafta sayının ondalıklı olduğunu ifade etmemiz gerekir. Bunun ifade edebilmek için ise örneğin `11.0` gibi bunu belirmeliyiz.

Ruby'de `**` aritmetik işlemi üstel almayi ifade eder. Üstel bir işlem gerçekleştirecek isek bunu `2 ** 5` şeklinde ifade edebilmekteyiz.

Ruby'de `%` operatörü ile aritmatik işlemler yaptığımızda şunu ifade ederiz; `5 % 2` bunun değeri 5'in 2'ye bölümünden kalan değeri döndürmek anlamına gelmektedir. Örneğimizde yer alan ifade `5 % 2 = 1` alacaktır. 5, 2'ye tam bölünmez ve kalan ise 1 olur bu şekilde bizler dönüş değerini 1 olara görmnekteyiz.

## Yorum Satırları

Ruby'de yorum satırları `#` ile oluşturulur. Örnekler üzerinden incelemek gerekirse:

```ruby
puts "Yorum satırı 1"
# puts "Yorum Satırı 2"
pust "Yorum satırı 3"
```

Çıktı:

```text
Yorum satırı 1
Yorum satırı 3
```

Çıktılarda da görebileceğimiz üzere `# puts "Yorum Satırı 2"` ifadesi yorumlayacı tarafından işlem görmez ve herhangi bir dönüş vermez yani terminalde `Yorum Satırı 2` ifadesini göremeyiz.

Yorum satrıları aslında çok önemlidir. Çalıştığınız projelerde yazdığınız kodlarınızda yorum satırları da yazarak, tekrar kodlara döndüğünüzde sizlere ve sizle beraber çalışacak ekip arkadaşlarınıza  yapmış olduğunuz fonksiyonların, classların hangi amaca hizmet ettiği hakkında bilgi sahabi olması adına önem arzeder.

## Değişkenler

Ruby'de değişken tanımı yapılışını örnekler üzerinden inceleyelim:

```ruby
isim = "bilişim diyarı"
yas = 15
fiyat = 198.99

puts isim
puts yas + 15
puts fiyat * 3
```

Çıktı:

```text
bilişim diyarı
30
596.97
```

Çıktılarda görüldüğü üzere değişkenlere tip belirtmesek de Ruby' bınları yorumlayıp değişkenin hangi veri tipinde olduğunu algılayabilmekte. Bunu anladığının göstergesi ise `yas + 15` sonucunun **30** `fiyat * 3` ise **596.97** olarak dönmeleri tamsayıların ve ondalıklı sayıların dönen değerlerini olması gerektiği gibi dönürmesinden anlaşılmaktadır.

Değişkenler `degiskenIsmi = deger` şeklinde olmalıdır.

Deüişkenleri paralel olarak da ataya biliriz:

```ruby
a, b, c = 5, "merhaba", 6.8
puts a, b, c
```

Çikti:
```text
5
merhaba
6.8
```

Çıktıda da görüleceği üzere değişkenlerimizi paralel bir şekilde de ataya biliriz ama bunu yapmak ilerleyen süreçlerde risk barındırabilir yani beklenmedik hatalarla karşılaşabiliriz. Bu yüzde bu şekilde atama yapmanızı tavsiye etmem

## Sabirler

Ruby'de sabit değişkenler oluşturabilmekteyiz. Örneğin **pi** sayısını üzerinden gidecek olursak:

```ruby
PI = 3.14
puts PI

PI = 4
puts PI
```

Şeklinde işlemler yapacak olursak `PI = 3.14` şeklinde atadığımız değer bir sabit olur. Sabitler **BÜYÜK** harflerle ifade edilirler. Sabitler değiştirilemez niteliğe sahiptir bu yüzde `PI = 4` ifadesine geldiği zaman kod hata verecektir.


## String Interpolation

String Interpolation ifade etmek gerekirse oluşturduğumuz `isim = "Bilişim Diyarı"` değişkenimizi başka bir değişkende yer almasını sağlamaktır. Örneğin:

```ruby
isim = "Bilişim Diyarı"

puts "Hoşgeldin #{isim}, seni aramızda görmek ne kadar hoş!"

yas = 25

cevap = "Adım #{isim}, yaşım #{yas}"

puts cevap
```

Çıktı:

```ruby
Hoşgeldin Bilişim Diyarı, seni aramızda görmek ne kadar hoş!
Adım Bilişim Diyarı, yaşım 25
```

Çıktılarda da görüldüğü üzere farklı yerlerde tanımladığımız değerleri başka değerler dizilerinde kullanabilmek için `#{...}` yapısını kullanmaktayız. Bu şekilde isim değişkenimiz `puts "Hoşgeldin #{isim}, seni aramızda görmek ne kadar hoş!"` burada kullanıldığında çıktı bize `Hoşgeldin Bilişim Diyarı, seni aramızda görmek ne kadar hoş!` bu şekilde dönmüştür.

## Nesne ve Class Metodları

Bu bölümde sizlere neselerde ve classlarda var olan hazır metotların bazılarından bahsedeceğim. Örneklerimiz üzerinden devam edelim:

```ruby
puts "Merhaba Dünya".length #uzunluk metodu (karakter sayısını verir)
puts "Merhaba Dünya".upcase #harfleri büyütür
puts "Merhaba Dünya".downcase #harfleri küçülütr

isim = "Bilişim Diyarı"

puts isim.length
puts isim.upcase
puts isim.downcase

puts isim.upcase.downcase


puts 5.next
puts "a".next

puts

puts "Merhaba Dünya".class
puts 5.class
puts 6.25.class
```

Çıktı:

```text
13
MERHABA DÜNYA
merhaba dünya
14
ABDULLAH ŞAHIN
abdullah şahin
abdullah şahin
6
b

String
Integer
Float
```

Sırasıyla `length` metodumuz bizlere karakter sayısını vermektedir, `upcase` karakterleri büyük harflere dönüştürür, `downcase` ise karakterleri küçük harflere dönüştürür, `next` bir sonraki değere bizi götürür, `class` ise o değişkenin sınıfı bize döner.

## Veri tipi Değiştirme

Değişkenlerin veri tipini değiştirmek için `to_X` yapısını kullanırız. Burada "X" değerinin yerine `s` (string), `i` (integer), `f` (float) karakterlerini koyarak tip dönüşümü gerçekleştiriz. Örneklerimizi inceleyecek olursak:

```ruby
ornek = "3"
p ornek.class

p ornek.to_i.class

p ornek.to_f.class

sayi = 5
p sayi.to_s

p sayi.to_f

kusurlu_sayu = 3.89

p kusurlu_sayu.to_s

p kusurlu_sayu.to_i
```

Çıktı:

```text
String
Integer
Float
"5"
5.0
"3.89"
3
```

Bu çıktılardan anlaşılacağı üzere küsüratlı bir sayayı tam sayı tip dönüşümü uyguladığımızad bizlere sayının yuvarlanmış biçimini değil, olndalıklı kısmının değerden direkt çıkartarak döndürdüğünü görürüz.

## Kullanıcıdan Veri Alma

Kullanıcıdan veri almak için `gets` kullanırız. Bir örnekle destekleyelim:

```ruby
puts "Merhaba, isminiz nedir?"
isim = gets.chomp 
puts "Hoşgeldin #{isim}, yaşınız kaç?"
yas = gets.chomp.to_i
puts "Yaşınız #{yas}"
```

Çıktı:

```text
Merhaba, isminiz nedir?
Bilişim Diyarı
Hoşgeldin Bilişim Diyarı, yaşınız kaç?
25
Yaşınız 25
```

Burada gets kullanıcıdan veriyi alırken alınan veride `\n` kaçış karekteri ile beraber gelir. Bundan kurtulmak için ise `.chomp` kullanırız.

Eğer `.chomp` kullanmamış olsak çıktımız:

```text
Merhaba, isminiz nedir?
Bilişim Diyarı
Hoşgeldin Bilişim Diyarı
, yaşınız kaç?
```

Şeklinde gözükerek düzenli bir sonuç dönmemiş olacaktı.

## Boolean Veri Tipi

Boolean veri tipi sınıf'ın true ve ya false değeri ile oluşur. Bunu bir örnekle pekiştirelim:

```ruby
puts 2 < 5
puts 5 > 10

puts true.class
puts false.class

mezun = true
emekli = false

puts

puts mezun
puts emekli
```

Çıktı:

```text
true
false
TrueClass
FalseClass

true
false
```

Çıktılarımızda göründüğü üzere `2 < 5` karşılaştırmasının cevabı `true` dönerken, `2 > 5` ise `false` olmaktadır. Değişkenlere bunları değerleri atadığımızda da Ruby bunu yorumlayarak boolean olarak algılar ve sınıfını `.class` olarak sorguladığımızda `TrueClass` ve ya `FalseClass` olarak döndüğünü görürüz.

Bu noktada bir ara verelim. Gelecek yazıları takipte kalın👋