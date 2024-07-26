---
title: "JavaScript Spread Operator: Temel Kullanım ve Avantajları"
date: 2024-07-26 03:30:00 +0300
categories: [programing, javascript]
tags: [javascript, spread operator, es6]
description: "JavaScript spread operator nedir ve nasıl kullanılır? Dizileri ve objeleri daha verimli bir şekilde manipüle etmek için spread operator’ün avantajlarını, temel kullanım örneklerini ve uygulama alanlarını öğrenin. Kodunuzu daha temiz ve okunabilir hale getirin"
image:
  path: assets/img/post_images/2024-07-26-javascript-spread-operator-temek-kullanim-ve avantajlari-preview.webp
  lqip: assets/img/post_images/2024-07-26-javascript-spread-operator-temek-kullanim-ve avantajlari-preview-low.avif
  alt: Spread operator nedir yazan bir görsel.
---


## Spread Operator Nedir?

JavaScript'te spread Operator, **ES6 (ECMAScript 2015)** ile hayatımıza giren ve dizileri ve objeleri kolay bir şekilde manipüle etmek için kullandığımız güçlü bir yapıdır.

Spread operator, `(…)` ile gösterilir ve iterasyon yapılabilir bir dizi veya nesnenin içindeki değerleri ayırarak başka bir dizi veya nesne içinde kullanmayı veya fonksiyona parametre olarak vermek için kullanılan bir JavaScript operatörüdür.

Yani kısaca, **spread** operator, iterasyon edilebilir bir obje veya dizinin içindeki elemanları ayırarak kullanmamıza olanak tanır.

Spread operator kullanım alanları şunlardır:

- Dizileri birleştirmek.
- Bir dizi içindeki elemanları başka bir dizi içinde kullanmak veya eklemek.
- Bir dizinin içindeki elemanları bir fonksiyona parametre olarak vermek.
- Objeleri birleştirmek.
- Yeni objeler oluşturmak ve yeni özellikler eklemek.
- Bir objeyi başka bir objeye kopyalamak.

## Spread Operator Nasıl Kullanılır?

Örnek vermek gerekirse:

```javascript
function multiply(x, y, z) {
  return x * y * z;
}

const numbers = [1, 2, 3];

console.log(multiply(...numbers)); // multiply(1, 2, 3)
```

Yukarıda, `number` dizisinin bütün elemanlarını `...number` operator’ünü kullanarak `multiply` fonksiyonuna parametre olarak verdik. Burada `multiply(...number)` ve `multiply(1, 2, 3)` aynı işi yapar.

Spread operator’ünü kullandığımız 3 farklı yer bulunmaktadır:

1. Fonksiyon argümanlarında: `myFunction(a, ...iterableObj, b)`
2. Dizilerde: `[1, ...iterableObj, '4', 'five', 6]`
3. Objelerde: `{ ...obj, key: 'value'}`

>  Not: Spread operator sadece iterasyon yapılabilen diziler ve nesnelerde kullanılabilir.

Bir nesne, bir dizinin içinde spread operator ile kullanılamaz.

```javascript
const nesne = { anahtar1: "deger1"};  
const dizi = [...nesne] /// TypeError: nesne is not iterable
```

Kullanıldığı takdirde yukarıdaki gibi TypeError hatası verir.

Bunun yanında, bir dizinin elemanları bir nesne içinde spread operator ile kullanılabilir.

```js
const dizi = [1, 2, 3];  
const nesne = { ...dizi }; // { 0: 1, 1: 2, 2: 3 }  
  
console.log(nesne)
```

## Dizilerde Spread Operator Kullanımı
### Fonksiyon Parametrelerinde Spread Operator Kullanımı

Eskiden spread operator’dan önce bir dizinin elemanlarını fonksiyon parametresi olarak kullanmak için `Function.prototype.apply()` fonksiyonunu kullanırdık.

```js
function sum(x, y, z) {
 return x + y + z;
}

const numbers = [2, 3, 4,];

console.log(sum.apply(null, numbers))
```

Spread operator ile bu işlemi aşağıdaki gibi yapabilirsiniz.

```js
function sum(x, y, z) {
 return x + y + z;
}

const numbers = [2, 3, 4,];

console.log(sum(...numbers))
```

Spread operator ile fonksiyona istediğinizden daha fazla argüman verebilirsiniz.

```js
function sum(x, y, z) {
 return x + y + z;
}

const numbers = [2, 3, 4, 5, 6];

console.log(sum(...numbers))

```

Fonksiyon sadece ilk 3 sıradaki 2, 3, 4 argümanlarını parametre olarak alacaktır.

Başka bir örnek kullanım:

```js
function sum(x, y, z, k) {
 return x + y + z + k;
}

const numbers = [2, 3];

console.log(sum(1, ...numbers, 4)) // sum(1, 2, 3, 4)
```

Bir constructor fonksiyonunu `new` ile çağırırken `apply()` fonksiyonunu kullanmak mümkün olmadığı için bir dizinin elemanlarını argüman olarak fonksiyona veremeyiz. Tam bu noktada spread operator imdadımıza koşuyor.

```js
const dateFields = [1970, 0, 1]; // 1 Jan 1970  
const d = new Date(...dateFields);
```

### Dizileri Kopyalama ve Birleştirme

Spread operator’ünü kullanarak bir dizinin içine başka bir dizinin elemanlarını rahatlıkla ekleyebiliriz. Spread olmadan bu işlemi `push`, `splice`, `concat` fonksiyonları ile yapmak zorundaydık.

```js
const meyveler1 = ["elma", "armut", "kivi", "muz"]  
const meyveler2 = ["portalak", ...meyveler1 ,"mandalina"]  
// "portalak", "elma", "armut", "kivi", "muz" ,"mandalina"
```

Yukarıda, `meyveler1` dizisinin elemanlarını `meyveler2` dizisinin içine kolayca yerleştirdik.

Spread kullanarak bir diziyi kolay bir şekilde kopyalayabiliriz.

```js
const arr = [1, 2, 3];  
const arr2 = [...arr]; // [1, 2, 3]
```

### Spread Operator ile Dizi Elemanlarını Birleştirme
Eğer spread operator kullanmadan bir diziyi birleştirmek isteseydik `concat()` fonksiyonunu kullanırdık.

```js
const dizi1 = [1, 2, 3]  
const dizi2 = [4, 5, 6]  
  
const yeniDizi = dizi1.concat(dizi2)  
console.log(yeniDizi) // [1, 2, 3, 4, 5, 6]
```

Spread ile bunu aşağıdaki gibi yapabiliriz.

```js
const dizi1 = [1, 2, 3]  
const dizi2 = [4, 5, 6]  
  
const yeniDizi = [...dizi1, ...dizi2]; // [1, 2, 3, 4, 5, 6]  
  
console.log(yeniDizi)
```

Bu yöntem ile hangi dizinin başa, hangisinin sona geleceğini kolay bir şekilde belirtebiliriz.

## Objelerde Spread Operator Kullanımı
### Objeleri Kopyalama
Spread operator’ünden önce nesneleri kopyalamak için `Object.assign()` fonksiyonu kullanılırdı.

```js
const obje1 = { a: 1, b: 2 };  
  
const result = Object.assign(obje1, null);  
console.log(obje1); // { a: 1, b: 2 }  
console.log(result); // { a: 1, b: 2 }
```

Spread operator ile aşağıdaki gibi kullanılır.

```js
const obje1 = { a: 1, b: 2 };  
  
const result = {...obje1};  
console.log(obje1); // { a: 1, b: 2 }  
console.log(result); // { a: 1, b: 2 }
```

Spread operator’ü ile nesne kopyalamada kaynak nesnenin değişmesi, hedef nesneyi etkilemezken, `Object.assign()` kullanılarak nesne kopyalama işleminde kaynak nesnenin değişmesi, hedef nesneyi etkiler.

### Objeleri Birleştirme

Nesneleri birleştirme işlemini aşağıdaki gibi yapabiliriz.

```js
// assing ile  
const target = { a: 1, b: 2 };  
const source = { b: 4, c: 5 };  
  
const result = Object.assign(target, source);  
  
console.log(target); // { a: 1, b: 4, c: 5 }  
console.log(result); // { a: 1, b: 4, c: 5 }  
  
// spread ile  
const obj1 = { a: 1, b: 2 };  
const obj2 = { b: 4, c: 5 };  
  
const result = {...obj1, ...obj2}  
  
console.log(result); // { a: 1, b: 4, c: 5 }
```

`Object.assign` kullanarak birleştirme işlemi hedef nesne üzerine yazılırken, spread ile birleştirme yaparken kaynak ve hedef nesne birleşir.

### Objeye Yeni Özellikler Eklemek
Spread operator’ünden önce objelere özellik eklerken nokta notasyonu veya köşeli parantez notasyonu kullanırdık.

Eski kullanım:

```js
const obje1 = { name: "Ali", surname: "Kaya" };

obje1.age = 12;
obje1["city"] = "Konya";

console.log(obje1); //{ name:

 'Ali', surname: 'Kaya', age: 12, city: 'Konya' }

```

Spread operator’den sonra ise bu işlemi oldukça pratik bir şekilde yapabiliriz:
```js
const obje1 = { name: "Ali", surname: "Kaya" };

const newObje = { ...obje1, age: 12, city: "Konya" };

console.log(newObje); //{ name: 'Ali', surname: 'Kaya', age: 12, city: 'Konya' }

```

## JavasSript Spread Operator Deep Copy

Spread operator yüzeysel kopyalama yani shallow copy yapar. Bu, sadece 1. seviyede bulunan elemanları kopyalayacağı anlamına gelir. Daha derin seviyede bulunan elemanların referanslarını kopyalar. Dolayısıyla, kopyalanmış bir dizinin derin seviyedeki bir elemanını değiştirirsek, orijinal dizide değişiklik olur.

Bir örnekle inceleyelim:

```js
const orjinal = { x: 1, y: { z: 2 } };
const kopya = { ...orjinal };

kopya.y.x = 8;

console.log(orjinal.y.z); // 8 (orjinal nesne de değişti)
console.log(kopya.y.z);    // 8
```

Yukarida `orjinal` nesnesini spread ile `kopya` nesnesine kopyaladik. Ama spread  shallow copy  yaptigi icin `kopya.y.x = 8;` satiri orjinal nesneyi de degistirdi.

Yukarıda, `orijinal` nesneyi spread operatörüyle kopyaladık. Ancak spread operatorü shallow copy yaptığı için `kopya.y.z = 8;` satırı orijinal nesneyi değiştirdi.

### Derin Kopya (Deep Copy) Yapma

Derin kopya yapabilmek için birden çok yöntem vardır, ben sadece burada en basit olanı olan JSON yöntemini göstereceğim. Ancak bu yöntem `Map`, `Date`, `Set` gibi özel nesneleri kopyalamaz.

```js
const orjinal = { x: 1, y: { z: 2 } };
const derinKopya = JSON.parse(JSON.stringify(orjinal));

derinKopya.y.z = 8;

console.log(orjinal.y.z); // 2 (orjinal nesne etkilenmedi)
console.log(derinKopya.y.z); // 8
```

`JSON.stringify` fonksiyonu ile önce orijinal nesneyi string türüne çeviriyoruz, daha sonra `JSON.parse` fonksiyonu ile string türündeki nesneyi tekrar nesne haline getirip `derinKopya` nesnesine atıyoruz. Artık sorunsuz bir şekilde nesneler üzerinde değişiklik yapabiliriz. Nesneler birbirini etkilemeyecektir çünkü iki nesnenin tüm seviyelerdeki referansları birbirinden farklıdır.


## Spread Operator’ün Sağladığı Avantajlar

**Temiz ve Basit Kod:** Spread operator büyük ve karmaşık veriler üzerinde çalışırken önceki yöntemlere nazaran daha az kod yazmamızı sağlar, bu da karmaşıklığı oldukça azaltır. Bu durum kodun okunabilirliğini önemli ölçüde artırır.

**Daha Az Hata Yapma, Bakımı Kolay Kod:** Spread operator kodu daha sade ve okunabilir hale getirdiği için hata yapma olasılığımız azalır ve kodun bakımı daha kolay hale gelir.

**Yeniden Kullanılabilirlik:** Spread operator dizileri veya nesneleri kopyalarken veya birleştirirken dizileri veya nesneleri doğrudan değiştirmek yerine bir kopyasını oluşturur. Bu durum sayesinde kod tekrar kullanılabilir ve modüler hale gelir.

**Immutable Yapı:** Spread operator, React framework’ünde sıkça kullanılan immutable yapılarda ve state management konularında oldukça kullanışlıdır. Örneğin, immutable bir nesneyi güncellemek için spread operator büyük bir kolaylık sağlar. Bunun sayesinde çok daha pratik, temiz ve bakımı kolay kod yazmamıza olanak tanır.

**Fonksiyonel Programlama:** Spread operator veri kopyalarken veya birleştirirken fonksiyonel programlamanın "immutability" (değişmezlik) ilkesine uygun bir şekilde davranır; yani veriyi değiştirmez, bunun yerine yeni veri oluşturur ve mevcut veriyi korur. Bu da fonksiyonel programlama ilkesine uygundur.

## Sonuç

Spread Operator, veri yapılarını daha etkili hale getirir, kopyalama, birleştirme gibi işlemleri daha kolay hale getirir. Veri üzerinde mutasyon yapmadan verilerin manipülasyonuna olanak tanır. Eski yöntemlere nazaran kodu daha okunabilir ve basit bir hale getirir. Bu sayede bakımı ve anlaşılması daha kolay olur.


**Kaynaklar:**
- <https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax>
- <https://www.freecodecamp.org/news/an-introduction-to-spread-syntax-in-javascript-fba39595922c/>
- <https://javascript.info/rest-parameters-spread>
