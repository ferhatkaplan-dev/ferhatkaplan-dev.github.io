---
title: "C#'ta Nesne Tabanlı Programlamanın Temelleri: Sınıflar, Nesneler ve Özellikler"
date: 2024-07-29 01:30:00 +0300
categories: [programing, c#]
tags: [csharp,oop, c#, nesne tabanlı programlama, this keyword ]
description: "C# ile nesne tabanlı programlamaya giriş yapın! Bu makalede, C# dilinde sınıflar, nesneler, auto property'ler, shallow ve deep copy kavramları ile indexer ve property'lerin nasıl kullanılacağını öğrenin. Ayrıca, 'this' anahtar kelimesinin kullanımı ve sınıf açıklamaları hakkında detaylı bilgi edinin. Yazılım ve teknoloji konularında bilgi edinmek için ideal bir kaynak."
image:
  path: assets/img/post_images/2024-07-29-csharp-nesne-tabanli-programlamanin-temelleri-preview.webp
  lqip: assets/img/post_images/2024-07-29-csharp-nesne-tabanli-programlamanin-temelleri-preview.avif
  alt: c# OOP preview resim
---



Nesne tabanlı programlama birçok dilde kullanılmaktadır. Nesne tabanlı programlama bir kod yazma tekniği veya yaklaşımıdır diyebiliriz. Hayatımızda kullandığımız nesneleri kod halinde yazıp simüle etmemizi sağlayan bir tekniktir. Örnek olarak kitap nesnesini verebiliriz. Gerçek hayatta olduğu gibi kitabın adı, türü, sayfa sayısı, baskı numarası vs. bulunur, bu özelliklere sahip kitap adında bir nesne oluştururuz. Bu nesne tabanlı programlamanın temel mantığıdır. “Herşey bir nesnedir” mantığı bulunmaktadır, yani kitaplar, arabalar, kişiler, ağaçlar vb. bir nesnedir.

OOP’de en küçük parçaya nesne denir. Nesnelerin içinde veri tutulan alanlar bulunmaktadır ve bu alanlara field adı verilir. Nesneler sınıflardan türetilir, yani sınıflara nesne kalıpları diyebiliriz ve bu kalıplardan istediğimiz kadar nesne oluşturabiliriz. Örnek olarak araba nesnesini verelim. Araba adında bir class oluşturup bütün arabalardaki ortak özellikleri (rengi, kapı sayısı, motor gücü, motor türü vb.) bu class’ın içinde tanımlarız daha sonra nesne oluşturacağımız zaman bu class’dan nesneyi türetiriz. Nesneler referans türü yapılardır.

## C#'ta Sınıfların ve Nesnelerin Tanımlanması

Nesne tabanlı programlamada bir nesneyi tanımlayabilmemiz için o nesnenin bir kalıbının tanımlı olması gerekir, işte tam bu noktada class yapısı kullanılır. Çünkü class içerisinde Field(alan), Property(özellik) ve kapsülleme yapılarını, metotlar vb. yapıları tanımlayabiliyoruz. BUnlar programlamanın temel yapılarıdır.
**Arabalar** isminde bir sınıfımızın olduğunu var sayalım ve bu sınıftan **araba** isminde bir nesne tanımlayalım. Bu durunda **araba**, **Arabalar** sınıfının bir nesnesi ve **araba**, **Arabalar** tipinde bir değişken olur.
Bir nesneyi tanımlamak için new operatörünü kullanırız.
`SınıfAdı sınıfDeğişkeni = new SınıfAdı();` şeklinde sınıftan nesne oluştururuz. Burada **SınıfAdı** bir referans türüdür ve **sınıfDeğişkeni** bu türden üretilmiş bir nesnedir.

```c#
class Program
{
    static void Main(string[] args)
    {
        Arabalar araba = new Arabalar();
        araba.renk = "Kırımız";
        araba.model = "Şahin";
        araba.kapıSayısı = 4;
        araba.OzellikYaz();
            
    }

}

class Arabalar
{
    public string renk;
    public string model;
    public int kapıSayısı;
        
    public void OzellikYaz()
    {
        Console.WriteLine($"renk {renk}, model {model}, kapıs sayısı {kapıSayısı}");
    }
}
```

Yukarıda `Arabalar araba = new Arabalar();` ile Araba sınıfına ait, **araba** isminde bir nesne tanımladık. Bu nesne Arabalar sınıfına ait renk, model, kapısayısı özellikleri ve OzellikYaz metodunu kullanabilmektedir.

Classlar 3 farklı yerde oluşabilir. Bunlar namespace içinde, namespace dışında ve class içerisinde(nested type) oluşturulabilir. Ama aynı isimde birden fazla class tanımlanamaz.

- **namespace içinde:** Buradaki sınıflar aralarında namespace adı belirtmeden sadece sınıf adı ile iletişim kurabilir. Namespace dışında erişim sağlamak için namaspace ismi belirtmek gerekir.

- **namespace dışında:** Bu sınıfa namespace ismi belirmeden her yerden erişim sağlayabiliriz.

- **class içinde(nested type):** Class içinde tanımlanan classlar sınıf elemanı değildir. Diyelim ki class1 sınıfının içine class2 sınıfı tanımlı olsun. class2 sınıfından nesne oluşturmak için `class1.class2 nesneIsmi = new class1.class2();` şeklinde bir yapı kullanmalıyız.

## C#'ta Sınıfların ve Elemanlarına Açıklama Ekleme

Bir elemana açıklama eklemek için hemen üst satırını:

```c#
/// <summary>
/// Açıklama
/// </summary>
```

şeklinde bir yapı ile açıklama ekleyebilirsiniz.

```c#
/// <summary>
/// Bu bir öğrenci clasıdır.
/// </summary>
class Ogrenci
{
    /// <summary>
    /// Bu bir indexer'dır.
    /// </summary>
    /// <param name="x"> x parametresi </param>
    public int this[int x]
    {
        get
        {
            return x;
        }
        set
        {
            x = value;
        }
    }
        
    /// <summary>
    /// Bu bir Merhaba yazan bir metoddur.
    /// </summary>
    public void MerhabaYaz()
    {
        Console.WriteLine("Merhaba");
    }
}
```

Bu açıklama satırları yazdığımız kodun daha sonra rahat anlaşılmasını, yada başka biri okuduğunda rahat anlayabilmesini sağlamak için kullanılan yapılardır.

## Nesne Kavramı​
Nesneye bir veri bütünü diyebiliriz. Mesela bir pervaneyi nesne olarak düşünelim. Bu nesnenin verileri yani özellikleri; kaç volt olduğu, kaç pervanesi olduğu, dönme hızı, yapıldığı malzeme vb. bunlar nesnenin özellikleridir. Bir nesne örneği daha verelim. Bu nesne öğrenci olsun. Öğrenci nesnesinin elemanları; Adı, soyadı, sınıfı, numarası, cinsiyeti vb. dir. Ama bu elemanlara öğrencini saatinin rengi örneğini veremeyiz, çünkü her öğrencinin saati olmak zorunda değildir. Kısaca bir nesneyi tanımlarken nesnenin özelliklerini ortak şekilde belirlemeliyiz. Bir nesneyi oluşturmak için new operatörünü kullanılır. `new nesnetipi()` şeklinde kullanılır. Bu işlemi yaparak ramdaki heap bölgesinde bir nesne tanımladık. Peki bu nesne nasıl erişim sağlayacağız? İşte tam bunun için stack bölgesinde aynı tipte referans türü bir değişken oluşturup atama işlemi gerçekleştiriyoruz. Bu işlem `nesneTipi değişkenAdı = new NesneTipi();` şeklinde tanımlanır. Burada = operatörü referans türü değerlerde kullanıldığı için atama operatörü depil , işaret etme , referans etme operatörü olarak adlandırılır.

## Target_Typed New Expressions​

Nesne oluştururken referans direk atanıyor ise C# hangi nesne tipinin oluşturacağını anlamaktadır. Yani `NesneTipi nesneAdı = new NesneTipi()` yerine `NesnteTipi NesneAdı = new()` şeklindede nesne tanımlayabiliriz. Bu özelliği kullanabilmek için en az .Net 5.0'ı kullanmalıyız.

## Referans​

Referans ram’ın stack bölgesinde tanımlanıp, heap bölgesindeki nesneleri işaret eden bir tipdir.
Örnek olarak SınıfIsmi nesneAdı = new SınıfIsmi(); şeklinde referans tipi olan bir nesne oluşumunu örnek verelim. Burada SınıfIsmi nesneAdı kodu ile stack bölgesinde nesneAdı isminde bir referans noktası oluşturduk, new SınıfIsmi kodu ile ise heap bölgesinde SınıfIsmi cinsinde bir nesne oluşturduk. = ile stack bölgesindeki değişkeni, heap bölgesindeki nesneye işaretliyor, referans ediyor.

## Shallow copy​

Kısaca bir nesneyi birden fazla referansın işaretlemesidir.

```c#
class Program
{
    static void Main(string[] args)
    {
        Myclass m1 = new Myclass();
        Myclass m2 = m1;
    }
}

class Myclass
{

}
```
Burada bir nesne tanımlıyoruz ve m1 ile referans gösteriyoruz. Daha sonra `Myclass m2 = m1;` m1'in gösterdiği aynı nesneyi m2 ile referans gösteriyoruz. Yani ortada 1 adet nesne bulunmakta ve o nesneyi referans gösteren 2 adet değişken bulunmakta. Bunlardan birinde bir değişiklik olduğunda aynı nesneyi referans gösterdiğinden dolayı diğer nesnede de aynı değişiklik oluşur. Bu olaya shallow copy denir.

## Field(alan)​
Nesne içinde veriyi sakladığımız alandır. Sadece class içinde tanımlanır ve herhangi bir türden olabilir. Class içerisine tanımlanan field’lara değer atamazsak varsayılan değer otomatik olarak atanır.

## Property​

Property temelde bir metoddur. Ama metoddan farkı herhangi bir parametre almaması ve içinde 2 adet blok bulunmaktadır, bunlar get ve set bloklarıdır. Property’den bir değer alındığında get bloğu çalışır, bir değer atandığında ise set bloğu çalışır. Nesnelerin içerisindeki field’lara erişimi kontrol etmek amacı ile kullanılır. Hem veri erişiminde hem de verileri dışarıya paylaşmada kontrol sağlamak istediğimizde bu yapıyı kullanılır. Bu kontrol mekanizmasına Encapsulation(Kapsülleme) denir.

## Full Property​

En sade property yapısıdır. İçerisinde get ve set blokları tanımlanmalıdır.

```c#
ErişimBelirleyici GeriDÖnüşTürü PropertyAdı
{
    get{Property'den veri istendiğinde tetiklenir.}
    set{Property'e veri gönderildiğinde tetiklenir ve gönderilen veriyi value keywordü ile yakalar.}
{
```
Temelde property yapısı yukarıdaki gibidir. Full property’lerde set bloğu tanımlanmaz ise sadece okunabilir, get bloğu tanımlanmaz ise sadece yazılabilir olurlar.

```c#
class Program
{
    static void Main(string[] args)
    {
        Arabalar araba = new Arabalar();
        // Burada set bloğu tetiklenmektedir.
        araba.Renk = "Kırmızı";
        
        // Burada ise get bloğu tetiklenmektedir.
        Console.ReadLine(araba.Renk);
    }
}

class Arabalar
{
    private string renk;
    public string Renk
    {
        get
        {
            return renk;
        }
        set
        {
            renk = value;
        }
    }
}
```

Yukarıda property yapısına bir örnek verdik. Property ismi büyük harfle başlamalıdır, bu zorunlu bir kural değildir ama genel olarak bu şekilde kullanılır. get bloğunun içinde return keywordü tanımlanması zorunludur, çünkü geriye döndürülecek bir değer beklenmektedir. set bloğunda ise value keywordü gönderilen değeri yakalamaktadır. Yani `araba.Renk = "Kırmızı";` ile set bloğu tetiklenmekte ve value keywordü "Kırmızı" değerini yakalamaktadır, ardından değeri renk field'ine atamaktadır. `Console.ReadLine(araba.Renk);` ile ise get bloğu tetiklenmekte renk field değeri return keywordü ile dışarı aktarılmaktadır.

## Prop Property​

Bir property encapsulation yapsa dahi temsil ettiği field’daki veriyi herhangi bir müdahale etmeden hem erişimi hem de veri atanmasını gerçekleştiriyorsa bu property türüne prop property denir.
Bu normal kullanım:

```c#
class Ogrenci
{
    private string ismi;

    public string Ismi
    {
        get
        {
            return ismi;
        }
        set
        {
            ismi = value;
        }
    }
}
```
Buda prop kullanımdır:

```c#
class Program
{
    static void Main(string[] args)
    {
        Ogrenci ogrnci = new Ogrenci();

        ogrnci.İsim = "Osman";
        Console.WriteLine(ogrnci.İsim);
    }
}

class Ogrenci
{

    public string İsim { get; set; }
}
```

Prop kullanıldığında field tanımlamamıza gerek yoktur. Çünkü field otomatik olarak tanımlanır.

## Auto Property İnitializers​

Bir property’nin ilk değerini nesne ayağa kalkar kalkmaz tanımladığımız bir yapıdır.

```c#
class Ogrenci
{

    public string İsim { get; set; } = "Osman";
}
```

## Ref readonly Returns​

Bu yapı bir sınıf içerisindeki field değerini referansıyla döndürmemizi sağlayan ve bir yandan da bu değişkeni read only(sadece okunabilir) yapar.

```c#
class Ogrenci
{
    private string isim = "Osman";
    public ref readonly string Isim => ref isim;
}
```
## Computed(Hesaplanmış) Properties​

İçerisinde türetilmiş bir bağıntı taşıyan propery’lerdir. Get veya set’in içerisinde farklı aritmetik işlemler yapmamızı sağlayan bir yapıdır.

## Expression-Bodied Property​

Lambda Expression kullanıldığı bir property yapısıdır. Auto Property Initializers yapısına benzer. Sadece readonly yapılarda kullanılır.

```c#
class Ogrenci
{
    public string Isim => "Osman";
}
```

## Propertylere İlk Değer Verme​

```c#
class Program
{
    static void Main(string[] args)
    {
        Ogrenci og = new Ogrenci()
        {
            Myproperty1 = 10,
            Myproperty2 = 20,
            Myproperty3 = 30
        };
            
    }
}

class Ogrenci
{
    public int Myproperty1 { get; set; }
    public int Myproperty2 { get; set; }
    public int Myproperty3 { get; set; }
}
```
Şeklinde yada

```c#
class Program
{
    static void Main(string[] args)
    {
        Ogrenci og = new Ogrenci();
        og.Myproperty1 = 10;
        og.Myproperty2 = 20;
        og.Myproperty3 = 30;

    }
}

class Ogrenci
{
    public int Myproperty1 { get; set; }
    public int Myproperty2 { get; set; }
    public int Myproperty3 { get; set; }
}
```
Şeklinde property’e ilk değerini verebiliriz.

## Indexer​

Nesneye indexer özelliği kazandıran, property ile aynı özelliklere sahip olan bir yağıdır.

```c#
erişimBelirleyicisi geriDönüşDeğeri this[]
{
    get{    }
    set{    }
}
```
```c#
class Program
{
    static void Main(string[] args)
    {
        Ogrenci ogrnci = new Ogrenci();
        ogrnci[1] = 2;
        ogrnci[2] = 4;

        Console.WriteLine(ogrnci[1]);
        Console.WriteLine(ogrnci[2]);
    }
}

class Ogrenci
{
    public int this[int x]
    {
        get
        {
            return x;
        }
        set
        {
            x = value;
        }
    }
}
```

## This Keyword​

This keywordü 3 farklı amaç ile kullanılır. Bunlar; Sınıf nesnesini temsil etme, Aynı isimden field ile metod parametrelerini ayırmak için, Bir Constructer’dan başka bir constructer’ı çağırmak için kullanılır.

```c#
class Ogrenci
{
    public void Yaz()
    {
        this.MerhabaYaz();
    }
    public void MerhabaYaz()
    {
        Console.WriteLine("Merhaba");
    }
}
```
Burada this keywordü class’dan üretilmiş nesneyi temsil eder.

```c#
class Ogrenci
{
    public string yazı = "Merhaba";
    
    public void EkranaYAz(string yazı)
    {
        Console.WriteLine(this.yazı);
    }
}
```
Burada ise this keywordü aynı isimlerde olan yazı fieldi ile metod içerisindeki yazı parametresini birbirinden ayırdı. Yani kodda field olan yazı değerini kullandı.
