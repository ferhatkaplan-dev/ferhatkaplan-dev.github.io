---
title: "Python Requests Modülü Kullanımı"
date: 2024-07-24 16:30:00 +0300
categories: [programing, python, module]
tags: [python, requests modülü, modül, request]
description: "Python Requests modülünü kullanarak HTTP istekleri yapmayı öğrenin. GET ve POST istekleri, parametre ve header ekleme, JSON veri alışverişi, hata yönetimi ve cookies kullanımı hakkında kapsamlı bilgi edinin."
image:
  path: assets/img/post_images/2024-07-24-python-requests-modulu-preview.webp
  lqip: assets/img/post_images/2024-07-24-python-requests-modulu-preview-low.avif
  alt: Python Requests modülünü tanıtan bir resim.
---

## Requests Nedir?

**Requests** modülü, HTTP isteklerini basit, anlaşılır bir şekilde kullanmamıza olanak tanıyan bir Python modülüdür. Genellikle veri çekme, API'lar ile çalışma ve otomasyon programları yazmak için kullanılır. Hadi nasıl kullanılıyormuş bakalım.

## HTTP İsteklerini Yakalamak İçin Express.js Kullanımı

Bu kısımda atacağımız HTTP isteklerini daha iyi görebilmemiz için Express.js ile basit bir API kurulumunu göstereceğim. Eğer bununla uğraşmak istemiyorsanız **[Pipedream](https://pipedream.com/)** gibi istekleri yakalayan bir online hizmet kullanabilirsiniz. Hadi kuruluma başlayalım.

> Not: Node.js'in bilgisayarınızda kurulu olması gerekmektedir. `node -v` ile kurulu olup olmadığını kontrol edebilirsiniz.

1. İlk olarak `package.json` dosyamızı `npm init -y` komutu ile kuralım.
2. `express.js` paketini `npm install express` komutu ile kuralım.
3. `server.js` adında bir dosya oluşturup aşağıdaki kodları dosyaya yapıştıralım.

```js
const express = require("express");
const app = express();
const port = 3000;

app.use(express.json());
app.use(express.urlencoded({ extended: true }));

app.get("/", (req, res) => {
  console.log("Get istegi alindi.");
  console.log("Header:", req.headers);
  console.log("Full URL:", `${req.protocol}://${req.hostname}${req.originalUrl}`);
  console.log("-----------------------------------------");
  res.send("Get istegi geldi.");
});

app.post("/post", (req, res) => {
  console.log("Post istegi alindi.");
  console.log("Header:", req.headers);
  console.log("Body:", req.body);
  console.log("-----------------------------------------");
  res.send("Post istegi geldi.");
});

app.listen(port, () => {
  console.log("http://localhost:" + port);
});


```

Son olarak sunucumuzu çalıştırmak için `node server.js` komutunu çalıştıralım. Artık sunucumuz doğru bir şekilde çalışmaktadır.


## Requests Kurulumu

Requests modülümüzü sistemimize kurmamız için `pip` Python paket yöneticisinin kurulu olması gerekmektedir. Eğer Python kurulu ise `pip` yanında kurulu olarak gelmektedir. Terminale `pip` yazarak kurulu olup olmadığını kontrol edebilirsiniz.

Requests modülümüzü kurmak için aşağıdaki komutu kullanalım:
```sh
pip install requests
```


## Temel Kullanımı

### Get İsteği

Get isteği en çok kullanılan HTTP isteklerinden biridir. Genellikle sunucudan bir şey talep etmek için kullanılır. Get isteğinin nasıl kullanıldığına dair kolay bir örnek:

```python
import requests

URL = "http://127.0.0.1:3000"
res = requests.get(URL)
print(res.text)
```

Express.js sunucu çıktısı:
```
host: '127.0.0.1:3000',
'user-agent': 'python-requests/2.32.3',
'accept-encoding': 'gzip, deflate',
accept: '*/*',
connection: 'keep-alive'
```

### Post İsteği

POST isteği sunucuya veri gönderimi için kullanılan bir HTTP isteğidir. Yaygın olarak form işlemlerinde kullanılır. POST isteğinin nasıl kullanıldığına dair kolay bir örnek:

```python
import requests

URL = "http://127.0.0.1:3000/post"

post_data = {"username": "ali", "password": "ali123"}
res = requests.post(URL, data=post_data)
print(res.text)
```

Express.js sunucu çıktısı:
```
Header: {
  host: '127.0.0.1:3000',
  'user-agent': 'python-requests/2.32.3',
  'accept-encoding': 'gzip, deflate',
  accept: '*/*',
  connection: 'keep-alive',
  'content-length': '28',
  'content-type': 'application/x-www-form-urlencoded'
}
Body: { username: 'ali', password: 'ali123' }
```


## HTTP İsteklerine Parametre Ekleme

HTTP isteklerine parametre eklemek için `params` veya `data` argümanlarını kullanırız.

### Params Kullanımı

Örnek kullanım:
```python
import requests

URL = "http://127.0.0.1:3000"
params = {"query": "python"}
res = requests.get(URL, params=params)
print(res.url)

```

Express.js sunucu çıktısı:
```
Header: {
  host: '127.0.0.1:3000',
  'user-agent': 'python-requests/2.32.3',
  'accept-encoding': 'gzip, deflate',
  accept: '*/*',
  connection: 'keep-alive'
}
Full URL: http://127.0.0.1/?query=python
```

Full URL kısmında gördüğünüz gibi istek URL'sine `?/query=python` sorgusunu ekledi.

### Data Kullanımı
Örnek kullanım:
```python
import requests

URL = "http://127.0.0.1:3000/post"
post_data = {"name": "osman", "surname": "deli"}

res = requests.post(URL, data=post_data)
print(res.text)

```

Express.js sunucu çıktısı:
```
Header: {
  host: '127.0.0.1:3000',
  'user-agent': 'python-requests/2.32.3',
  'accept-encoding': 'gzip, deflate',
  accept: '*/*',
  connection: 'keep-alive',
  'content-length': '23',
  'content-type': 'application/x-www-form-urlencoded'
}
Body: { name: 'osman', surname: 'deli' }
```

Yukarıda da gördüğünüz gibi `data` parametresine verdiğimiz veri **body** ile gönderildi.

## Header Ekleme

Requests modülünde header önemlidir çünkü bazı sunucular Python user-agent'ını kabul etmeyebiliyor.

```python
import requests

URL = "http://127.0.0.1:3000"
headers = {
    "User-Agent": "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/126.0.0.0 Safari/537.36"
}

res = requests.get(URL, headers=headers)
print(res.text)

```

Express.js sunucu çıktısı:
```
Header: {
  host: '127.0.0.1:3000',
  'user-agent': 'Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/126.0.0.0 Safari/537.36',
  'accept-encoding': 'gzip, deflate',
  accept: '*/*',
  connection: 'keep-alive'
}
Full URL: http://127.0.0.1/
```

Böylelikle "user-agent" bölümünü istediğimiz gibi değiştirdik.

## JSON Veri Alışverişi

Günümüzde API'lar çoğunlukla JSON formatında veri alışverişi yaparlar. Hadi Requests modülünde bunu nasıl yapacağımızı öğrenelim.

**JSON verisi gönderme:**
```python
import requests

URL = "http://127.0.0.1:3000/post"

json_data = {"password": "123123"}

res = requests.post(URL, json=json_data)
print(res.text)

```

Express.js sunucu çıktısı:
```
Header: {
  host: '127.0.0.1:3000',
  'user-agent': 'python-requests/2.32.3',
  'accept-encoding': 'gzip, deflate',
  accept: '*/*',
  connection: 'keep-alive',
  'content-length': '22',
  'content-type': 'application/json'
}
Body: { password: '123123' }
```

Gördüğünüz gibi `json` parametresi ile gönderdiğimiz veriyi **body** ile yakaladık.

**JSON verisi alma:**
Öncelikle Express.js sunucumuz şu anda bir JSON döndürmüyor bu yüzden `res.send("Get isteği geldi.");` satırını bulup `res.json({key: "value"});` ile değiştirmeliyiz. Ardından terminalde `Ctrl + c` ile sunucumuzu durdurup `node server.js` komutu ile tekrar çalıştırmamız gerekmektedir.

```python
import requests

URL = "http://127.0.0.1:3000"

res = requests.get(URL)
print(res.json())

```

Express.js sunucu çıktısı:
```
Header: {
  host: '127.0.0.1:3000',
  'user-agent': 'python-requests/2.32.3',
  'accept-encoding': 'gzip, deflate',
  accept: '*/*',
  connection: 'keep-alive'
}
Full URL: http://127.0.0.1/
```

Python çıktısı:
```
{'key': 'value'}
```

## Hata Yönetimi

Requests modülü ile HTTP isteğinde bulunurken herhangi bir hatayı kontrol edebilmek için `response.raise_for_status()` fonksiyonunu kullanırız. Bu fonksiyon HTTP isteğinin yanıtını kontrol eder ve yanıt 200-399 arasında değilse geriye `HTTPError` hatasını fırlatır.

Kullanım:
```python
import requests

URL = "http://127.0.0.1:3000"


try:
    res = requests.get(URL)
    res.raise_for_status()
    # ....
except requests.exceptions.HTTPError as error:
    print(f"HTTP error: {error}")
except Exception as error:
    print(f"Other error: {error}")

```

Böylelikle istek sırasında oluşabilecek hataları rahatlıkla yakalayabiliriz.


## Cookies Yönetimi

### HTTP İsteğine Cookie Ekleme
```python
import requests

URL = "http://127.0.0.1:3000"
new_cookies = {"session_id": "akldjfas32"}

res = requests.get(URL, cookies=new_cookies)
print(res.text)

```

### Cookielere Erişim
```python
import requests

URL = "http://127.0.0.1:3000"

res = requests.get(URL)
cookies = res.cookies

for cookie in cookies:
    print(cookie.name, cookie.value)

print(res.text)

```

Cookieler hakkında bilmeniz gereken birkaç önemli bilgi daha var. Cookieler name, value, domain, path, expires, secure vs. gibi birçok özellik ile cookienin ne zaman ve nasıl kullanacağını belirtir. Güvenlik nedeniyle bazı çerezler sadece https üzerinden gönderilir, bu secure özelliği ile alakalıdır.


## Python Requests Modülü Response Nesnesinin Fonksiyon ve Özellikleri

- **res.status_code:** HTTP yanıtının kodunu döndürür.
- **res.headers:** HTTP yanıtının headers'ını döndürür ve `res.headers['accept-language']` şeklinde kullanabilirsiniz.
- **res.cookies:** HTTP yanıtının cookie'sini döndürür. `res.cookies['id']` şeklinde kullanabilirsiniz.
- **res.url:** HTTP yanıtının URL'sini döndürür.
- **res.encoding:** HTTP yanıtının kodlama türünü döndürür.
- **res.text:** HTTP yanıtının body'sini string formatında döndürür.
- **res.content:** HTTP yanıtını raw bir şekilde döndürür.
- **res.json():** HTTP yanıtının body'sini JSON formatında döndürür.
- **res.raise_for_status():** HTTP yanıtının kodu 200-399 arasında değilse bir `HTTPError` hatasını fırlatır.
- **res.iter_lines(decode_unicode=False):** HTTP yanıtını itere edilebilir bir şekilde satır satır döndürür ve `for ... in` yanıtına satır satır erişebilirsiniz.
- **res.iter_content(chunk_size=1024, decode_unicode=False):** HTTP yanıtını belirli boyutlarda parçalara ayırarak döndürür.

Daha fazla ayrıntılı bilgi için: [https://requests.readthedocs.io/en/latest/](https://requests.readthedocs.io/en/latest/)