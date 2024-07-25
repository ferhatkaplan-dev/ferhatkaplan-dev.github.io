---
title: Kaliteli Commit Mesajları ve İpuçları
date: 2024-07-23 03:30:00 +0300
categories: [programing, git]
tags: [git, github, commit message]
description: "Git commit nedir, nasıl yapılır ve neden önemlidir? Bu makalede, kaliteli commit mesajları oluşturma, semantik commit kullanımı ve Git ticket sistemleriyle uyum hakkında kapsamlı bilgiler bulabilirsiniz. Projenizi nasıl daha iyi yönetebilirsiniz?"
image:
  path: assets/img/post_images/2024-07-23-commit-mesaji-nasil-yazilmali.png
  lqip: assets/img/post_images/2024-07-23-commit-mesaji-nasil-yazilmali-low.png
  alt: git commit mesajı fotoğrafı
---

## Git Commit Ne İş Yapar ve Neden İhtiyaç Duyarız?

`git commit` komutu, bir git reposundaki değişikliklerin eklenmesi, silinmesi veya güncellenmesi işlemlerinin anlık bir görüntüsünü alarak kaydeder. Bu, bilgisayar oyunlarındaki oyun kaydetme işlemine benzer şekilde çalışır. Projemiz belirli bir aşamaya geldiğinde, git commit komutu ile ilerlememizi kaydederiz. Bu, projenin daha önceki sürümlerine dönülebilmesini sağlar ve işbirliği yaptığımız diğer geliştiricilerin çalışmalarını takip etmesine yardımcı olur.

Git commit mesajını yazmanın en basit yolu, `git commit -m “commit mesajınız”` komutunu kullanmaktır. Bu komut, değişikliklerin anlık bir görüntüsünü alarak depoya kaydeder ve “commit mesajınız” olarak adlandırılan açıklayıcı bir mesaj ile bu değişikliklerin ne olduğunu belirtir. Bu sayede, depodaki değişikliklerin ne zaman ve neden yapıldığı gibi bilgileri takip edebilir ve projenin daha önceki sürümlerine dönebilirsiniz. Ayrıca, commit mesajlarının açıklayıcı olması, projeye dahil olan diğer geliştiricilerin çalışmalarını takip etmelerine yardımcı olur ve projenin gelecekteki gelişimini kolaylaştırır.

## Commit Mesajı Nedir ve Neden Önemlidir?

Commit mesajı, bir Git commit işlemi sırasında eklenen açıklayıcı bir metindir ve commit’i yazan geliştirici tarafından commit nesnesine eklenir. 

Commit mesajları genellikle bir başlık ve isteğe bağlı bir gövdeye sahiptir. Başlık, değişikliklerin özetini içerirken, gövde daha ayrıntılı bilgiler sağlayabilir. 

Commit mesajları, projedeki değişikliklerin ne olduğunu ve neden yapıldığını açıklamak için kullanılır. Bu sayede, projenin gelecekteki okuyucuları veya diğer geliştiricileri değişiklikleri anlayabilir ve projenin tarihini takip edebilir.

Commit mesajları, yazdığımız kodların anlaşılması için de önemlidir. Çünkü gelecekteki bir zamanda, kodlara tekrar baktığımızda yazdığımız eski kodları daha iyi anlamamızı sağlar. 

## Kaliteli Commit Mesajı Nasıl Oluşturulur?

Commitlerimiz kod değişikliklerimizin anlık bir görüntüsüdür ve bu değişikliklerin açıklamasını içeren commit mesajları ile birlikte saklanır. Bu nedenle, iyi yazılmış commit mesajları kodumuzun ne iş yaptığını daha sonra bakan kişilerin anlamasına yardımcı olur. Eğer kötü veya yetersiz commit mesajları yazarsak, kodumuzda bir hata oluştuğunda bu hatayı bulmak için eski commit mesajlarına bakmamız gerekebilir. Bu durumda, hataları bulmak için tüm kodu okumamız gerekebilir ve bu zaman alıcı ve zahmetli bir işlemdir. Ayrıca, aylar önce yazılmış bir kodun ne iş yaptığını anlamak zor olabilir. İyi yazılmış commit mesajları, hataların nerede olduğunu kolayca bulmamızı ve kodun ne yaptığını anlamamızı sağlar. Bu sayede, hataları düzeltebilir ve kodu daha iyi bir duruma getirebiliriz.

## Genel commit mesajları atma kuralları

Commit mesajları, genel kural olarak, başlık kısmının 50 karakteri geçmeyecek şekilde kısa, açıklayıcı ve tek satır olmalıdır. Ardından boş bir satır bırakılmalı ve daha ayrıntılı açıklayıcı metin isteğe bağlı olarak yazılabilir. 

Eğer commitinizde birden fazla değişiklik varsa, tek bir kısa mesajla commit yazmak zor olabilir. Bu durumda değişiklikleri birden fazla commite bölerek işinizi kolaylaştırabilirsiniz. Örneğin, 3 değişiklik yaptığınız bir committe, 2 tanesi sorunsuz çalışıyor ama bir tanesi ileride hata nedeni oluyorsa, bu hatayı düzeltmek için commit atmadan önceki orijinal haline döndüğünüzde, çalışan 2 değişiklik durumunu da silmek zorunda kalabilirsiniz. Bu durumu yaşamamak için değişiklikleri mümkün olduğunca küçük parçalar halinde commitlemeniz önerilir.

Daha kaliteli commit mesajı yazmak için aşağıdaki önerileri takip edebilirsiniz:

1. Kısa ve öz olsun:

   - Bir committen daha az değişiklik bulunması mesajı kısa yazmanıza yardımcı olacaktır.
   - Mesajınızın açık ve anlaşılır olması için tek bir konuya odaklanın ve olabildiğince sade tutun.

2. Şimdiki zaman ve emir kipi kullanın:

   - “x metodunu asenkron yap” gibi.

3. Kisa bir başlık ekleyin:

   - Başlık 50 karakterden az olmalı.
   - Çoğu kod yönetim sistemleri, commit mesaj başlıkları için sınırlı bir alan sağlar ve bu genellikler 50 karakterle sınırlıdır, bu nedenle mesajinizin tamamının görünmesi için 50 karakterden az olması gerekmektedir.
   - Başliginizin kısa olması diğer ekip uyelerinizin hızlı bir şekilde değişiklikler hakkında bilgi edinmesine yardımcı olur.
   - Başlıkları başlık gibi yani kelimelerin baş harflerini büyük yazın.(Opsiyonel)

4. İsteğe bağlı bir gövde ekleyin:

   - Başlık ve gövde arasında bir boş satır olmalıdır.
   - Gövde satır uzunluğu 72 karakterden az olmalı.
   - Bu kısım yapılan değişikliğin ne olduğu, neden yapıldığı ve bu değişikliğin projeye etkisinin ne olduğunu yazdığımız kısımdır.
   - Değişikliğin ne olduğunu olabildiğince ayrıntılı şekilde anlatmalıyız.
   - Gereksiz ayrıntıdan kaçının.

5. Büyük boyutlu commit mesajlarından kaçının:

   - 100mb’lik bir mesaj kesinlikle performans sorunlarına neden olacaktır.

6. Mesajları ingilizce yazın:

   - Ingilizce dünya genelinde ve özellikler teknolji alanında kullanılan ortak dil olduğu için ingilizce kullanmak, projeye katkı sağlayan insanların commit mesajlarını daha kolay okumasına ve anlamasına yardımcı olacaktır.

Bunların yanında footer yani alt bilgide eklenebilir ve bu genelde jira kimlik numarası veya sorunun numarası gibi harici bir referans kimlik numarasıdır.

Kötü commit örneği:

```
Fix some bugs
```
Bu commit mesajı, değişikliğin ne olduğunu açıkça tanımlamaz ve hangi hataları düzelttiği belirtilmez. Bu tür bir commit mesajı, gelecekte bu değişikliği geri izlemeyi zorlaştırabilir.

İyi commit örneği:

```
feat: Add user authentication feature
```


## Semantic Commit Nedir?

Sematic commit, commitin amacını ve ne iş yaptığımızı kısa ve oz olarak belirten bir yapıya sahiptir. Commit mesajlarının okunakligini artırır bunun yanında değişikliklerin daha anlaşılır şekilde takip edilmesini sağlar.

Sematic commit, commit mesajının başlığına bir on ek ve ardından kısa açıklama eklenmesiyle oluşur. Bunun yanında hangi bölümde değişiklik yapıldığını parantez içinde belirtebilirsiniz.

Örnek olarak aşağıdaki commite bakalım:

```
feat(login): Add support for user login
```

Yukarıdaki committe “feat” eki yeni bir özellik eklendiğini belirtmektedir. “login” ise hangi bölümde ekleme yapıldığını belirtir.

Sematic commitin genel yapısı aşağıdaki gibidir:

```
feat: add hat wobble
^--^  ^------------^
|     |
|     +-> Summary in present tense.
|
+-------> Type: chore, docs, feat, fix, refactor, style, or test.
```
- **feat**: “feature” kelimesinin kısaltmasıdır ve yeni bir özellik eklendiğinde kullanılır.
- **fix**: Hata düzeltmeleri için kullanılır.
- **docs**: Dokümantasyon değişiklikleri için kullanılır.
- **style**: Kodun stilinde yapılan değişikliklerde kullanılır.
- **refactor**: Var olan kodu iyileştirmek, yeniden yapılandırmak veya düzenlemek için kullanılır.
- **test**: Testler ile ilgili değişiklikler için kullanılır.
- **chore**: Kodun bakımı veya yapılandırması ile ilgili değişikliklerde kullanılır.

Daha fazla ayrıntı için bakınız: <https://gist.github.com/joshbuchea/6f47e86d2510bce28f8e7f42ae84c716>

Aşağıda birkaç tane commit örneği bulunmaktadır:

```
feat: Add pagination to user list page

This commit adds pagination functionality to the user list page,
allowing users to view a large number of users in smaller, more
manageable groups. The pagination controls are located at the bottom
of the page and allow the user to navigate through the different pages.

The following changes were made:
- Added pagination functionality to user list page
- Updated styling for pagination controls

No issues closed
```

```
fix: Resolve issue with user profile image upload

This commit fixes an issue where user profile images could not be
uploaded due to a server error. The issue was caused by an
incorrect file path in the upload function, which has now been
corrected.

The following changes were made:

Updated file path in upload function to correct path
Tested and verified image upload functionality
Issue #1234 closed
```

```
feat(requests): Add retry functionality for failed requests

This commit adds retry functionality to the requests module, allowing
failed requests to be retried automatically. The retry mechanism uses
an exponential backoff algorithm to gradually increase the time between
retries, preventing overwhelming the server with repeated requests.

The following changes were made:
- Added retry functionality to requests module
- Implemented exponential backoff algorithm for retry interval

No issues closed
```

## Git Ticket Sistemine Sahip Ekipler

Çoğu ekip, belirli bir iş bölümüne bir bilet numarası atayan “Jira” ve benzeri ticket sistemleri kullanır.

Commit mesajlarını yazarken, proje yönetimi için bir bilet veya takip sistemi kullanıyorsanız, commit mesajlarınızda bilet numaralarını kullanmak yararlı olabilir.

Örnek olarak [Jira](https://www.atlassian.com/software/jira) ticket’i “ACME-1” için aşağıdaki gibi bilet numarasını commitin başına dahil etmek kullanılan bir yöntemdir.

```
[ACME-1] Enable Logging Globally
```
Burada, “ACME-1” bilet numarası, değişikliğin hangi bilet için yapıldığını açıkça belirtir.

Bilet numaralarını commit mesajlarında kullanmak, hem diğer geliştiricilerin değişikliklerin hangi biletlerle ilgili olduğunu anlamalarına yardımcı olur, hem de proje yönetimindeki biletlerin takibini kolaylaştırır. Böylece, bilet numaralarını kullanmak, projenin izlenebilirliğini ve yönetilebilirliğini artırır.

Yardımcı kaynaklar:

```
1. https://medium.com/@steveamaza/how-to-write-a-proper-git-commit-message-e028865e5791
2. https://initialcommit.com/blog/git-commit-messages-best-practices
3. https://www.gitkraken.com/learn/git/best-practices/git-commit-message
4. https://www.microverse.org/blog/how-writing-meaningful-commit-messages-helps-you-be-a-better-developer
5. https://chiamakaikeanyi.dev/how-to-write-good-git-commit-messages/
6. https://github.blog/2022-06-30-write-better-commits-build-better-projects/
7. https://www.freecodecamp.org/news/how-to-write-better-git-commit-messages/
8. https://cbea.ms/git-commit/
9. http://who-t.blogspot.com/2009/12/on-commit-messages.html
10. https://corgibytes.com/blog/2019/03/20/commit-messages/
11. https://yvonnickfrin.dev/a-guide-on-commit-messages
12. https://hackernoon.com/power-up-your-pair-programming-with-co-authored-commits-on-github-ffb5d049aed3
13. https://docs.github.com/en/pull-requests/committing-changes-to-your-project/creating-and-editing-commits/creating-a-commit-with-multiple-authors
14. https://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html
15. https://medium.com/ltunes/git-commit-mesajlar%C4%B1m%C4%B1z-nas%C4%B1l-olmal%C4%B1-fdf3ae323672
16. https://oguzhanturan.medium.com/i%CC%87yi-bir-git-commit-mesaj%C4%B1-nas%C4%B1l-yaz%C4%B1l%C4%B1r-3b0cbc07377b
17. https://vigo.github.io/git-puf-noktalari/bolum-01/13-commit-mesaji-nedir/
18. https://www.conventionalcommits.org/tr/v1.0.0/
```
