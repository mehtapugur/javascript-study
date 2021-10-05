  - Fonksiyonel programlama, çözümlerin basit, izole fonksiyonlar olduğu, fonksiyon kapsamı dışında herhangi bir yan etkisi olmayan bir programlama stilidir:
  - ``INPUT -> PROCESS -> OUTPUT``
  - Aynı girdi her zaman aynı çıktıyı verir.
  - Fonksiyonel programlama bir bildirimsel programlama biçimidir. Bir yöntem veya işlev çağırarak bilgisayara ne yapmak istediğinizi söylersiniz.

### FCC terminolojisine bakalım:

  - ***Callbacks*** are the functions that are slipped or passed into another function to decide the invocation of that function.
You may have seen them passed to other methods, for example in filter, the callback function tells JavaScript the criteria for how to filter an array.
  - ***First Class*** Functions that can be assigned to a variable, passed into another function, or returned from another function just like any other normal value,
are called first class functions. In JavaScript, all functions are first class functions.
  - ***Higher Order*** The functions that take a function as an argument, or return a function as a return value are called higher order functions.
  - ***lambda*** When functions are passed in to or returned from another function, then those functions which were passed in or returned can be called a lambda.
 <hr>
 
 #### Avoid Mutations and Side Effects Using Functional Programming
 
  - FC'nin temel ilkelerinden biri, bir şeyleri değiştirmemektir. Changes lead to bugs.
  - Fonksiyonel programlamada bir şeyleri değiştirmeye ***mutation*** ve sonuca ***side effect*** denir.
  - Bir değişkeni veya nesneyi değiştirmeyin - yeni değişkenler ve nesneler oluşturun ve gerekirse bunları bir işlevden döndürün.
  
  
 #### Bir Fonksiyonda Dışa Bağımlılıktan Kaçınmak İçin Argümanları İletin
 
  - İşlevsel programlamanın başka bir ilkesi, bağımlılıklarınızı her zaman açıkça bildirmektir.
  - Bu sayede parametre ile alınan değişkeni değiştirmeden fonksiyon içinde kullanabiliriz.
  - İşlev parametreleri bildir - bir işlev içindeki herhangi bir hesaplama, herhangi bir genel nesne veya değişkene değil, yalnızca işleve iletilen argümanlara bağlıdır.
 
#### Return Part of an Array Using the slice Method

  - Slice yöntemi, bir dizinin belirli öğelerinin bir kopyasını döndürür.
  - İki argüman alabilir, ilki dilimin nereden başlayacağının indeksini verir, ikincisi dilimin nerede biteceğinin indeksidir (ve dahil değildir)
  - Argümanlar sağlanmazsa ya da verilmezse, varsayılan olarak dizinin başından sonuna kadar gider; bu, tüm dizinin bir kopyasını oluşturmanın kolay bir yoludur.
  - Yani hiçbir şey yazmazsak aslında yaptığımız şey diziyi kopyalamaktır.
  - Slice yöntemi orijinal diziyi değiştirmez, ancak yeni bir tane döndürür.
Here's an example:
```js
var arr = ["Cat", "Dog", "Tiger", "Zebra"];
var newArray = arr.slice(1, 3);
```
newArray would have the value ["Dog", "Tiger"].

#### Remove Elements from an Array Using splice

  - JavaScript, öğelerin kaldırılmasına nereden başlanacağı ve ardından kaldırılacak öğelerin sayısı için bağımsız değişkenler alan ***splice*** yöntemini sunar.
  - İkinci argüman sağlanmazsa, varsayılan, öğeleri sonuna kadar kaldırmaktır.
  - ***!!!*** splice yöntemi, çağrıldığı orijinal diziyi değiştirir.
  - 
