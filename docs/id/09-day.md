# 📔 Hari 9

## Higher Order Function

Higher order function adalah fungsi yang menerima fungsi lain sebagai parameter atau mengembalikan fungsi sebagai nilai. Fungsi yang dilewatkan sebagai parameter disebut callback.

### Callback

Callback adalah fungsi yang dapat dilewatkan sebagai parameter ke fungsi lain. Lihat contoh di bawah ini.

```js
// fungsi callback, nama fungsinya bisa nama apa saja
const callback = (n) => {
  return n ** 2
}
​
// fungsi yang menerima fungsi lain sebagai callback
function cube(callback, n) {
  return callback(n) * n
}
​
console.log(cube(callback, 3))
```

### Fungsi yang Mengembalikan Fungsi

Higher order function mengembalikan fungsi sebagai nilai
​
```js
// Higher order function mengembalikan fungsi lain
const higherOrder = n => {
  const doSomething = m => {
    const doWhatEver = t => {
      return 2 * n + 3 * m + t
    }
    return doWhatEver
  }
  return doSomething
}
console.log(higherOrder(2)(3)(10))
```

Mari kita lihat di mana kita menggunakan fungsi callback. Misalnya metode _forEach_ menggunakan callback.

```js
const numbers = [1, 2, 3, 4, 5]
const sumArray = arr => {
  let sum = 0
  const callback = function(element) {
    sum += element
  }
  arr.forEach(callback)
  return sum

}
console.log(sumArray(numbers))
```

```sh
15
```

Contoh di atas dapat disederhanakan sebagai berikut:

```js
const numbers = [1, 2, 3, 4]
​
const sumArray = arr => {
  let sum = 0
  arr.forEach(function(element) {
    sum += element
  })
  return sum

}
console.log(sumArray(numbers))
```

```sh
15
```

### Mengatur Waktu (Setting time)

Di JavaScript kita dapat mengeksekusi beberapa aktivitas dalam interval waktu tertentu atau kita dapat menjadwalkan (menunggu) selama beberapa waktu untuk mengeksekusi beberapa aktivitas.

- setInterval
- setTimeout

#### Mengatur Interval menggunakan fungsi setInterval

Di JavaScript, kita menggunakan higher order function setInterval untuk melakukan suatu aktivitas secara terus-menerus dalam interval waktu tertentu. Metode global setInterval menerima fungsi callback dan durasi sebagai parameter. Durasi dalam milidetik dan callback akan selalu dipanggil dalam interval waktu tersebut.

```js
// sintaks
function callback() {
  // kode di sini
}
setInterval(callback, duration)
```

```js
function sayHello() {
  console.log('Hello')
}
setInterval(sayHello, 1000) // mencetak hello setiap detik, 1000ms adalah 1s
```

#### Mengatur waktu menggunakan setTimeout

Di JavaScript, kita menggunakan higher order function setTimeout untuk mengeksekusi suatu aksi pada suatu waktu di masa depan. Metode global setTimeout menerima fungsi callback dan durasi sebagai parameter. Durasi dalam milidetik dan callback menunggu selama jumlah waktu tersebut.

```js
// sintaks
function callback() {
  // kode di sini
}
setTimeout(callback, duration) // durasi dalam milidetik
```

```js
function sayHello() {
  console.log('Hello')
}
setTimeout(sayHello, 2000) // mencetak hello setelah menunggu selama 2 detik.
```

## Functional Programming

Alih-alih menulis loop biasa, versi terbaru JavaScript memperkenalkan banyak metode bawaan yang dapat membantu kita menyelesaikan masalah yang rumit. Semua metode bawaan menggunakan fungsi callback. Di bagian ini, kita akan melihat _forEach_, _map_, _filter_, _reduce_, _find_, _every_, _some_, dan _sort_.

### forEach

_forEach_: Mengiterasi elemen array. Kita menggunakan _forEach_ hanya dengan array. Metode ini menerima fungsi callback dengan parameter elemen, indeks, dan array itu sendiri. Indeks dan array bersifat opsional.

```js
arr.forEach(function (element, index, arr) {
  console.log(index, element, arr)
})
// Kode di atas dapat ditulis menggunakan arrow function
arr.forEach((element, index, arr) => {
  console.log(index, element, arr)
})
// Kode di atas dapat ditulis menggunakan arrow function dan explicit return
arr.forEach((element, index, arr) => console.log(index, element, arr))
```

```js
let sum = 0;
const numbers = [1, 2, 3, 4, 5];
numbers.forEach(num => console.log(num))
console.log(sum)
```

```sh
1
2
3
4
5
```

```js
let sum = 0;
const numbers = [1, 2, 3, 4, 5];
numbers.forEach(num => sum += num)

console.log(sum)
```

```sh
15
```

```js
const countries = ['Finland', 'Denmark', 'Sweden', 'Norway', 'Iceland']
countries.forEach((element) => console.log(element.toUpperCase()))
```

```sh
FINLAND
DENMARK
SWEDEN
NORWAY
ICELAND
```

### map

_map_: Mengiterasi elemen array dan memodifikasi elemen array. Metode ini menerima fungsi callback dengan parameter elemen, indeks, array dan mengembalikan array baru.

```js
const modifiedArray = arr.map(function (element, index, arr) {
  return element
})
```

```js
/*Arrow function dan explicit return
const modifiedArray = arr.map((element,index) => element);
*/
//Contoh
const numbers = [1, 2, 3, 4, 5]
const numbersSquare = numbers.map((num) => num * num)

console.log(numbersSquare)
```

```sh
[1, 4, 9, 16, 25]
```

```js
const names = ['Asabeneh', 'Mathias', 'Elias', 'Brook']
const namesToUpperCase = names.map((name) => name.toUpperCase())
console.log(namesToUpperCase)
```

```sh
['ASABENEH', 'MATHIAS', 'ELIAS', 'BROOK']
```

```js
const countries = [
  'Albania',
  'Bolivia',
  'Canada',
  'Denmark',
  'Ethiopia',
  'Finland',
  'Germany',
  'Hungary',
  'Ireland',
  'Japan',
  'Kenya',
]
const countriesToUpperCase = countries.map((country) => country.toUpperCase())
console.log(countriesToUpperCase)

/*
// Arrow function
const countriesToUpperCase = countries.map((country) => {
  return country.toUpperCase();
})
//Explicit return arrow function
const countriesToUpperCase = countries.map(country => country.toUpperCase());
*/
```

```sh
['ALBANIA', 'BOLIVIA', 'CANADA', 'DENMARK', 'ETHIOPIA', 'FINLAND', 'GERMANY', 'HUNGARY', 'IRELAND', 'JAPAN', 'KENYA']
```

```js
const countriesFirstThreeLetters = countries.map((country) =>
  country.toUpperCase().slice(0, 3)
)
```

```sh
 ["ALB", "BOL", "CAN", "DEN", "ETH", "FIN", "GER", "HUN", "IRE", "JAP", "KEN"]
```

### filter

_Filter_: Menyaring item yang memenuhi kondisi penyaringan dan mengembalikan array baru.

```js
//Filter countries containing land
const countriesContainingLand = countries.filter((country) =>
  country.includes('land')
)
console.log(countriesContainingLand)
```

```sh
['Finland', 'Ireland']
```

```js
const countriesEndsByia = countries.filter((country) => country.endsWith('ia'))
console.log(countriesEndsByia)
```

```sh
['Albania', 'Bolivia','Ethiopia']
```

```js
const countriesHaveFiveLetters = countries.filter(
  (country) => country.length === 5
)
console.log(countriesHaveFiveLetters)
```

```sh
['Japan', 'Kenya']
```

```js
const scores = [
  { name: 'Asabeneh', score: 95 },
   { name: 'Lidiya', score: 98 },
  { name: 'Mathias', score: 80 },
  { name: 'Elias', score: 50 },
  { name: 'Martha', score: 85 },
  { name: 'John', score: 100 },
]

const scoresGreaterEighty = scores.filter((score) => score.score > 80)
console.log(scoresGreaterEighty)
```

```sh
[{name: 'Asabeneh', score: 95}, { name: 'Lidiya', score: 98 },{name: 'Martha', score: 85},{name: 'John', score: 100}]
```

### reduce

_reduce_: Reduce menerima fungsi callback. Fungsi callback menerima accumulator, current, dan nilai awal opsional sebagai parameter dan mengembalikan satu nilai. Praktik yang baik adalah mendefinisikan nilai awal untuk nilai accumulator. Jika kita tidak menentukan parameter ini, secara default accumulator akan mendapatkan `nilai pertama` array. Jika array kita adalah _array kosong_, maka `Javascript` akan melemparkan error.

```js
arr.reduce((acc, cur) => {
  // beberapa operasi di sini sebelum mengembalikan nilai
 return 
}, initialValue)
```

```js
const numbers = [1, 2, 3, 4, 5]
const sum = numbers.reduce((acc, cur) => acc + cur, 0)

console.log(sum)
```

```js
15
```

### every

_every_: Memeriksa apakah semua elemen serupa dalam satu aspek. Mengembalikan boolean

```js
const names = ['Asabeneh', 'Mathias', 'Elias', 'Brook']
const areAllStr = names.every((name) => typeof name === 'string') // Apakah semuanya string?

console.log(areAllStr)
```

```sh
true
```

```js
const bools = [true, true, true, true]
const areAllTrue = bools.every((b) => b === true) // Apakah semuanya true? 

console.log(areAllTrue) // true
```

```sh
true

```

### find

_find_: Mengembalikan elemen pertama yang memenuhi kondisi

```js
const ages = [24, 22, 25, 32, 35, 18]
const age = ages.find((age) => age < 20)

console.log(age)
```

```js
18
```

```js
const names = ['Asabeneh', 'Mathias', 'Elias', 'Brook']
const result = names.find((name) => name.length > 7)
console.log(result)
```

```sh
Asabeneh
```

```js
const scores = [
  { name: 'Asabeneh', score: 95 },
  { name: 'Mathias', score: 80 },
  { name: 'Elias', score: 50 },
  { name: 'Martha', score: 85 },
  { name: 'John', score: 100 },
]

const score = scores.find((user) => user.score > 80)
console.log(score)
```

```sh
{ name: "Asabeneh", score: 95 }
```

### findIndex

_findIndex_: Mengembalikan posisi elemen pertama yang memenuhi kondisi

```js
const names = ['Asabeneh', 'Mathias', 'Elias', 'Brook']
const ages = [24, 22, 25, 32, 35, 18]

const result = names.findIndex((name) => name.length > 7)
console.log(result) // 0

const age = ages.findIndex((age) => age < 20)
console.log(age) // 5
```

### some

_some_: Memeriksa apakah beberapa elemen serupa dalam satu aspek. Mengembalikan boolean

```js
const names = ['Asabeneh', 'Mathias', 'Elias', 'Brook']
const bools = [true, true, true, true]

const areSomeTrue = bools.some((b) =>  b === true)

console.log(areSomeTrue) //true
```

```js
const areAllStr = names.some((name) => typeof name === 'number') // Apakah semuanya string ?
console.log(areAllStr) // false
```

### sort

_sort_: Metode sort mengatur elemen array secara ascending atau descending. Secara default, metode **_sort()_** mengurutkan nilai sebagai string. Ini bekerja dengan baik untuk item array string tetapi tidak untuk angka. Jika nilai angka diurutkan sebagai string, ini akan memberikan hasil yang salah. Metode sort memodifikasi array asli. Disarankan untuk menyalin data asli sebelum Anda mulai menggunakan metode _sort_.

#### Mengurutkan nilai string

```js
const products = ['Milk', 'Coffee', 'Sugar', 'Honey', 'Apple', 'Carrot']
console.log(products.sort()) // ['Apple', 'Carrot', 'Coffee', 'Honey', 'Milk', 'Sugar']
//Sekarang array products asli juga sudah terurut
```

#### Mengurutkan nilai numerik

Seperti yang Anda lihat pada contoh di bawah, 100 muncul pertama setelah diurutkan secara ascending. Sort mengonversi item ke string, karena '100' dan angka lainnya dibandingkan, 1 yang merupakan awal dari string '100' menjadi yang terkecil. Untuk menghindari ini, kita menggunakan fungsi callback pembanding di dalam metode sort, yang mengembalikan negatif, nol atau positif.

```js
const numbers = [9.81, 3.14, 100, 37]
// Menggunakan metode sort untuk mengurutkan item angka memberikan hasil yang salah. lihat di bawah
console.log(numbers.sort()) //[100, 3.14, 37, 9.81]
numbers.sort(function (a, b) {
  return a - b
})

console.log(numbers) // [3.14, 9.81, 37, 100]

numbers.sort(function (a, b) {
  return b - a
})
console.log(numbers) //[100, 37, 9.81, 3.14]
```

#### Mengurutkan Array Objek

Setiap kali kita mengurutkan objek dalam array, kita menggunakan kunci objek untuk membandingkan. Mari kita lihat contoh di bawah ini.

```js
objArr.sort(function (a, b) {
  if (a.key < b.key) return -1
  if (a.key > b.key) return 1
  return 0
})

// atau

objArr.sort(function (a, b) {
  if (a['key'] < b['key']) return -1
  if (a['key'] > b['key']) return 1
  return 0
})

const users = [
  { name: 'Asabeneh', age: 150 },
  { name: 'Brook', age: 50 },
  { name: 'Eyob', age: 100 },
  { name: 'Elias', age: 22 },
]
users.sort((a, b) => {
  if (a.age < b.age) return -1
  if (a.age > b.age) return 1
  return 0
})
console.log(users) // terurut ascending
// [{…}, {…}, {…}, {…}]
```

🌕 Anda hebat. Jangan pernah menyerah karena hal-hal besar membutuhkan waktu. Anda baru saja menyelesaikan tantangan hari ke-9 dan Anda selangkah lebih maju menuju kehebatan. Sekarang lakukan beberapa latihan untuk otak dan otot Anda.

## 💻 Latihan

### Latihan: Level 1

```js
const countries = ['Finland', 'Sweden', 'Denmark', 'Norway', 'IceLand']
const names = ['Asabeneh', 'Mathias', 'Elias', 'Brook']
const numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
const products = [
  { product: 'banana', price: 3 },
  { product: 'mango', price: 6 },
  { product: 'potato', price: ' ' },
  { product: 'avocado', price: 8 },
  { product: 'coffee', price: 10 },
  { product: 'tea', price: '' },
]
```

1. Jelaskan perbedaan antara **_forEach, map, filter, dan reduce_**.
2. Definisikan fungsi callback sebelum Anda menggunakannya di forEach, map, filter atau reduce.
3. Gunakan **_forEach_** untuk console.log setiap negara di array countries.
4. Gunakan **_forEach_** untuk console.log setiap nama di array names.
5. Gunakan **_forEach_** untuk console.log setiap angka di array numbers.
6. Gunakan **_map_** untuk membuat array baru dengan mengubah setiap negara menjadi huruf besar di array countries.
7. Gunakan **_map_** untuk membuat array panjang negara dari array countries.
8. Gunakan **_map_** untuk membuat array baru dengan mengubah setiap angka menjadi kuadrat di array numbers
9. Gunakan **_map_** untuk mengubah setiap nama menjadi huruf besar di array names
10. Gunakan **_map_** untuk memetakan array products ke harga yang sesuai.
11. Gunakan **_filter_** untuk menyaring negara yang mengandung **_land_**.
12. Gunakan **_filter_** untuk menyaring negara yang memiliki enam karakter.
13. Gunakan **_filter_** untuk menyaring negara yang mengandung enam huruf atau lebih di array countries.
14. Gunakan **_filter_** untuk menyaring negara yang dimulai dengan 'E';
15. Gunakan **_filter_** untuk menyaring hanya harga yang memiliki nilai.
16. Deklarasikan fungsi bernama getStringLists yang menerima array sebagai parameter dan kemudian mengembalikan array hanya dengan item string.
17. Gunakan **_reduce_** untuk menjumlahkan semua angka di array numbers.
18. Gunakan **_reduce_** untuk menggabungkan semua negara dan menghasilkan kalimat ini: **_Estonia, Finland, Sweden, Denmark, Norway, and IceLand are north European countries_**
19. Jelaskan perbedaan antara **_some_** dan **_every_**
20. Gunakan **_some_** untuk memeriksa apakah ada panjang nama yang lebih dari tujuh di array names
21. Gunakan **_every_** untuk memeriksa apakah semua negara mengandung kata land
22. Jelaskan perbedaan antara **_find_** dan **_findIndex_**.
23. Gunakan **_find_** untuk menemukan negara pertama yang hanya memiliki enam huruf di array countries
24. Gunakan **_findIndex_** untuk menemukan posisi negara pertama yang hanya memiliki enam huruf di array countries
25. Gunakan **_findIndex_** untuk menemukan posisi **_Norway_** jika tidak ada di array Anda akan mendapatkan -1.
26. Gunakan **_findIndex_** untuk menemukan posisi **_Russia_** jika tidak ada di array Anda akan mendapatkan -1.

### Latihan: Level 2

1. Temukan total harga produk dengan merantai dua atau lebih array iterator (mis. arr.map(callback).filter(callback).reduce(callback))
1. Temukan jumlah harga produk hanya menggunakan reduce reduce(callback))
1. Deklarasikan fungsi bernama **_categorizeCountries_** yang mengembalikan array negara yang memiliki beberapa pola umum (Anda dapat menemukan array countries di repositori ini sebagai countries.js (mis 'land', 'ia', 'island','stan')).
1. Buat fungsi yang mengembalikan array objek, yang berisi huruf dan jumlah kali huruf tersebut digunakan untuk memulai nama suatu negara.
1. Deklarasikan fungsi **_getFirstTenCountries_** dan kembalikan array sepuluh negara. Gunakan functional programming yang berbeda untuk bekerja pada array countries.js
1. Deklarasikan fungsi **_getLastTenCountries_** yang mengembalikan sepuluh negara terakhir di array countries.
1. Cari tahu _huruf_ mana yang paling _banyak_ digunakan sebagai awal nama negara dari array countries (mis. Finland, Fiji, France dll)

### Latihan: Level 3

1. Gunakan informasi countries, di folder data. Urutkan negara berdasarkan nama, berdasarkan ibu kota, berdasarkan populasi
1. \*\*\* Temukan 10 bahasa yang paling banyak digunakan:

   ````js
   // Output Anda seharusnya terlihat seperti ini
   console.log(mostSpokenLanguages(countries, 10))
   [
   {country: 'English',count:91},
   {country: 'French',count:45},
   {country: 'Arabic',count:25},
   {country: 'Spanish',count:24},
   {country:'Russian',count:9},
   {country:'Portuguese', count:9},
   {country:'Dutch',count:8},
   {country:'German',count:7},
   {country:'Chinese',count:5},
   {country:'Swahili',count:4}
   ]

   // Output Anda seharusnya terlihat seperti ini
   console.log(mostSpokenLanguages(countries, 3))
   [
   {country: 'English',count: 91},
   {country: 'French',count: 45},
   {country: 'Arabic',count: 25},
   ]```

   ````

2. \*\*\* Gunakan file countries_data.js buat fungsi yang membuat sepuluh negara dengan populasi terbanyak

   ````js
   console.log(mostPopulatedCountries(countries, 10))

   [
   {country: 'China', population: 1377422166},
   {country: 'India', population: 1295210000},
   {country: 'United States of America', population: 323947000},
   {country: 'Indonesia', population: 258705000},
   {country: 'Brazil', population: 206135893},
   {country: 'Pakistan', population: 194125062},
   {country: 'Nigeria', population: 186988000},
   {country: 'Bangladesh', population: 161006790},
   {country: 'Russian Federation', population: 146599183},
   {country: 'Japan', population: 126960000}
   ]

   console.log(mostPopulatedCountries(countries, 3))
   [
   {country: 'China', population: 1377422166},
   {country: 'India', population: 1295210000},
   {country: 'United States of America', population: 323947000}
   ]
   ```

   ````

3. \*\*\* Cobalah untuk mengembangkan program yang menghitung ukuran tendensi sentral suatu sampel (mean, median, mode) dan ukuran variabilitas (range, variance, standar deviasi). Selain ukuran-ukuran tersebut, temukan min, max, count, percentile, dan distribusi frekuensi dari sampel. Anda dapat membuat objek bernama statistics dan membuat semua fungsi yang melakukan perhitungan statistik sebagai metode untuk objek statistics. Lihat output di bawah ini.

   ```js
   const ages = [31, 26, 34, 37, 27, 26, 32, 32, 26, 27, 27, 24, 32, 33, 27, 25, 26, 38, 37, 31, 34, 24, 33, 29, 26]

   console.log('Count:', statistics.count()) // 25
   console.log('Sum: ', statistics.sum()) // 744
   console.log('Min: ', statistics.min()) // 24
   console.log('Max: ', statistics.max()) // 38
   console.log('Range: ', statistics.range() // 14
   console.log('Mean: ', statistics.mean()) // 30
   console.log('Median: ',statistics.median()) // 29
   console.log('Mode: ', statistics.mode()) // {'mode': 26, 'count': 5}
   console.log('Variance: ',statistics.var()) // 17.5
   console.log('Standard Deviation: ', statistics.std()) // 4.2
   console.log('Variance: ',statistics.var()) // 17.5
   console.log('Frequency Distribution: ',statistics.freqDist()) # [(20.0, 26), (16.0, 27), (12.0, 32), (8.0, 37), (8.0, 34), (8.0, 33), (8.0, 31), (8.0, 24), (4.0, 38), (4.0, 29), (4.0, 25)]
   ```

   ```sh
   console.log(statistics.describe())
   Count: 25
   Sum:  744
   Min:  24
   Max:  38
   Range:  14
   Mean:  30
   Median:  29
   Mode:  (26, 5)
   Variance:  17.5
   Standard Deviation:  4.2
   Frequency Distribution: [(20.0, 26), (16.0, 27), (12.0, 32), (8.0, 37), (8.0, 34), (8.0, 33), (8.0, 31), (8.0, 24), (4.0, 38), (4.0, 29), (4.0, 25)]
   ```

🎉 SELAMAT ! 🎉
