---
title: "SCSS Dosya Yapısı: 7-1 Pattern ile Projelerinizi Nasıl Düzenlersiniz?"
date: 2024-07-30 01:30:00 +0300
categories: [programing, scss]
tags: [scss, 7-1 pattern, css, scss file structure]
description: "SCSS dosya yapınızı düzenlemenin yollarını mı arıyorsunuz? 7-1 pattern ile projelerinizde modülerlik, yeniden kullanılabilirlik ve bakım kolaylığı sağlayın. Bu kapsamlı kılavuz, büyük projelerde etkili bir SCSS organizasyonu için adım adım rehberlik eder ve dosya yapısının avantajlarını keşfetmenizi sağlar."
image:
  path: assets/img/post_images/2024-07-30-scss-dosya-yapisi-7-1-pattern-ile-projelerinizi-nasil-duzenlersiniz.webp
  lqip: assets/img/post_images/2024-07-30-scss-dosya-yapisi-7-1-pattern-ile-projelerinizi-nasil-duzenlersiniz.avif
  alt: SCSS 7-1 pattern kapak resmi
---

CSS ile yazdığımız projelerde proje büyüdükçe, bakım, tutarlılık, kod çakışmaları gibi sorunlarla karşılaşabiliriz. Bu sorunları düzgün bir dosya yapısı kullanarak SCSS ile aşabiliriz. SCSS bize modülerlik, yeniden kullanılabilir kod, bakım kolaylığı ve tutarlılık gibi avantajlar sağlar. Bunlara daha yakından bakalım.

- **Modülerlik:** SCSS kodumuzu daha modüler hale getirmeyi teşvik eder. Renkler, stil bileşenleri, tipografi gibi parçalara ayrılarak yazılabilir ve böylelikle her dosya sadece bir sorumluluğu olur. Bu sayede kod bakımı ve okunabilirliği artar. Örneğin `_variables.scss` dosyası projedeki ortak değerleri barındıran bir dosyadır.
- **Yeniden kullanılabilirlik:** SCSS mixin ve extend kullanarak kodun yeniden kullanılabilir olmasını sağlar ve kod tekrarını azaltır. Programlama prensiplerinden DRY prensibine uygundur.
- **Bakım kolaylığı:** Dosya yapısının modüler olması projelerin zamanla büyüyüp genişlemesi, güncelleme, hata düzeltmeleri gibi işleri daha kolay ve hızlı bir şekilde yapmamıza olanak tanır.
- **Tutarlılık:** SCSS değişkenler ve mixin gibi yapılar sayesinde stil yapısında daha tutarlı olunmasını sağlar.
- **Yapısal tutarlılık:** Projenin dosyalarının `base`, `components`, `layout` gibi bölümlere ayrılması yapısal olarak tutarlılık sağlar. Bu yapı projenin yönetimini ve takım çalışmasını kolaylaştırır.

Yani özetle SCSS karmaşıklığı azaltır, kod tekrarını ortadan kaldırır, bakımı ve yönetimi daha kolay hale getirir ve kodun organizasyonunu artırır.

## 7-1 Pattern Nedir?

**7-1 Pattern SCSS Dosya Yapısı:** Genellikle büyük projelerde kullanılır ve yönetimi oldukça kolaylaştırır. 7-1 pattern, projenizdeki dosyaları **abstracts**, **base**, **components**, **layout**, **pages**, **themes** ve **vendors**  7 klasöre bölerek modülerlik, tutarlılık, yapısal bütünlük ve bakım kolaylığı sağlar.

## 7-1 Pattern Dosya Yapısı

Şimdi aşağıdan 7-1 pattern yapısını inceleyelim.

```
styles/
|-- abstracts veya utilities/
|   |-- _variables.scss        // Renkler, fontlar gibi değişkenler
|   |-- _mixins.scss           // Tekrar kullanılabilir mixin'ler
|   |-- _functions.scss        // Tekrar kullanılabilir fonksiyonlar
|   |-- _breakpoints.scss      // Medya sorguları ve breakpoint'ler
|   |-- _shadows.scss          // Gölge efektleri
|   |-- _gradients.scss        // Gradyan geçişler
|
|-- base/
|   |-- _reset.scss            // Tarayıcı varsayılanlarını sıfırlama
|   |-- _typography.scss       // Genel tipografi ayarları
|   |-- _base.scss             // Genel stil kuralları
|   |-- _colors.scss           // Renk paletleri
|   |-- _forms.scss            // Form stilleri
|
|-- components/
|   |-- _buttons.scss          // Buton stilleri
|   |-- _carousel.scss         // Carousel stilleri
|   |-- _modal.scss            // Modal stilleri
|   |-- _cards.scss            // Kart stilleri
|   |-- _dropdowns.scss        // Açılır menü stilleri
|   |-- _alerts.scss           // Uyarı ve bildirim stilleri
|
|-- layout/
|   |-- _header.scss           // Üst bilgi stil ayarları
|   |-- _footer.scss           // Alt bilgi stil ayarları
|   |-- _sidebar.scss          // Yan menü stil ayarları
|   |-- _grid.scss             // Izgara sistemleri
|   |-- _container.scss        // Konteyner ayarları
|   |-- _navigation.scss       // Navigasyon stilleri
|
|-- pages/
|   |-- _home.scss             // Ana sayfa stil ayarları
|   |-- _about.scss            // Hakkında sayfası stil ayarları
|   |-- _services.scss         // Hizmetler sayfası stil ayarları
|   |-- _contact.scss          // İletişim sayfası stil ayarları
|   |-- _profile.scss          // Profil sayfası stil ayarları
|   |-- _dashboard.scss        // Yönetim paneli stil ayarları
|
|-- themes/
|   |-- _default.scss          // Varsayılan tema
|   |-- _dark.scss             // Koyu tema
|   |-- _light.scss            // Açık tema
|   |-- _colorful.scss         // Renkli tema
|   |-- _minimal.scss          // Minimalist tema
|
|-- vendors/
|   |-- _bootstrap.scss        // Bootstrap framework
|   |-- _swiper.scss           // Swiper slider
|   |-- _font-awesome.scss     // Font Awesome ikonları
|   |-- _slick.scss            // Slick slider
|
|-- utilities/
|   |-- _animations.scss       // Animasyon stilleri
|   |-- _responsive.scss       // Responsive ayarlar
|   |-- _transitions.scss      // Geçiş stilleri
|   |-- _helpers.scss          // Yardımcı sınıflar ve mixin'ler
|
|-- main.scss                  // Diğer tüm dosyaların import edildiği ana dosya
```

Yukarıdaki klasör yapısını daha yakından inceleyelim:

- **abstracts:** Mixins, fonksiyonlar, değişkenler gibi stil uygulamasında yardımcı olan araçların bulunduğu dizin, yani stilin kendisini oluşturmuyor, oluşturmasına yardımcı olan araçları barındırır; bundan dolayı adı "abstracts".
- **base:** Projeye genel görünümü ayarlamak için kullanılan stil dosyalarını içerir. `reset.scss` projenin reset stillerini, `typography.scss` projenin metin tipi stillerini, `base.scss` ise projenin bileşenlerinin stillerini içerir.
- **components:** `buttons.scss`, `carousel.scss` gibi özel bileşenlerin stillerini içeren dosyalardır.
- **layout:** `header`, `footer` ve `sidebar` gibi projenin ana katmanlarının stillerini içerir.
- **pages:** Sayfaların özel stillerini içeren dosyalardır.
- **themes:** Projenin dark ve light tema stillerini içeren dosyalardır.
- **vendors:** Projeye dahil edilmiş üçüncü taraf CSS kütüphanelerinin kodlarını içerir.

Örnek repolar:
- [sass-template](https://github.com/dostonnabotov/sass-template)
- [sass-boilerplate](https://github.com/KittyGiraudel/sass-boilerplate/tree/master)

Başka bir dosya yapısı örneği:

```
sass/
|
|- abstracts/
|    |- _variables.scss
|    |- _media-query.scss
|    |- _colors.scss
|    ...
|    |- _index.scss
|
|- base/
|    |- _base.scss
|    |- _reset.scss
|    ...
|    |- _index.scss
|
|- utilities/
|    |- _main.scss
|    |- _container.scss
|    |- _exceptions.scss
|    ...
|    |- _index.scss
|
|- components/
|    |- _buttons.scss
|    |- _carousel.scss
|    |- _dropdown.scss
|    ...
|    |- _index.scss
|
|- layout/
|    |- _header.scss
|    |- _sidebar.scss
|    |- _footer.scss
|    ...
|    |- _index.scss
|
|- pages/
|    |- _about.scss
|    |- _contact.scss
|    ...
|    |- _index.scss
|
|- themes/
|    |- _theme.scss
|    |- _admin.scss
|    ...
|    |- _index.scss
|
|- vendors/
|    |- _bootstrap.scss
|    |- _modern-reset.scss
|    ...
|    |- _index.scss
|
|- style.scss
```

Burada klasörlerin yanında `_index.scss` dosyaları bulunmaktadır çünkü `@import` yerine `@use` ve `@forward` kullanımını desteklemektedir.
