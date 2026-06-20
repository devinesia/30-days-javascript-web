# 📔 Hari 5 - Mantap Lanjut!

## Arrays

Beda sama variabel biasa, sebuah array bisa nyimpen _beberapa nilai_. Setiap nilai dalam array punya _indeks_, dan setiap indeks punya _referensi di alamat memori_. Setiap nilai bisa diakses pake _indeksnya_. Indeks dari array dimulai dari _nol_, dan indeks dari elemen terakhir adalah kurang satu dari panjang array.

Array adalah kumpulan tipe data berbeda yang terurut dan bisa diubah (modifiable). Array memungkinkan penyimpanan elemen duplikat dan tipe data yang beda-beda. Array bisa kosong, atau bisa punya nilai tipe data yang beda-beda. Cakep kan?

### Cara membuat array kosong

Di JavaScript, kita bisa bikin array dengan berbagai cara. Yuk kita lihat berbagai cara buat bikin array.
Umum banget pake _const_ daripada _let_ buat mendeklarasikan variabel array. Kalau kamu pake const, artinya kamu nggak pake nama variabel itu lagi.

- Pake Array constructor

```js
// sintaks
const arr = Array()
// atau
// let arr = new Array()
console.log(arr) // []
```

- Pake tanda kurung siku ([])

```js
// sintaks
// Ini adalah cara yang paling direkomendasikan untuk membuat daftar kosong
const arr = []
console.log(arr)
```

### Cara membuat array dengan nilai

Array dengan nilai awal. Kita pake properti _length_ buat nemuin panjang array.

```js
const numbers = [0, 3.14, 9.81, 37, 98.6, 100] // array of numbers
const fruits = ['banana', 'orange', 'mango', 'lemon'] // array of strings, fruits
const vegetables = ['Tomato', 'Potato', 'Cabbage', 'Onion', 'Carrot'] // array of strings, vegetables
const animalProducts = ['milk', 'meat', 'butter', 'yoghurt'] // array of strings, products
const webTechs = ['HTML', 'CSS', 'JS', 'React', 'Redux', 'Node', 'MongDB'] // array of web technologies
const countries = ['Finland', 'Denmark', 'Sweden', 'Norway', 'Iceland'] // array of strings, countries

// Cetak array dan panjangnya

console.log('Numbers:', numbers)
console.log('Number of numbers:', numbers.length)

console.log('Fruits:', fruits)
console.log('Number of fruits:', fruits.length)

console.log('Vegetables:', vegetables)
console.log('Number of vegetables:', vegetables.length)

console.log('Animal products:', animalProducts)
console.log('Number of animal products:', animalProducts.length)

console.log('Web technologies:', webTechs)
console.log('Number of web technologies:', webTechs.length)

console.log('Countries:', countries)
console.log('Number of countries:', countries.length)
```

```sh
Numbers: [0, 3.14, 9.81, 37, 98.6, 100]
Number of numbers: 6
Fruits: ['banana', 'orange', 'mango', 'lemon']
Number of fruits: 4
Vegetables: ['Tomato', 'Potato', 'Cabbage', 'Onion', 'Carrot']
Number of vegetables: 5
Animal products: ['milk', 'meat', 'butter', 'yoghurt']
Number of animal products: 4
Web technologies: ['HTML', 'CSS', 'JS', 'React', 'Redux', 'Node', 'MongDB']
Number of web technologies: 7
Countries: ['Finland', 'Estonia', 'Denmark', 'Sweden', 'Norway']
Number of countries: 5
```

- Array bisa punya item dengan tipe data beda-beda

```js
const arr = [
    'Asabeneh',
    250,
    true,
    { country: 'Finland', city: 'Helsinki' },
    { skills: ['HTML', 'CSS', 'JS', 'React', 'Python'] }
] // arr berisi tipe data yang berbeda
console.log(arr)
```

### Membuat array menggunakan split

Kayak yang udah kita lihat di bagian sebelumnya, kita bisa ngebelah string di posisi yang beda-beda, dan kita bisa ngubahnya jadi array. Yuk lihat contoh di bawah nih.

```js
let js = 'JavaScript'
const charsInJavaScript = js.split('')

console.log(charsInJavaScript) // ["J", "a", "v", "a", "S", "c", "r", "i", "p", "t"]

let companiesString = 'Facebook, Google, Microsoft, Apple, IBM, Oracle, Amazon'
const companies = companiesString.split(',')

console.log(companies) // ["Facebook", " Google", " Microsoft", " Apple", " IBM", " Oracle", " Amazon"]
let txt =
  'I love teaching and empowering people. I teach HTML, CSS, JS, React, Python.'
const words = txt.split(' ')

console.log(words)
// teks tersebut memiliki karakter khusus, pikirkan bagaimana Anda bisa hanya mendapatkan kata-katanya saja
// ["I", "love", "teaching", "and", "empowering", "people.", "I", "teach", "HTML,", "CSS,", "JS,", "React,", "Python"]
```

### Mengakses item array menggunakan indeks

Kita akses setiap elemen dalam array pake indeksnya. Indeks array dimulai dari 0. Gambar di bawah ini jelas nunjukin indeks setiap elemen dalam array.

![arr index](../images/array_index.png)

```js
const fruits = ['banana', 'orange', 'mango', 'lemon']
let firstFruit = fruits[0] // kita mengakses item pertama menggunakan indeksnya

console.log(firstFruit) // banana

secondFruit = fruits[1]
console.log(secondFruit) // orange

let lastFruit = fruits[3]
console.log(lastFruit) // lemon
// Indeks terakhir dapat dihitung sebagai berikut

let lastIndex = fruits.length - 1
lastFruit = fruits[lastIndex]

console.log(lastFruit)  // lemon
```

```js
const numbers = [0, 3.14, 9.81, 37, 98.6, 100]  // kumpulan angka

console.log(numbers.length)  // => untuk mengetahui ukuran array, yaitu 6
console.log(numbers)         // -> [0, 3.14, 9.81, 37, 98.6, 100]
console.log(numbers[0])      //  -> 0
console.log(numbers[5])      //  -> 100

let lastIndex = numbers.length - 1;
console.log(numbers[lastIndex]) // -> 100
```

```js
const webTechs = [
  'HTML',
  'CSS',
  'JavaScript',
  'React',
  'Redux',
  'Node',
  'MongoDB'
] // Daftar teknologi web

console.log(webTechs)        // semua item array
console.log(webTechs.length) // => untuk mengetahui ukuran array, yaitu 7
console.log(webTechs[0])     //  -> HTML
console.log(webTechs[6])     //  -> MongoDB

let lastIndex = webTechs.length - 1
console.log(webTechs[lastIndex]) // -> MongoDB
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
  'Kenya'
] // Daftar negara

console.log(countries)      // -> semua negara dalam array
console.log(countries[0])   //  -> Albania
console.log(countries[10])  //  -> Kenya

let lastIndex = countries.length - 1;
console.log(countries[lastIndex]) //  -> Kenya
```

```js
const shoppingCart = [
  'Milk',
  'Mango',
  'Tomato',
  'Potato',
  'Avocado',
  'Meat',
  'Eggs',
  'Sugar'
] // Daftar produk makanan

console.log(shoppingCart) // -> semua shoppingCart dalam array
console.log(shoppingCart[0]) //  -> Milk
console.log(shoppingCart[7]) //  -> Sugar

let lastIndex = shoppingCart.length - 1;
console.log(shoppingCart[lastIndex]) //  -> Sugar
```

### Memodifikasi elemen array

Array bersifat mutable (bisa dimodifikasi). Setelah array dibuat, kita bisa modifikasi isi elemen array.

```js
const numbers = [1, 2, 3, 4, 5]
numbers[0] = 10      // mengubah 1 pada indeks 0 menjadi 10
numbers[1] = 20      // mengubah 2 pada indeks 1 menjadi 20

console.log(numbers) // [10, 20, 3, 4, 5]

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
  'Kenya'
]

countries[0] = 'Afghanistan'  // Mengganti Albania dengan Afghanistan
let lastIndex = countries.length - 1
countries[lastIndex] = 'Korea' // Mengganti Kenya dengan Korea

console.log(countries)
```

```sh
["Afghanistan", "Bolivia", "Canada", "Denmark", "Ethiopia", "Finland", "Germany", "Hungary", "Ireland", "Japan", "Korea"]
```

### Metode untuk memanipulasi array

Ada berbagai metode buat manipulasi array. Nih beberapa metode yang tersedia buat nangani array: _Array, length, concat, indexOf, slice, splice, join, toString, includes, lastIndexOf, isArray, fill, push, pop, shift, unshift_

#### Array Constructor

Array: Buat bikin array.

```js
const arr = Array() // membuat array kosong
console.log(arr)

const eightEmptyValues = Array(8) // membuat delapan nilai kosong
console.log(eightEmptyValues) // [empty x 8]
```

#### Membuat nilai statis dengan fill

fill: Ngisi semua elemen array dengan nilai statis

```js
const arr = Array() // membuat array kosong
console.log(arr)

const eightXvalues = Array(8).fill('X') // membuat delapan elemen diisi dengan 'X'
console.log(eightXvalues) // ['X', 'X','X','X','X','X','X','X']

const eight0values = Array(8).fill(0) // membuat delapan elemen diisi dengan '0'
console.log(eight0values) // [0, 0, 0, 0, 0, 0, 0, 0]

const four4values = Array(4).fill(4) // membuat 4 elemen diisi dengan '4'
console.log(four4values) // [4, 4, 4, 4]
```

#### Menggabungkan array menggunakan concat

concat: Buat ngegabungin dua array.

```js
const firstList = [1, 2, 3]
const secondList = [4, 5, 6]
const thirdList = firstList.concat(secondList)

console.log(thirdList) // [1, 2, 3, 4, 5, 6]
```

```js
const fruits = ['banana', 'orange', 'mango', 'lemon']                 // array buah-buahan
const vegetables = ['Tomato', 'Potato', 'Cabbage', 'Onion', 'Carrot'] // array sayuran
const fruitsAndVegetables = fruits.concat(vegetables)                 // menggabungkan dua array

console.log(fruitsAndVegetables)
```

```sh
["banana", "orange", "mango", "lemon", "Tomato", "Potato", "Cabbage", "Onion", "Carrot"]
```

#### Mendapatkan panjang array

Length: Buat tahu ukuran array

```js
const numbers = [1, 2, 3, 4, 5]
console.log(numbers.length) // -> 5 adalah ukuran array
```

#### Mendapatkan indeks elemen dalam array

indexOf: Buat ngecek apakah suatu item ada di array. Kalau ada, dia ngembaliin indeksnya, kalau nggak ngembaliin -1.

```js
const numbers = [1, 2, 3, 4, 5]

console.log(numbers.indexOf(5)) // -> 4
console.log(numbers.indexOf(0)) // -> -1
console.log(numbers.indexOf(1)) // -> 0
console.log(numbers.indexOf(6)) // -> -1
```

Cek sebuah elemen apakah ada di array.

- Cek item di daftar
  
```js
// mari kita periksa apakah banana ada dalam array

const fruits = ['banana', 'orange', 'mango', 'lemon']
let index = fruits.indexOf('banana')  // 0

if(index === -1){
   console.log('This fruit does not exist in the array')  
} else {
    console.log('This fruit does exist in the array')
}
// This fruit does exist in the array

// kita juga bisa menggunakan ternary di sini
index === -1 ? console.log('This fruit does not exist in the array'): console.log('This fruit does exist in the array')

// mari kita periksa apakah avocado ada dalam array
let indexOfAvocado = fruits.indexOf('avocado')  // -1, jika elemen tidak ditemukan, indeksnya -1
if(indexOfAvocado === -1){
   console.log('This fruit does not exist in the array')  
} else {
    console.log('This fruit does exist in the array')
}
// This fruit does not exist in the array
```

#### Mendapatkan indeks terakhir elemen dalam array

lastIndexOf: Ngasih posisi item terakhir dalam array. Kalau ada, dia ngembaliin indeksnya, kalau nggak ngembaliin -1.

```js
const numbers = [1, 2, 3, 4, 5, 3, 1, 2]

console.log(numbers.lastIndexOf(2)) // 7
console.log(numbers.lastIndexOf(0)) // -1
console.log(numbers.lastIndexOf(1)) //  6
console.log(numbers.lastIndexOf(4)) //  3
console.log(numbers.lastIndexOf(6)) // -1
```

includes: Buat ngecek apakah suatu item ada di array. Kalau ada, dia ngembaliin true, kalau nggak ngembaliin false.

```js
const numbers = [1, 2, 3, 4, 5]

console.log(numbers.includes(5)) // true
console.log(numbers.includes(0)) // false
console.log(numbers.includes(1)) // true
console.log(numbers.includes(6)) // false

const webTechs = [
  'HTML',
  'CSS',
  'JavaScript',
  'React',
  'Redux',
  'Node',
  'MongoDB'
] // Daftar teknologi web

console.log(webTechs.includes('Node'))  // true
console.log(webTechs.includes('C'))     // false
```

#### Memeriksa array

Array.isArray: Buat ngecek apakah tipe data adalah array

```js
const numbers = [1, 2, 3, 4, 5]
console.log(Array.isArray(numbers)) // true

const number = 100
console.log(Array.isArray(number)) // false
```

#### Mengonversi array ke string

toString: Ngubah array ke string

```js
const numbers = [1, 2, 3, 4, 5]
console.log(numbers.toString()) // 1,2,3,4,5

const names = ['Asabeneh', 'Mathias', 'Elias', 'Brook']
console.log(names.toString()) // Asabeneh,Mathias,Elias,Brook
```

#### Menggabungkan elemen array

join: Dipake buat ngegabungin elemen-elemen array, argumen yang kita kasih di metode join bakal digabungin dalam array dan dikembaliin sebagai string. Secara default, dia ngegabungin dengan koma, tapi kita bisa ngasih parameter string berbeda yang bisa digabungin di antara item-item tersebut.

```js
const numbers = [1, 2, 3, 4, 5]
console.log(numbers.join()) // 1,2,3,4,5

const names = ['Asabeneh', 'Mathias', 'Elias', 'Brook']

console.log(names.join()) // Asabeneh,Mathias,Elias,Brook
console.log(names.join('')) //AsabenehMathiasEliasBrook
console.log(names.join(' ')) //Asabeneh Mathias Elias Brook
console.log(names.join(', ')) //Asabeneh, Mathias, Elias, Brook
console.log(names.join(' # ')) //Asabeneh # Mathias # Elias # Brook

const webTechs = [
  'HTML',
  'CSS',
  'JavaScript',
  'React',
  'Redux',
  'Node',
  'MongoDB'
] // Daftar teknologi web

console.log(webTechs.join())       // "HTML,CSS,JavaScript,React,Redux,Node,MongoDB"
console.log(webTechs.join(' # '))  // "HTML # CSS # JavaScript # React # Redux # Node # MongoDB"
```

#### Memotong elemen array

Slice: Buat motong beberapa item dalam rentang tertentu. Nerima dua parameter: posisi awal dan posisi akhir. Nggak nyertakan posisi akhir.

```js
  const numbers = [1,2,3,4,5]

  console.log(numbers.slice()) // -> menyalin semua item
  console.log(numbers.slice(0)) // -> menyalin semua item
  console.log(numbers.slice(0, numbers.length)) // menyalin semua item
  console.log(numbers.slice(1,4)) // -> [2,3,4] // tidak menyertakan posisi akhir
```

#### Metode splice dalam array

Splice: Nerima tiga parameter: Posisi awal, jumlah yang bakal dihapus, dan jumlah item yang bakal ditambahin.

```js
  const numbers = [1, 2, 3, 4, 5]
  numbers.splice()
  console.log(numbers)                // -> menghapus semua item

```

```js
  const numbers = [1, 2, 3, 4, 5]
	numbers.splice(0,1)
  console.log(numbers)            // menghapus item pertama
```

```js
  const numbers = [1, 2, 3, 4, 5, 6]
	numbers.splice(3, 3, 7, 8, 9)
  console.log(numbers.splice(3, 3, 7, 8, 9))  // -> [1, 2, 3, 7, 8, 9] //menghapus tiga item dan mengganti tiga item
```

#### Menambahkan item ke array menggunakan push

Push: nambahin item di akhir. Buat nambahin item ke akhir array yang udah ada, kita pake metode push.

```js
// sintaks
const arr  = ['item1', 'item2','item3']
arr.push('new item')
console.log(arr)
// ['item1', 'item2','item3','new item']
```

```js
const numbers = [1, 2, 3, 4, 5]
numbers.push(6)
console.log(numbers) // -> [1,2,3,4,5,6]

numbers.pop() // -> menghapus satu item dari akhir
console.log(numbers) // -> [1,2,3,4,5]
```

```js
let fruits = ['banana', 'orange', 'mango', 'lemon']
fruits.push('apple')
console.log(fruits)    // ['banana', 'orange', 'mango', 'lemon', 'apple']

fruits.push('lime')
console.log(fruits)   // ['banana', 'orange', 'mango', 'lemon', 'apple', 'lime']
```

#### Menghapus elemen akhir menggunakan pop

pop: Nghapus item di akhir.

```js
const numbers = [1, 2, 3, 4, 5]
numbers.pop() // -> menghapus satu item dari akhir
console.log(numbers) // -> [1,2,3,4]
```

#### Menghapus elemen dari awal

shift: Nghapus satu elemen array di awal array.

```js
const numbers = [1, 2, 3, 4, 5]
numbers.shift() // -> menghapus satu item dari awal
console.log(numbers) // -> [2,3,4,5]
```

#### Menambahkan elemen dari awal

unshift: Nambahin elemen array di awal array.

```js
const numbers = [1, 2, 3, 4, 5]
numbers.unshift(0) // -> menambahkan satu item dari awal
console.log(numbers) // -> [0,1,2,3,4,5]
```

#### Membalik urutan array

reverse: ngebalik urutan array.

```js
const numbers = [1, 2, 3, 4, 5]
numbers.reverse() // -> membalik urutan array
console.log(numbers) // [5, 4, 3, 2, 1]

numbers.reverse()
console.log(numbers) // [1, 2, 3, 4, 5]
```

#### Mengurutkan elemen dalam array

sort: ngatur elemen array dalam urutan menaik. Sort nerima fungsi callback, kita bakal lihat gimana pake sort dengan fungsi callback di bagian-bagian selanjutnya.

```js
const webTechs = [
  'HTML',
  'CSS',
  'JavaScript',
  'React',
  'Redux',
  'Node',
  'MongoDB'
]

webTechs.sort()
console.log(webTechs) // ["CSS", "HTML", "JavaScript", "MongoDB", "Node", "React", "Redux"]

webTechs.reverse() // setelah mengurutkan kita bisa membaliknya
console.log(webTechs) // ["Redux", "React", "Node", "MongoDB", "JavaScript", "HTML", "CSS"]
```

### Array dari array

Array bisa nyimpen tipe data yang beda-beda termasuk array itu sendiri. Yuk kita bikin array dari array.

```js
const firstNums = [1, 2, 3]
const secondNums = [1, 4, 9]

const arrayOfArray =  [[1, 2, 3], [1, 2, 3]]
console.log(arrayOfArray[0]) // [1, 2, 3]

 const frontEnd = ['HTML', 'CSS', 'JS', 'React', 'Redux']
 const backEnd = ['Node','Express', 'MongoDB']
 const fullStack = [frontEnd, backEnd]
 console.log(fullStack)   // [["HTML", "CSS", "JS", "React", "Redux"], ["Node", "Express", "MongoDB"]]
 console.log(fullStack.length)  // 2
 console.log(fullStack[0])  // ["HTML", "CSS", "JS", "React", "Redux"]
 console.log(fullStack[1]) // ["Node", "Express", "MongoDB"]
```

🌕 Kamu rajin banget dan udah mencapai banyak hal. Kamu baru aja nyelesein tantangan hari ke-5 dan kamu selangkah lebih maju menuju kehebatan. Gaskeun sekarang lakuin latihan buat otak dan otot kamu.

## 💻 Latihan

### Latihan: Level 1

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
  'Kenya'
]

const webTechs = [
  'HTML',
  'CSS',
  'JavaScript',
  'React',
  'Redux',
  'Node',
  'MongoDB'
]
```

1. Deklarasikan array _kosong_;
2. Deklarasikan array dengan lebih dari 5 jumlah elemen
3. Temuin panjang array kamu
4. Dapetin item pertama, item tengah, dan item terakhir dari array
5. Deklarasikan array bernama _mixedDataTypes_, masukin tipe data yang beda-beda di array dan temuin panjang array. Ukuran array harus lebih dari 5
6. Deklarasikan variabel array bernama itCompanies dan kasih nilai awal Facebook, Google, Microsoft, Apple, IBM, Oracle dan Amazon
7. Cetak array pake _console.log()_
8. Cetak jumlah perusahaan dalam array
9. Cetak perusahaan pertama, tengah, dan terakhir
10. Cetak setiap perusahaan
11. Ubah setiap nama perusahaan jadi huruf kapital satu per satu dan cetak
12. Cetak array seperti sebuah kalimat: Facebook, Google, Microsoft, Apple, IBM, Oracle dan Amazon adalah perusahaan IT besar.
13. Cek apakah perusahaan tertentu ada di array itCompanies. Kalau ada, kembalikan perusahaan tersebut, kalau nggak kembalikan perusahaan _tidak ditemukan_
14. Saring perusahaan yang punya lebih dari satu 'o' tanpa metode filter
15. Urutkan array pake metode _sort()_
16. Balik array pake metode _reverse()_
17. Potong 3 perusahaan pertama dari array
18. Potong 3 perusahaan terakhir dari array
19. Potong perusahaan IT tengah dari array
20. Hapus perusahaan IT pertama dari array
21. Hapus perusahaan IT tengah dari array
22. Hapus perusahaan IT terakhir dari array
23. Hapus semua perusahaan IT

### Latihan: Level 2

1. Bikin file countries.js terpisah dan simpen array countries ke file ini, bikin file terpisah web_techs.js dan simpen array webTechs ke file ini. Akses kedua file di file main.js
1. Pertama, hapus semua tanda baca dan ubah string jadi array, terus hitung jumlah kata di array

    ```js
    let text =
    'I love teaching and empowering people. I teach HTML, CSS, JS, React, Python.'
    console.log(words)
    console.log(words.length)
    ```

    ```sh
    ["I", "love", "teaching", "and", "empowering", "people", "I", "teach", "HTML", "CSS", "JS", "React", "Python"]
  
    13
    ```

1. Di keranjang belanja berikut, tambahin, hapus, edit item

    ```js
    const shoppingCart = ['Milk', 'Coffee', 'Tea', 'Honey']
    ```

   - tambahin 'Meat' di awal keranjang belanja kamu kalau belum ditambahin
   - tambahin Sugar di akhir keranjang belanja kamu kalau belum ditambahin
   - hapus 'Honey' kalau kamu alergi madu
   - ubah Tea jadi 'Green Tea'
1. Di array countries, cek apakah 'Ethiopia' ada di array. Kalau ada, cetak 'ETHIOPIA'. Kalau nggak ada, tambahin ke daftar countries.
1. Di array webTechs, cek apakah Sass ada di array dan kalau ada cetak 'Sass is a CSS preprocess'. Kalau nggak ada, tambahin Sass ke array dan cetak arraynya.
1. Gabungin dua variabel berikut dan simpen di variabel fullStack.

    ```js
    const frontEnd = ['HTML', 'CSS', 'JS', 'React', 'Redux']
    const backEnd = ['Node','Express', 'MongoDB']
  
    console.log(fullStack)
    ```

    ```sh
    ["HTML", "CSS", "JS", "React", "Redux", "Node", "Express", "MongoDB"]
    ```

### Latihan: Level 3

1. Nih array dari 10 usia siswa:

    ```js
    const ages = [19, 22, 19, 24, 20, 25, 26, 24, 25, 24]
    ```

    - Urutkan array dan temuin usia minimum dan maksimum
    - Temuin usia median (satu item tengah atau dua item tengah dibagi dua)
    - Temuin usia rata-rata (semua item dibagi jumlah item)
    - Temuin rentang usia (maksimum dikurangi minimum)
    - Bandingin nilai (min - rata-rata) dan (max - rata-rata), pake metode _abs()_
1. Potong sepuluh negara pertama dari [array countries](https://github.com/Asabeneh/30DaysOfJavaScript/tree/master/data/countries.js)
1. Temuin negara tengah di [array countries](https://github.com/Asabeneh/30DaysOfJavaScript/tree/master/data/countries.js)
2. Bagi array countries jadi dua array yang sama kalau jumlahnya genap. Kalau array countries nggak genap, satu negara lebih banyak buat setengah pertama.
  
🎉 SELAMAT ! 🎉
