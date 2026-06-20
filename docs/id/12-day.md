# 📘 Hari 12

## Regular Expressions

Regular expression atau RegExp adalah bahasa pemrograman kecil yang membantu menemukan pola dalam data. RegExp dapat digunakan untuk memeriksa apakah suatu pola ada dalam berbagai tipe data. Untuk menggunakan RegExp di JavaScript, kita bisa menggunakan RegExp constructor atau mendeklarasikan pola RegExp menggunakan dua garis miring diikuti flag. Kita dapat membuat pola dengan dua cara.

Untuk mendeklarasikan string kita menggunakan tanda kutip tunggal, ganda, atau backtick. Untuk mendeklarasikan regular expression kita menggunakan dua garis miring dan flag opsional. Flag bisa berupa g, i, m, s, u atau y.

### Parameter RegExp

Regular expression menerima dua parameter. Satu pola pencarian yang wajib dan satu flag opsional.

#### Pola

Pola bisa berupa teks atau bentuk pola apa pun yang memiliki kesamaan tertentu. Misalnya kata spam dalam email bisa menjadi pola yang kita minati untuk dicari dalam email, atau format nomor telepon mungkin menjadi minat kita untuk dicari.

#### Flag

Flag adalah parameter opsional dalam regular expression yang menentukan jenis pencarian. Mari kita lihat beberapa flag:

- g: flag global yang berarti mencari pola di seluruh teks
- i: flag case insensitive (mencari baik huruf kecil maupun huruf besar)
- m: multiline

### Membuat pola dengan RegExp Constructor

Mendeklarasikan regular expression tanpa flag global dan flag case insensitive.

```js
// without flag
let pattern = 'love'
let regEx = new RegExp(pattern)
```

Mendeklarasikan regular expression dengan flag global dan flag case insensitive.

```js
let pattern = 'love'
let flag = 'gi'
let regEx = new RegExp(pattern, flag)
```

Mendeklarasikan pola regex menggunakan objek RegExp. Menulis pola dan flag di dalam RegExp constructor

```js
let regEx = new RegExp('love','gi')
```

### Membuat pola tanpa RegExp Constructor

Mendeklarasikan regular expression dengan flag global dan flag case insensitive.

```js
let regEx= /love/gi
```

Regular expression di atas sama dengan yang kita buat dengan RegExp constructor

```js
let regEx= new RegExp('love','gi')
```

### Metode Objek RegExp

Mari kita lihat beberapa metode RegExp

#### Menguji kecocokan

*test()*: Menguji kecocokan dalam string. Mengembalikan true atau false.

```js
const str = 'I love JavaScript'
const pattern = /love/
const result = pattern.test(str)
console.log(result)
```

```sh
true
```

#### Array yang berisi semua kecocokan

*match()*: Mengembalikan array yang berisi semua kecocokan, termasuk capturing groups, atau null jika tidak ada kecocokan.
Jika kita tidak menggunakan flag global, match() mengembalikan array yang berisi pola, indeks, input, dan group.

```js
const str = 'I love JavaScript'
const pattern = /love/
const result = str.match(pattern)
console.log(result)
```

```sh
["love", index: 2, input: "I love JavaScript", groups: undefined]
```

```js
const str = 'I love JavaScript'
const pattern = /love/g
const result = str.match(pattern)
console.log(result)
```

```sh
["love"]
```

*search()*: Menguji kecocokan dalam string. Mengembalikan indeks kecocokan, atau -1 jika pencarian gagal.

```js
const str = 'I love JavaScript'
const pattern = /love/g
const result = str.search(pattern)
console.log(result)
```

```sh
2
```

#### Mengganti substring

*replace()*: Melakukan pencarian kecocokan dalam string, dan mengganti substring yang cocok dengan substring pengganti.

```js
const txt = 'Python is the most beautiful language that a human begin has ever created.\
I recommend python for a first programming language'

matchReplaced = txt.replace(/Python|python/, 'JavaScript')
console.log(matchReplaced)
```

```sh
JavaScript is the most beautiful language that a human begin has ever created.I recommend python for a first programming language
```

```js
const txt = 'Python is the most beautiful language that a human begin has ever created.\
I recommend python for a first programming language'

matchReplaced = txt.replace(/Python|python/g, 'JavaScript')
console.log(matchReplaced)
```

```sh
JavaScript is the most beautiful language that a human begin has ever created.I recommend JavaScript for a first programming language
```

```js
const txt = 'Python is the most beautiful language that a human begin has ever created.\
I recommend python for a first programming language'

matchReplaced = txt.replace(/Python/gi, 'JavaScript')
console.log(matchReplaced)
```

```sh
JavaScript is the most beautiful language that a human begin has ever created.I recommend JavaScript for a first programming language
```

```js

const txt = '%I a%m te%%a%%che%r% a%n%d %% I l%o%ve te%ach%ing.\
T%he%re i%s n%o%th%ing as m%ore r%ewarding a%s e%duc%at%i%ng a%n%d e%m%p%ow%er%ing \
p%e%o%ple.\
I fo%und te%a%ching m%ore i%n%t%er%%es%ting t%h%an any other %jobs.\
D%o%es thi%s m%ot%iv%a%te %y%o%u to b%e a t%e%a%cher.'

matches = txt.replace(/%/g, '')
console.log(matches)  
```

```sh
I am teacher and  I love teaching.There is nothing as more rewarding as educating and empowering people.I found teaching more interesting than any other jobs.Does this motivate you to be a teacher.
```

* Kumpulan karakter
  * [a-c] berarti, a atau b atau c
  * [a-z] berarti, huruf apa pun dari a sampai z
  * [A-Z] berarti, karakter apa pun dari A sampai Z
  * [0-3] berarti, 0 atau 1 atau 2 atau 3
  * [0-9] berarti angka apa pun dari 0 sampai 9
  * [A-Za-z0-9] karakter apa pun dari a sampai z, A sampai Z, 0 sampai 9
* \\:  digunakan untuk escape karakter khusus
  * \d berarti: cocok jika string mengandung digit (angka dari 0-9)
  * \D berarti: cocok jika string tidak mengandung digit
* . : karakter apa pun kecuali karakter baris baru (\n)
* ^: dimulai dengan
  * r'^substring' contoh r'^love', kalimat yang dimulai dengan kata love
  * r'[^abc] berarti bukan a, bukan b, bukan c.
* $: diakhiri dengan
  * r'substring$' contoh r'love$', kalimat diakhiri dengan kata love
* *: nol kali atau lebih
  * r'[a]*' berarti a opsional atau bisa muncul berkali-kali.
* +: satu kali atau lebih
  * r'[a]+' berarti setidaknya sekali atau lebih
* ?: nol atau satu kali
  *  r'[a]?' berarti nol kali atau sekali
* \b: word boundary, cocok dengan awal atau akhir kata
* {3}: Tepat 3 karakter
* {3,}: Setidaknya 3 karakter
* {3,8}: 3 sampai 8 karakter
* |: Salah satu atau
  * r'apple|banana' berarti salah satu dari apple atau banana
* (): Capture dan group

![Regular Expression cheat sheet](../images/regex.png)

Mari kita gunakan contoh untuk memperjelas meta karakter di atas

### Kurung Siku (Square Bracket)

Mari kita gunakan kurung siku untuk menyertakan huruf kecil dan besar

```js
const pattern = '[Aa]pple' // this square bracket means either A or a
const txt = 'Apple and banana are fruits. An old cliche says an apple a day keeps the  doctor way has been replaced by a banana a day keeps the doctor far far away. '
const matches = txt.match(pattern)

console.log(matches)  
```

```sh
["Apple", index: 0, input: "Apple and banana are fruits. An old cliche says an apple a day keeps the  doctor way has been replaced by a banana a day keeps the doctor far far away.", groups: undefined]

```

```js
const pattern = /[Aa]pple/g // this square bracket means either A or a
const txt = 'Apple and banana are fruits. An old cliche says an apple a day a doctor way has been replaced by a banana a day keeps the doctor far far away. '
const matches = txt.match(pattern)

console.log(matches)  
```

```sh
["Apple", "apple"]
```

Jika kita ingin mencari banana, kita tulis polanya sebagai berikut:

```js
const pattern = /[Aa]pple|[Bb]anana/g // this square bracket mean either A or a
const txt = 'Apple and banana are fruits. An old cliche says an apple a day a doctor way has been replaced by a banana a day keeps the doctor far far away. Banana is easy to eat too.'
const matches = txt.match(pattern)

console.log(matches)  
```

```sh
["Apple", "banana", "apple", "banana", "Banana"]
```

Menggunakan kurung siku dan operator or, kita berhasil mengekstrak Apple, apple, Banana dan banana.

### Karakter Escape (\\) dalam RegExp

```js
const pattern = /\d/g  // d is a special character which means digits
const txt = 'This regular expression example was made in January 12,  2020.'
const matches = txt. match(pattern)

console.log(matches)  // ["1", "2", "2", "0", "2", "0"], this is not what we want
```

```js
const pattern = /\d+/g  // d is a special character which means digits
const txt = 'This regular expression example was made in January 12,  2020.'
const matches = txt. match(pattern)

console.log(matches)  // ["12", "2020"], this is not what we want
```

### Satu kali atau lebih (+)

```js
const pattern = /\d+/g  // d is a special character which means digits
const txt = 'This regular expression example was made in January 12,  2020.'
const matches = txt. match(pattern)
console.log(matches)  // ["12", "2020"], this is not what we want
```

### Titik (.)

```js
const pattern = /[a]./g  // this square bracket means a and . means any character except new line
const txt = 'Apple and banana are fruits'
const matches = txt.match(pattern)

console.log(matches)  // ["an", "an", "an", "a ", "ar"]
```

```js
const pattern = /[a].+/g  // . any character, + any character one or more times 
const txt = 'Apple and banana are fruits'
const matches = txt.match(pattern)

console.log(matches)  // ['and banana are fruits']
```

### Nol kali atau lebih (*)

Nol kali atau berkali-kali. Pola mungkin tidak muncul atau bisa muncul berkali-kali.

```js

const pattern = /[a].*/g  //. any character, + any character one or more times 
const txt = 'Apple and banana are fruits'
const matches = txt.match(pattern)

console.log(matches)  // ['and banana are fruits']

```

### Nol atau satu kali (?)

Nol atau satu kali. Pola mungkin tidak muncul atau bisa muncul sekali.

```js
const txt = 'I am not sure if there is a convention how to write the word e-mail.\
Some people write it email others may write it as Email or E-mail.'
const pattern = /[Ee]-?mail/g  // ? means optional
matches = txt.match(pattern)

console.log(matches)  // ["e-mail", "email", "Email", "E-mail"]

```

### Quantifier dalam RegExp

Kita dapat menentukan panjang substring yang kita cari dalam teks menggunakan kurung kurawal. Mari kita lihat cara menggunakan quantifier RegExp. Bayangkan kita tertarik pada substring yang panjangnya 4 karakter.

```js
const txt = 'This regular expression example was made in December 6,  2019.'
const pattern = /\b\w{4}\b/g  //  exactly four character words
const matches = txt.match(pattern)
console.log(matches)  //['This', 'made', '2019']
```

```js
const txt = 'This regular expression example was made in December 6,  2019.'
const pattern = /\b[a-zA-Z]{4}\b/g  //  exactly four character  words without numbers
const matches = txt.match(pattern)
console.log(matches)  //['This', 'made']
```

```js
const txt = 'This regular expression example was made in December 6,  2019.'
const pattern = /\d{4}/g  // a number and exactly four digits
const matches = txt.match(pattern)
console.log(matches)  // ['2019']
```

```js
const txt = 'This regular expression example was made in December 6,  2019.'
const pattern = /\d{1,4}/g   // 1 to 4
const matches = txt.match(pattern)
console.log(matches)  // ['6', '2019']
```

### Tanda ^

- Dimulai dengan
  
```js
const txt = 'This regular expression example was made in December 6,  2019.'
const pattern = /^This/ // ^ means starts with
const matches = txt.match(pattern)
console.log(matches)  // ['This']
```

- Negasi

```js
const txt = 'This regular expression example was made in December 6,  2019.'
const pattern = /[^A-Za-z,. ]+/g  // ^ in set character means negation, not A to Z, not a to z, no space, no comma no period
const matches = txt.match(pattern)
console.log(matches)  // ["6", "2019"]
```

### Pencocokan tepat

Harus memiliki ^ untuk awal dan $ untuk akhir.

```js
let pattern = /^[A-Z][a-z]{3,12}$/;
let name = 'Asabeneh';
let result = pattern.test(name)

console.log(result) // true
```

🌕 Anda telah melangkah jauh. Teruslah maju! Sekarang, Anda sangat bertenaga dengan kekuatan regular expression. Anda memiliki kemampuan untuk mengekstrak dan membersihkan segala jenis teks dan Anda dapat membuat makna dari data yang tidak terstruktur. Anda baru saja menyelesaikan tantangan hari ke-12 dan Anda 12 langkah lebih maju menuju kehebatan. Sekarang lakukan beberapa latihan untuk otak dan otot Anda.

## 💻 Latihan

### Latihan: Level 1

1. Hitung total pendapatan tahunan orang tersebut dari teks berikut. 'He earns 4000 euro from salary per month, 10000 euro annual bonus, 5500 euro online courses per month.'
2. Posisi beberapa partikel pada sumbu-x horizontal -12, -4, -3 dan  -1 di arah negatif, 0 di titik asal, 4 dan 8 di arah positif. Ekstrak angka-angka ini dan temukan jarak antara dua partikel terjauh.

```js
points = ['-1', '2', '-4', '-3', '-1', '0', '4', '8']
sortedPoints =  [-4, -3, -1, -1, 0, 2, 4, 8]
distance = 12
```

3. Tulis pola yang mengidentifikasi apakah sebuah string adalah variabel JavaScript yang valid

    ```sh
    is_valid_variable('first_name') # True
    is_valid_variable('first-name') # False
    is_valid_variable('1first_name') # False
    is_valid_variable('firstname') # True
    ```

### Latihan: Level 2

1. Tulis fungsi bernama *tenMostFrequentWords* yang mendapatkan sepuluh kata paling sering muncul dari sebuah string?

```js
paragraph = `I love teaching. If you do not love teaching what else can you love. I love Python if you do not love something which can give you all the capabilities to develop an application what else can you love.`
console.log(tenMostFrequentWords(paragraph))
```

```sh
[
  {word:'love', count:6},
  {word:'you', count:5},
  {word:'can', count:3},
  {word:'what', count:2},
  {word:'teaching', count:2},
  {word:'not', count:2},
  {word:'else', count:2},
  {word:'do', count:2},
  {word:'I', count:2},
  {word:'which', count:1},
  {word:'to', count:1},
  {word:'the', count:1},
  {word:'something', count:1},
  {word:'if', count:1},
  {word:'give', count:1},
  {word:'develop',count:1},
  {word:'capabilities',count:1},
  {word:'application', count:1},
  {word:'an',count:1},
  {word:'all',count:1},
  {word:'Python',count:1},
  {word:'If',count:1}
]
```

```js
console.log(tenMostFrequentWords(paragraph, 10))
```

```sh
[{word:'love', count:6},
{word:'you', count:5},
{word:'can', count:3},
{word:'what', count:2},
{word:'teaching', count:2},
{word:'not', count:2},
{word:'else', count:2},
{word:'do', count:2},
{word:'I', count:2},
{word:'which', count:1}
]
```

### Latihan: Level 3

1. Tulis fungsi yang membersihkan teks. Bersihkan teks berikut. Setelah dibersihkan, hitung tiga kata paling sering muncul dalam string.
  
```js
sentence = `%I $am@% a %tea@cher%, &and& I lo%#ve %tea@ching%;. There $is nothing; &as& mo@re rewarding as educa@ting &and& @emp%o@wering peo@ple. ;I found tea@ching m%o@re interesting tha@n any other %jo@bs. %Do@es thi%s mo@tivate yo@u to be a tea@cher!?`
console.log(cleanText(sentence))
```

```bash
I am a teacher and I love teaching There is nothing as more rewarding as educating and empowering people I found teaching more interesting than any other jobs Does this motivate you to be a teacher
```
2. Tulis fungsi yang menemukan kata paling sering muncul. Setelah dibersihkan, hitung tiga kata paling sering muncul dalam string.

  ```js
    console.log(mostFrequentWords(cleanedText))
    [{word:'I', count:3}, {word:'teaching', count:2}, {word:'teacher', count:2}]
  ```

🎉 SELAMAT! 🎉
