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

### concat

İki diziyi birleştirmeye yarar. Örneğin:
```js
[1, 2, 3].concat([4, 5, 6]);
```
The returned array would be [1, 2, 3, 4, 5, 6].

push ile concat farklıdır. Örneğin:
```js
var arr = [1, 2, 3];
arr.push([4, 5, 6]);
```
arr would have a modified value of [1, 2, 3, [4, 5, 6]], 

#### Use the reduce Method to Analyze Data

  - You can solve almost any array processing problem using the reduce method.
  - reduce, bir dizideki her öğe üzerinde yinelenir ve tek bir değer döndürür
  - dört bağımsız değişkeni kabul eder
  - İlk argüman, bir önceki yinelemeden callback işlevinin dönüş değerinin atandığı değişkendir
  - ikincisi işlenmekte olan geçerli öğedir
  - üçüncüsü o öğenin indeksidir ve dördüncüsü, reduce işleminin yapıldığı dizidir.
örnek:
```js
const users = [
  { name: 'John', age: 34 },
  { name: 'Amy', age: 20 },
  { name: 'camperCat', age: 10 }
];
const sumOfAges = users.reduce((sum, user) => sum + user.age, 0);
console.log(sumOfAges);
```
The console would display the value 64.

```js
const usersObj = users.reduce((obj, user) => {
  obj[user.name] = user.age;
  return obj;
}, {});
console.log(usersObj);
```
The console would display the value { John: 34, Amy: 20, camperCat: 10 }.

Problem: The variable watchList holds an array of objects with information on several movies. Use reduce to find the average IMDB rating of the movies directed by Christopher Nolan. Recall from prior challenges how to filter data and map over it to pull what you need. You may need to create other variables, and return the average rating from getRating function. Note that the rating values are saved as strings in the object and need to be converted into numbers before they are used in any mathematical operations.

Çözüm:
elimizdeki dizi
```js
var watchList = [
  {
    "Title": "Inception",
    "Year": "2010",
    "Rated": "PG-13",
    "Released": "16 Jul 2010",
    "Runtime": "148 min",
    "Genre": "Action, Adventure, Crime",
    "Director": "Christopher Nolan",
    "Writer": "Christopher Nolan",
    "Actors": "Leonardo DiCaprio, Joseph Gordon-Levitt, Elliot Page, Tom Hardy",
    "Plot": "A thief, who steals corporate secrets through use of dream-sharing technology, is given the inverse task of planting an idea into the mind of a CEO.",
    "Language": "English, Japanese, French",
    "Country": "USA, UK",
    "Awards": "Won 4 Oscars. Another 143 wins & 198 nominations.",
    "Poster": "http://ia.media-imdb.com/images/M/MV5BMjAxMzY3NjcxNF5BMl5BanBnXkFtZTcwNTI5OTM0Mw@@._V1_SX300.jpg",
    "Metascore": "74",
    "imdbRating": "8.8",
    "imdbVotes": "1,446,708",
    "imdbID": "tt1375666",
    "Type": "movie",
    "Response": "True"
  },
  {
    "Title": "Interstellar",
    "Year": "2014",
    "Rated": "PG-13",
    "Released": "07 Nov 2014",
    "Runtime": "169 min",
    "Genre": "Adventure, Drama, Sci-Fi",
    "Director": "Christopher Nolan",
    "Writer": "Jonathan Nolan, Christopher Nolan",
    "Actors": "Ellen Burstyn, Matthew McConaughey, Mackenzie Foy, John Lithgow",
    "Plot": "A team of explorers travel through a wormhole in space in an attempt to ensure humanity's survival.",
    "Language": "English",
    "Country": "USA, UK",
    "Awards": "Won 1 Oscar. Another 39 wins & 132 nominations.",
    "Poster": "http://ia.media-imdb.com/images/M/MV5BMjIxNTU4MzY4MF5BMl5BanBnXkFtZTgwMzM4ODI3MjE@._V1_SX300.jpg",
    "Metascore": "74",
    "imdbRating": "8.6",
    "imdbVotes": "910,366",
    "imdbID": "tt0816692",
    "Type": "movie",
    "Response": "True"
  },
```
böyle gidiyor.
Kod:
```js
function getRating(watchList){
  // Only change code below this line
  var count = 0;
  var averageRating = watchList.reduce((sum, film) => {
    if (film.Director == "Christopher Nolan") {
    count+=1;
    return sum + parseFloat(film.imdbRating);
  } 
  return sum;
  }, 0) / count;

  // Only change code above this line
  return averageRating;
}
console.log(getRating(watchList));
```

<hr>

#### Sort an Array Alphabetically using the sort Method

Sayıları sıralarken:
```js
function ascendingOrder(arr) {
  return arr.sort(function(a, b) {
    return a - b;
  });
}
ascendingOrder([1, 5, 2, 3, 4]);
```

Harfleri sıralarken:
```js
function reverseAlpha(arr) {
  return arr.sort(function(a, b) {
    return a === b ? 0 : a < b ? 1 : -1;
  });
}
reverseAlpha(['l', 'h', 'z', 'b', 's']);
```

sort() işlemi asıl diziyi mutasyona uğratır bu yüzden diziyi başka diziye kopyalayıp kullanmak daha güvenli.

#### Split a String into an Array Using the split Method

  - split yöntemi, bir stringi bir diziye dönüştürür
  - stringi neye göre böleceğine dair bir argüman alır
  - örneğin sınırlayıcı bir boşluksa, her kelimeyi ayırır, sınırlayıcı boş bir dizeyse, stringteki her karakteri ayırır.

her kelimeyi ayıran kod (noktalama işaretlerine de dikkat edildi):
```js
function splitify(str){ 
return str.split(/\W/);
}
splitify("Hello World,I-am code");
```

#### Combine an Array into a String Using the join Method

  - Join yöntemi, bir string (dize) oluşturmak için bir dizinin öğelerini birleştirmek için kullanılır.
  - Stringteki dizi öğelerini ayırmak için kullanılan sınırlayıcı için bir argüman alır.

```js
function sentensify(str) {
  return str.split(/\W/).join(" ");
}
sentensify("May-the-force-be-with-you");
```

#### Apply Functional Programming to Convert Strings to URL Slugs

Problem: Fill in the urlSlug function so it converts a string title and returns the hyphenated version for the URL. You can use any of the methods covered in this section, and don't use replace. Here are the requirements:
  - The input is a string with spaces and title-cased words
  - The output is a string with the spaces between words replaced by a hyphen (-)
  - The output should be all lower-cased letters
  - The output should not have any spaces
  
```js
function urlSlug(title) {
  return title
    .toLowerCase() // öncelikle bütün harfleri küçülttük
    .trim() // boşlukları sildik
    .split(/\s+/) // kelimeleri ayırıp stringi diziye çevirdik
    .join("-"); // kelimelerin arasına - koyarak diziyi stringe çevirdik
}
```
### arity
 Bir fonksiyonun aritesi, ihtiyaç duyduğu argüman sayısıdır.
 
 bu ile
 
 ```js
 function add(x) {
  return function(y) {
    return function(z) {
      return x + y + z;
    };
  };
}
add(10)(20)(30);
 ```
 
 bu
 ```js
   return y => z => x + y + z;
 ```
 
aynıdır.


