# 📔 Hari 7

## Fungsi (Function)

Sejauh ini kita telah melihat banyak fungsi bawaan JavaScript. Di bagian ini, kita akan fokus pada fungsi kustom. Apa itu fungsi? Sebelum kita mulai membuat fungsi, mari pahami apa itu fungsi dan mengapa kita membutuhkan fungsi?

Fungsi adalah blok kode atau pernyataan pemrograman yang dapat digunakan kembali yang dirancang untuk melakukan tugas tertentu.
Fungsi dideklarasikan dengan kata kunci function diikuti oleh nama, diikuti oleh tanda kurung (). Tanda kurung dapat menerima parameter. Jika sebuah fungsi menerima parameter, fungsi akan dipanggil dengan argumen. Fungsi juga dapat memiliki parameter default. Untuk menyimpan data ke suatu fungsi, fungsi harus mengembalikan tipe data tertentu. Untuk mendapatkan nilainya kita memanggil atau menjalankan (invoke) fungsi.
Fungsi membuat kode menjadi:

- bersih dan mudah dibaca
- dapat digunakan kembali
- mudah diuji

Fungsi dapat dideklarasikan atau dibuat dengan beberapa cara:

- _Fungsi Deklarasi (Declaration function)_
- _Fungsi Ekspresi (Expression function)_
- _Fungsi Anonim (Anonymous function)_
- _Fungsi Panah (Arrow function)_

### Deklarasi Fungsi

Mari kita lihat cara mendeklarasikan fungsi dan cara memanggil fungsi.

```js
// mendeklarasikan fungsi tanpa parameter
function functionName() {
  // kode di sini
}
functionName() // memanggil fungsi dengan namanya dan dengan tanda kurung
```

### Fungsi tanpa parameter dan return

Fungsi dapat dideklarasikan tanpa parameter.

**Contoh:**

```js
// fungsi tanpa parameter, fungsi yang membuat bilangan kuadrat
function square() {
  let num = 2
  let sq = num * num
  console.log(sq)
}

square() // 4

// fungsi tanpa parameter
function addTwoNumbers() {
  let numOne = 10
  let numTwo = 20
  let sum = numOne + numTwo

  console.log(sum)
}

addTwoNumbers() // fungsi harus dipanggil dengan namanya untuk dieksekusi 
```

```js
  function printFullName (){
      let firstName = 'Asabeneh'
      let lastName = 'Yetayeh'
      let space = ' '
      let fullName = firstName + space + lastName
      console.log(fullName)
}

printFullName() // memanggil fungsi
```

### Fungsi yang mengembalikan nilai

Fungsi juga dapat mengembalikan nilai, jika sebuah fungsi tidak mengembalikan nilai, nilai fungsi tersebut adalah undefined. Mari kita tulis fungsi-fungsi di atas dengan return. Mulai sekarang, kita mengembalikan nilai ke fungsi alih-alih mencetaknya.

```js
function printFullName (){
      let firstName = 'Asabeneh'
      let lastName = 'Yetayeh'
      let space = ' '
      let fullName = firstName + space + lastName
      return fullName
}
console.log(printFullName())
```

```js

  function addTwoNumbers() {
      let numOne = 2
      let numTwo = 3
      let total = numOne + numTwo
      return total

  }

console.log(addTwoNumbers())
```

### Fungsi dengan parameter

Dalam fungsi kita dapat melewatkan berbagai tipe data (number, string, boolean, object, function) sebagai parameter.

```js
// fungsi dengan satu parameter
function functionName(parm1) {
  //kode di sini
}
functionName(parm1) // saat memanggil atau menjalankan, dibutuhkan satu argumen

function areaOfCircle(r) {
  let area = Math.PI * r * r
  return area
}

console.log(areaOfCircle(10)) // harus dipanggil dengan satu argumen

function square(number) {
  return number * number
}

console.log(square(10))
```

### Fungsi dengan dua parameter

```js
// fungsi dengan dua parameter
function functionName(parm1, parm2) {
  //kode di sini
}
functionName(parm1, parm2) // saat memanggil atau menjalankan, dibutuhkan dua argumen
// Fungsi tanpa parameter tidak menerima input, jadi mari buat fungsi dengan parameter
function sumTwoNumbers(numOne, numTwo) {
  let sum = numOne + numTwo
  console.log(sum)
}
sumTwoNumbers(10, 20) // memanggil fungsi
// Jika fungsi tidak mengembalikan nilai, fungsi tidak menyimpan data, jadi harus mengembalikan nilai

function sumTwoNumbers(numOne, numTwo) {
  let sum = numOne + numTwo
  return sum
}

console.log(sumTwoNumbers(10, 20))
function printFullName(firstName, lastName) {
  return `${firstName} ${lastName}`
}
console.log(printFullName('Asabeneh', 'Yetayeh'))
```

### Fungsi dengan banyak parameter

```js
// fungsi dengan banyak parameter
function functionName(parm1, parm2, parm3,...){
  //kode di sini
}
functionName(parm1,parm2,parm3,...) // saat memanggil atau menjalankan, dibutuhkan tiga argumen


// fungsi ini menerima array sebagai parameter dan menjumlahkan angka-angka dalam array
function sumArrayValues(arr) {
  let sum = 0;
  for (let i = 0; i < arr.length; i++) {
    sum = sum + arr[i];
  }
  return sum;
}
const numbers = [1, 2, 3, 4, 5];
    //memanggil fungsi
console.log(sumArrayValues(numbers));


    const areaOfCircle = (radius) => {
      let area = Math.PI * radius * radius;
      return area;
    }
console.log(areaOfCircle(10))

```

### Fungsi dengan jumlah parameter tak terbatas

Terkadang kita tidak tahu berapa banyak argumen yang akan diberikan pengguna. Oleh karena itu, kita harus tahu cara menulis fungsi yang dapat menerima jumlah argumen tak terbatas. Caranya memiliki perbedaan signifikan antara fungsi deklarasi (fungsi biasa) dan arrow function. Mari kita lihat contoh pada fungsi deklarasi dan arrow function.

#### Jumlah parameter tak terbatas di fungsi biasa

Fungsi deklarasi menyediakan objek mirip array bernama arguments yang ter-scope ke fungsi. Apa pun yang kita lewatkan sebagai argumen dalam fungsi dapat diakses dari objek arguments di dalam fungsi. Mari kita lihat contohnya

```js
// Mari kita akses objek arguments
​
function sumAllNums() {
  console.log(arguments)
}

sumAllNums(1, 2, 3, 4)
// Arguments(4) [1, 2, 3, 4, callee: ƒ, Symbol(Symbol.iterator): ƒ]

```

```js
// deklarasi fungsi
​
function sumAllNums() {
  let sum = 0
  for (let i = 0; i < arguments.length; i++) {
    sum += arguments[i]
  }
  return sum
}

console.log(sumAllNums(1, 2, 3, 4)) // 10
console.log(sumAllNums(10, 20, 13, 40, 10))  // 93
console.log(sumAllNums(15, 20, 30, 25, 10, 33, 40))  // 173
```

#### Jumlah parameter tak terbatas di arrow function

Arrow function tidak memiliki objek arguments yang ter-scope ke fungsi. Untuk mengimplementasikan fungsi yang menerima jumlah argumen tak terbatas di arrow function, kita menggunakan spread operator diikuti dengan nama parameter apa pun. Apa pun yang kita lewatkan sebagai argumen dalam fungsi dapat diakses sebagai array di arrow function. Mari kita lihat contohnya

```js
// Mari kita akses objek arguments
​
const sumAllNums = (...args) => {
  // console.log(arguments), objek arguments tidak ditemukan di arrow function
  // sebagai gantinya kita menggunakan parameter diikuti spread operator (...)
  console.log(args)
}

sumAllNums(1, 2, 3, 4)
// [1, 2, 3, 4]

```

```js
// deklarasi fungsi
​
const sumAllNums = (...args) => {
  let sum = 0
  for (const element of args) {
    sum += element
  }
  return sum
}

console.log(sumAllNums(1, 2, 3, 4)) // 10
console.log(sumAllNums(10, 20, 13, 40, 10))  // 93
console.log(sumAllNums(15, 20, 30, 25, 10, 33, 40))  // 173
```

### Fungsi Anonim (Anonymous Function)

Fungsi anonim atau fungsi tanpa nama

```js
const anonymousFun = function() {
  console.log(
    'I am an anonymous function and my value is stored in anonymousFun'
  )
}
```

### Fungsi Ekspresi (Expression Function)

Fungsi ekspresi adalah fungsi anonim. Setelah kita membuat fungsi tanpa nama dan menetapkannya ke variabel. Untuk mengembalikan nilai dari fungsi kita harus memanggil variabelnya. Lihat contoh di bawah ini.

```js

// Function expression
const square = function(n) {
  return n * n
}

console.log(square(2)) // -> 4
```

### Fungsi yang Memanggil Dirinya Sendiri (Self Invoking Functions)

Self invoking functions adalah fungsi anonim yang tidak perlu dipanggil untuk mengembalikan nilai.

```js
(function(n) {
  console.log(n * n)
})(2) // 4, tetapi alih-alih hanya mencetak, jika kita ingin mengembalikan dan menyimpan data, kita lakukan seperti di bawah ini

let squaredNum = (function(n) {
  return n * n
})(10)

console.log(squaredNum)
```

### Arrow Function

Arrow function adalah alternatif untuk menulis fungsi, namun fungsi deklarasi dan arrow function memiliki beberapa perbedaan kecil.

Arrow function menggunakan tanda panah (arrow) alih-alih kata kunci *function* untuk mendeklarasikan fungsi. Mari kita lihat fungsi deklarasi dan arrow function.

```js
// Ini cara kita menulis fungsi normal atau deklarasi
// Mari kita ubah fungsi deklarasi ini menjadi arrow function
function square(n) {
  return n * n
}

console.log(square(2)) // 4

const square = n => {
  return n * n
}

console.log(square(2))  // -> 4

// jika kita hanya memiliki satu baris di blok kode, dapat ditulis sebagai berikut, explicit return
const square = n => n * n  // -> 4
```

```js
const changeToUpperCase = arr => {
  const newArr = []
  for (const element of arr) {
    newArr.push(element.toUpperCase())
  }
  return newArr
}

const countries = ['Finland', 'Sweden', 'Norway', 'Denmark', 'Iceland']
console.log(changeToUpperCase(countries))

// ["FINLAND", "SWEDEN", "NORWAY", "DENMARK", "ICELAND"]
```

```js
const printFullName = (firstName, lastName) => {
  return `${firstName} ${lastName}`
}

console.log(printFullName('Asabeneh', 'Yetayeh'))
```

Fungsi di atas hanya memiliki pernyataan return, oleh karena itu, kita dapat secara eksplisit mengembalikannya sebagai berikut.

```js
const printFullName = (firstName, lastName) => `${firstName} ${lastName}`

console.log(printFullName('Asabeneh', 'Yetayeh'))
```

### Fungsi dengan parameter default

Terkadang kita memberikan nilai default ke parameter, ketika kita menjalankan fungsi jika kita tidak melewatkan argumen, nilai default akan digunakan. Baik fungsi deklarasi maupun arrow function dapat memiliki nilai default.

```js
// sintaks
// Mendeklarasikan fungsi
function functionName(param = value) {
  //kode
}

// Memanggil fungsi
functionName()
functionName(arg)
```

**Contoh:**

```js
function greetings(name = 'Peter') {
  let message = `${name}, welcome to 30 Days Of JavaScript!`
  return message
}

console.log(greetings())
console.log(greetings('Asabeneh'))
```

```js
function generateFullName(firstName = 'Asabeneh', lastName = 'Yetayeh') {
  let space = ' '
  let fullName = firstName + space + lastName
  return fullName
}

console.log(generateFullName())
console.log(generateFullName('David', 'Smith'))
```

```js
function calculateAge(birthYear, currentYear = 2019) {
  let age = currentYear - birthYear
  return age
}

console.log('Age: ', calculateAge(1819))
```

```js
function weightOfObject(mass, gravity = 9.81) {
  let weight = mass * gravity + ' N' // nilainya harus diubah menjadi string terlebih dahulu
  return weight
}

console.log('Weight of an object in Newton: ', weightOfObject(100)) // 9.81 gravitasi di permukaan Bumi
console.log('Weight of an object in Newton: ', weightOfObject(100, 1.62)) // gravitasi di permukaan Bulan
```

Mari kita lihat cara menulis fungsi-fungsi di atas dengan arrow function

```js
// sintaks
// Mendeklarasikan fungsi
const functionName = (param = value) => {
  //kode
}

// Memanggil fungsi
functionName()
functionName(arg)
```

**Contoh:**

```js
const greetings = (name = 'Peter') => {
  let message = name + ', welcome to 30 Days Of JavaScript!'
  return message
}

console.log(greetings())
console.log(greetings('Asabeneh'))
```

```js
const generateFullName = (firstName = 'Asabeneh', lastName = 'Yetayeh') => {
  let space = ' '
  let fullName = firstName + space + lastName
  return fullName
}

console.log(generateFullName())
console.log(generateFullName('David', 'Smith'))
```

```js

const calculateAge = (birthYear, currentYear = 2019) => currentYear - birthYear
console.log('Age: ', calculateAge(1819))
```

```js
const weightOfObject = (mass, gravity = 9.81) => mass * gravity + ' N'
  
console.log('Weight of an object in Newton: ', weightOfObject(100)) // 9.81 gravitasi di permukaan Bumi
console.log('Weight of an object in Newton: ', weightOfObject(100, 1.62)) // gravitasi di permukaan Bulan
```

### Fungsi Deklarasi vs Arrow Function

Akan dibahas di bagian lain.

🌕 Anda adalah bintang yang sedang naik daun, sekarang Anda sudah mengenal fungsi. Sekarang, Anda sudah terisi penuh dengan kekuatan fungsi. Anda baru saja menyelesaikan tantangan hari ke-7 dan Anda selangkah lebih maju menuju kehebatan. Sekarang lakukan beberapa latihan untuk otak dan otot Anda.



## 💻 Latihan

### Latihan: Level 1

1. Deklarasikan fungsi _fullName_ dan cetak nama lengkap Anda.
2. Deklarasikan fungsi _fullName_ dan sekarang fungsi tersebut menerima firstName, lastName sebagai parameter dan mengembalikan nama lengkap Anda.
3. Deklarasikan fungsi _addNumbers_ yang menerima dua parameter dan mengembalikan jumlahnya.
4. Luas persegi panjang dihitung sebagai berikut: _area = panjang x lebar_. Tulis fungsi yang menghitung _areaOfRectangle_.
5. Keliling persegi panjang dihitung sebagai berikut: _perimeter = 2 x (panjang + lebar)_. Tulis fungsi yang menghitung _perimeterOfRectangle_.
6. Volume balok dihitung sebagai berikut: _volume = panjang x lebar x tinggi_. Tulis fungsi yang menghitung _volumeOfRectPrism_.
7. Luas lingkaran dihitung sebagai berikut: _area = π x r x r_. Tulis fungsi yang menghitung _areaOfCircle_
8. Keliling lingkaran dihitung sebagai berikut: _circumference = 2πr_. Tulis fungsi yang menghitung _circumOfCircle_
9. Massa jenis suatu zat dihitung sebagai berikut: _density = massa / volume_. Tulis fungsi yang menghitung _density_.
10. Kecepatan dihitung dengan membagi total jarak yang ditempuh oleh benda bergerak dibagi dengan total waktu yang dibutuhkan. Tulis fungsi yang menghitung kecepatan benda bergerak, _speed_.
11. Berat suatu zat dihitung sebagai berikut: _weight = massa x gravitasi_. Tulis fungsi yang menghitung _weight_.
12. Suhu dalam oC dapat dikonversi ke oF menggunakan rumus ini: _oF = (oC x 9/5) + 32_. Tulis fungsi yang mengonversi oC ke oF _convertCelsiusToFahrenheit_.
13. Indeks massa tubuh (BMI) dihitung sebagai berikut: _bmi = berat dalam Kg / (tinggi x tinggi) dalam m2_. Tulis fungsi yang menghitung _bmi_. BMI digunakan untuk secara luas mendefinisikan berbagai kelompok berat badan pada orang dewasa berusia 20 tahun atau lebih. Periksa apakah seseorang _underweight, normal, overweight_ atau _obese_ berdasarkan informasi yang diberikan di bawah ini.

    - Kelompok yang sama berlaku untuk pria dan wanita.
    - _Underweight_: BMI kurang dari 18.5
    - _Normal weight_: BMI 18.5 sampai 24.9
    - _Overweight_: BMI 25 sampai 29.9
    - _Obese_: BMI 30 atau lebih

14. Tulis fungsi bernama _checkSeason_, fungsi ini menerima parameter bulan dan mengembalikan musim: Autumn, Winter, Spring atau Summer.
15. Math.max mengembalikan argumen terbesarnya. Tulis fungsi findMax yang menerima tiga argumen dan mengembalikan nilai maksimumnya tanpa menggunakan metode Math.max.

    ```js
    console.log(findMax(0, 10, 5))
    10
    console.log(findMax(0, -10, -2))
    0
    ```
  
### Latihan: Level 2

1. Persamaan linear dihitung sebagai berikut: _ax + by + c = 0_. Tulis fungsi yang menghitung nilai persamaan linear, _solveLinEquation_.
1. Persamaan kuadrat dihitung sebagai berikut: _ax2 + bx + c = 0_. Tulis fungsi yang menghitung nilai atau nilai-nilai persamaan kuadrat, _solveQuadEquation_.

    ```js
    console.log(solveQuadratic()) // {0}
    console.log(solveQuadratic(1, 4, 4)) // {-2}
    console.log(solveQuadratic(1, -1, -2)) // {2, -1}
    console.log(solveQuadratic(1, 7, 12)) // {-3, -4}
    console.log(solveQuadratic(1, 0, -4)) //{2, -2}
    console.log(solveQuadratic(1, -1, 0)) //{1, 0}
    ```

1. Deklarasikan fungsi bernama _printArray_. Fungsi ini menerima array sebagai parameter dan mencetak setiap nilai dari array.
1. Tulis fungsi bernama _showDateTime_ yang menampilkan waktu dalam format ini: 08/01/2020 04:08 menggunakan objek Date.

    ```sh
    showDateTime()
    08/01/2020 04:08
    ```

1. Deklarasikan fungsi bernama _swapValues_. Fungsi ini menukar nilai x ke y.

    ```js
    swapValues(3, 4) // x => 4, y=>3
    swapValues(4, 5) // x = 5, y = 4
    ```

1. Deklarasikan fungsi bernama _reverseArray_. Fungsi ini menerima array sebagai parameter dan mengembalikan kebalikan dari array (jangan gunakan metode).

    ```js
    console.log(reverseArray([1, 2, 3, 4, 5]))
    //[5, 4, 3, 2, 1]
    console.log(reverseArray(['A', 'B', 'C']))
    //['C', 'B', 'A']
    ```

1. Deklarasikan fungsi bernama _capitalizeArray_. Fungsi ini menerima array sebagai parameter dan mengembalikan array yang dikapitalisasi.
1. Deklarasikan fungsi bernama _addItem_. Fungsi ini menerima parameter item dan mengembalikan array setelah menambahkan item
1. Deklarasikan fungsi bernama _removeItem_. Fungsi ini menerima parameter indeks dan mengembalikan array setelah menghapus item
1. Deklarasikan fungsi bernama _sumOfNumbers_. Fungsi ini menerima parameter angka dan menjumlahkan semua angka dalam rentang tersebut.
1. Deklarasikan fungsi bernama _sumOfOdds_. Fungsi ini menerima parameter angka dan menjumlahkan semua angka ganjil dalam rentang tersebut.
1. Deklarasikan fungsi bernama _sumOfEven_. Fungsi ini menerima parameter angka dan menjumlahkan semua angka genap dalam rentang tersebut.
1. Deklarasikan fungsi bernama evensAndOdds. Fungsi ini menerima bilangan bulat positif sebagai parameter dan menghitung jumlah bilangan genap dan ganjil dalam angka tersebut.

    ```sh
    evensAndOdds(100);
    The number of odds are 50.
    The number of evens are 51.
    ```

1. Tulis fungsi yang menerima sejumlah argumen dan mengembalikan jumlah dari argumen-argumen tersebut

    ```js
    sum(1, 2, 3) // -> 6
    sum(1, 2, 3, 4) // -> 10
    ```

1. Tulis fungsi yang menghasilkan _randomUserIp_.
1. Tulis fungsi yang menghasilkan _randomMacAddress_
1. Deklarasikan fungsi bernama _randomHexaNumberGenerator_. Ketika fungsi ini dipanggil, fungsi ini menghasilkan bilangan heksadesimal acak. Fungsi ini mengembalikan bilangan heksadesimal.

    ```sh
    console.log(randomHexaNumberGenerator());
    '#ee33df'
    ```

1. Deklarasikan fungsi bernama _userIdGenerator_. Ketika fungsi ini dipanggil, fungsi ini menghasilkan id tujuh karakter. Fungsi ini mengembalikan id tersebut.

    ```sh
    console.log(userIdGenerator());
    41XTDbE
    ```

### Latihan: Level 3

1. Modifikasi fungsi _userIdGenerator_. Deklarasikan fungsi bernama _userIdGeneratedByUser_. Fungsi ini tidak menerima parameter apa pun tetapi menerima dua input menggunakan prompt(). Salah satu input adalah jumlah karakter dan input kedua adalah jumlah id yang seharusnya dihasilkan.

    ```sh
    userIdGeneratedByUser()
    'kcsy2
    SMFYb
    bWmeq
    ZXOYh
    2Rgxf
    '
    userIdGeneratedByUser()
    '1GCSgPLMaBAVQZ26
    YD7eFwNQKNs7qXaT
    ycArC5yrRupyG00S
    UbGxOFI7UXSWAyKN
    dIV0SSUTgAdKwStr
    '
    ```

1. Tulis fungsi bernama _rgbColorGenerator_ yang menghasilkan warna rgb.

    ```sh
    rgbColorGenerator()
    rgb(125,244,255)
    ```

1. Tulis fungsi **_arrayOfHexaColors_** yang mengembalikan sejumlah warna heksadesimal dalam sebuah array.
1. Tulis fungsi **_arrayOfRgbColors_** yang mengembalikan sejumlah warna RGB dalam sebuah array.
1. Tulis fungsi **_convertHexaToRgb_** yang mengonversi warna hexa ke rgb dan mengembalikan warna rgb.
1. Tulis fungsi **_convertRgbToHexa_** yang mengonversi rgb ke warna hexa dan mengembalikan warna hexa.
1. Tulis fungsi **_generateColors_** yang dapat menghasilkan sejumlah warna hexa atau rgb.

    ```js
    console.log(generateColors('hexa', 3)) // ['#a3e12f', '#03ed55', '#eb3d2b']
    console.log(generateColors('hexa', 1)) // '#b334ef'
    console.log(generateColors('rgb', 3)) // ['rgb(5, 55, 175)', 'rgb(50, 105, 100)', 'rgb(15, 26, 80)']
    console.log(generateColors('rgb', 1)) // 'rgb(33,79, 176)'
    ```

1. Panggil fungsi Anda _shuffleArray_, fungsi ini menerima array sebagai parameter dan mengembalikan array yang diacak
1. Panggil fungsi Anda _factorial_, fungsi ini menerima bilangan bulat sebagai parameter dan mengembalikan faktorial dari bilangan tersebut
1. Panggil fungsi Anda _isEmpty_, fungsi ini menerima parameter dan memeriksa apakah parameter tersebut kosong atau tidak
1. Panggil fungsi Anda _sum_, fungsi ini menerima sejumlah argumen dan mengembalikan jumlahnya.
1. Tulis fungsi bernama _sumOfArrayItems_, fungsi ini menerima parameter array dan mengembalikan jumlah semua item. Periksa apakah semua item array bertipe number. Jika tidak, berikan umpan balik yang masuk akal.
1. Tulis fungsi bernama _average_, fungsi ini menerima parameter array dan mengembalikan rata-rata item. Periksa apakah semua item array bertipe number. Jika tidak, berikan umpan balik yang masuk akal.
1. Tulis fungsi bernama _modifyArray_ yang menerima array sebagai parameter dan memodifikasi item kelima dari array tersebut dan mengembalikan array. Jika panjang array kurang dari lima, fungsi ini mengembalikan 'item not found'.

    ```js
    console.log(modifyArray(['Avocado', 'Tomato', 'Potato','Mango', 'Lemon','Carrot']);
    ```

    ```sh
    ['Avocado', 'Tomato', 'Potato','Mango', 'LEMON', 'Carrot']
    ```

    ```js
    console.log(modifyArray(['Google', 'Facebook','Apple', 'Amazon','Microsoft',  'IBM']);
    ```

    ```sh
    ['Google', 'Facebook','Apple', 'Amazon','MICROSOFT',  'IBM']
    ```

    ```js
    console.log(modifyArray(['Google', 'Facebook','Apple', 'Amazon']);
    ```

    ```sh
      'Not Found'
    ```

1. Tulis fungsi bernama _isPrime_, yang memeriksa apakah suatu bilangan adalah bilangan prima.
1. Tulis fungsi yang memeriksa apakah semua item unik dalam array.
1. Tulis fungsi yang memeriksa apakah semua item array memiliki tipe data yang sama.
1. Nama variabel JavaScript tidak mendukung karakter khusus atau simbol kecuali \$ atau \_. Tulis fungsi **isValidVariable** yang memeriksa apakah suatu variabel valid atau tidak valid.
1. Tulis fungsi yang mengembalikan array berisi tujuh angka acak dalam rentang 0-9. Semua angka harus unik.

    ```js
    sevenRandomNumbers()
    [(1, 4, 5, 7, 9, 8, 0)]
    ```

1. Tulis fungsi bernama reverseCountries, fungsi ini menerima array countries dan pertama-tama menyalin array tersebut lalu mengembalikan kebalikan dari array asli

🎉 SELAMAT ! 🎉
