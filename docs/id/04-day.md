# 📔 Hari 4

## Kondisional

Pernyataan kondisional digunakan untuk membuat keputusan berdasarkan kondisi yang berbeda.
Secara default, pernyataan dalam skrip JavaScript dieksekusi secara berurutan dari atas ke bawah. Jika logika pemrosesan memerlukannya, alur eksekusi berurutan dapat diubah dengan dua cara:

- Eksekusi kondisional: sebuah blok yang terdiri dari satu atau lebih pernyataan akan dieksekusi jika ekspresi tertentu bernilai true
- Eksekusi berulang: sebuah blok yang terdiri dari satu atau lebih pernyataan akan dieksekusi secara berulang selama ekspresi tertentu bernilai true. Di bagian ini, kita akan membahas pernyataan _if_, _else_, _else if_. Operator perbandingan dan logika yang kita pelajari di bagian sebelumnya akan berguna di sini.

Kondisi dapat diimplementasikan menggunakan cara berikut:

- if
- if else
- if else if else
- switch
- ternary operator

### If

Dalam JavaScript dan bahasa pemrograman lainnya, kata kunci _if_ digunakan untuk memeriksa apakah suatu kondisi bernilai true dan untuk mengeksekusi blok kode. Untuk membuat kondisi if, kita memerlukan kata kunci _if_, kondisi di dalam tanda kurung, dan blok kode di dalam kurung kurawal ({}).

```js
// sintaks
if (condition) {
  //bagian kode ini berjalan untuk kondisi truthy
}
```

**Contoh:**

```js
let num = 3
if (num > 0) {
  console.log(`${num} is a positive number`)
}
//  3 is a positive number
```

Seperti yang Anda lihat pada contoh kondisi di atas, 3 lebih besar dari 0, jadi itu adalah angka positif. Kondisinya true dan blok kode dieksekusi. Namun, jika kondisinya false, kita tidak akan melihat hasil apa pun.

```js
let isRaining = true
if (isRaining) {
  console.log('Remember to take your rain coat.')
}
```

Hal yang sama berlaku untuk kondisi kedua, jika isRaining false, blok if tidak akan dieksekusi dan kita tidak melihat output apa pun. Untuk melihat hasil dari kondisi falsy, kita harus memiliki blok lain, yaitu _else_.

### If Else

Jika kondisi true, blok pertama akan dieksekusi, jika tidak kondisi else akan dieksekusi.

```js
// sintaks
if (condition) {
  // bagian kode ini berjalan untuk kondisi truthy
} else {
  // bagian kode ini berjalan untuk kondisi false
}
```

```js
let num = 3
if (num > 0) {
  console.log(`${num} is a positive number`)
} else {
  console.log(`${num} is a negative number`)
}
//  3 is a positive number

num = -3
if (num > 0) {
  console.log(`${num} is a positive number`)
} else {
  console.log(`${num} is a negative number`)
}
//  -3 is a negative number
```

```js
let isRaining = true
if (isRaining) {
  console.log('You need a rain coat.')
} else {
  console.log('No need for a rain coat.')
}
// You need a rain coat.

isRaining = false
if (isRaining) {
  console.log('You need a rain coat.')
} else {
  console.log('No need for a rain coat.')
}
// No need for a rain coat.
```

Kondisi terakhir adalah false, oleh karena itu blok else dieksekusi. Bagaimana jika kita memiliki lebih dari dua kondisi? Dalam kasus tersebut, kita akan menggunakan kondisi *else if*.

### If Else if Else

Dalam kehidupan sehari-hari, kita membuat keputusan setiap hari. Kita membuat keputusan tidak hanya dengan memeriksa satu atau dua kondisi, melainkan membuat keputusan berdasarkan banyak kondisi. Sama seperti kehidupan sehari-hari kita, pemrograman juga penuh dengan kondisi. Kita menggunakan *else if* ketika kita memiliki banyak kondisi.

```js
// sintaks
if (condition) {
     // kode
} else if (condition) {
   // kode
} else {
    //  kode

}
```

**Contoh:**

```js
let a = 0
if (a > 0) {
  console.log(`${a} is a positive number`)
} else if (a < 0) {
  console.log(`${a} is a negative number`)
} else if (a == 0) {
  console.log(`${a} is zero`)
} else {
  console.log(`${a} is not a number`)
}
```

```js
// if else if else
let weather = 'sunny'
if (weather === 'rainy') {
  console.log('You need a rain coat.')
} else if (weather === 'cloudy') {
  console.log('It might be cold, you need a jacket.')
} else if (weather === 'sunny') {
  console.log('Go out freely.')
} else {
  console.log('No need for rain coat.')
}
```

### Switch

Switch adalah alternatif untuk **if else if else else**.
Pernyataan switch dimulai dengan kata kunci *switch* diikuti oleh tanda kurung dan blok kode. Di dalam blok kode kita akan memiliki case yang berbeda. Blok case berjalan jika nilai dalam tanda kurung pernyataan switch cocok dengan nilai case. Pernyataan break adalah untuk menghentikan eksekusi sehingga eksekusi kode tidak berlanjut ke bawah setelah kondisi terpenuhi. Blok default berjalan jika semua case tidak memenuhi kondisi.

```js
switch(caseValue){
  case 1:
    // kode
    break
  case 2:
   // kode
   break
  case 3:
   // kode
   break
  default:
   // kode
}
```

```js
let weather = 'cloudy'
switch (weather) {
  case 'rainy':
    console.log('You need a rain coat.')
    break
  case 'cloudy':
    console.log('It might be cold, you need a jacket.')
    break
  case 'sunny':
    console.log('Go out freely.')
    break
  default:
    console.log(' No need for rain coat.')
}

// Contoh Switch Lainnya
let dayUserInput = prompt('What day is today ?')
let day = dayUserInput.toLowerCase()

switch (day) {
  case 'monday':
    console.log('Today is Monday')
    break
  case 'tuesday':
    console.log('Today is Tuesday')
    break
  case 'wednesday':
    console.log('Today is Wednesday')
    break
  case 'thursday':
    console.log('Today is Thursday')
    break
  case 'friday':
    console.log('Today is Friday')
    break
  case 'saturday':
    console.log('Today is Saturday')
    break
  case 'sunday':
    console.log('Today is Sunday')
    break
  default:
    console.log('It is not a week day.')
}

```

// Contoh penggunaan kondisi dalam case

```js
let num = prompt('Enter number');
switch (true) {
  case num > 0:
    console.log('Number is positive');
    break;
  case num == 0:
    console.log('Numbers is zero');
    break;
  case num < 0:
    console.log('Number is negative');
    break;
  default:
    console.log('Entered value was not a number');
}
```

### Operator Ternary

Cara lain untuk menulis kondisional adalah menggunakan operator ternary. Kita telah membahas ini di bagian lain, tetapi kita juga harus menyebutkannya di sini.

```js
let isRaining = true
isRaining
  ? console.log('You need a rain coat.')
  : console.log('No need for a rain coat.')
```

🌕 Anda luar biasa dan memiliki potensi yang luar biasa. Anda baru saja menyelesaikan tantangan hari ke-4 dan Anda selangkah lebih maju menuju kehebatan. Sekarang lakukan beberapa latihan untuk otak dan otot Anda.  

## 💻 Latihan

### Latihan: Level 1

1. Dapatkan input pengguna menggunakan prompt("Enter your age:"). Jika pengguna berusia 18 tahun atau lebih, berikan umpan balik: 'You are old enough to drive' tetapi jika belum 18, berikan umpan balik lain yang menyatakan untuk menunggu jumlah tahun yang diperlukan hingga berusia 18 tahun.

   ```sh
   Masukkan usia Anda: 30
   Anda cukup umur untuk mengemudi.

   Masukkan usia Anda:15
   Anda tinggal 3 tahun lagi untuk mengemudi.
   ```

1. Bandingkan nilai myAge dan yourAge menggunakan if … else. Berdasarkan perbandingan, catat hasilnya ke konsol yang menyatakan siapa yang lebih tua (saya atau Anda). Gunakan prompt("Enter your age:") untuk mendapatkan usia sebagai input.

   ```sh
   Masukkan usia Anda: 30
   Anda 5 tahun lebih tua dari saya.
   ```

1. Jika a lebih besar dari b, kembalikan 'a is greater than b' jika tidak 'a is less than b'. Coba implementasikan dengan dua cara

    - menggunakan if else
    - ternary operator.

    ```js
      let a = 4
      let b = 3
    ```

    ```sh
      4 is greater than 3
    ```

1. Angka genap dapat dibagi 2 dan sisanya nol. Bagaimana Anda memeriksa apakah suatu angka genap atau tidak menggunakan JavaScript?

    ```sh
    Masukkan angka: 2
    2 adalah angka genap

    Masukkan angka: 9
    9 adalah angka ganjil.
    ```

### Latihan: Level 2

1. Tulis kode yang dapat memberikan nilai kepada siswa sesuai dengan skor mereka:
   - 80-100, A
   - 70-89, B
   - 60-69, C
   - 50-59, D
   - 0-49, F
1. Periksa apakah musimnya Gugur, Dingin, Semi, atau Panas.
   Jika input pengguna adalah:
   - September, Oktober atau November, musimnya adalah Gugur.
   - Desember, Januari atau Februari, musimnya adalah Dingin.
   - Maret, April atau Mei, musimnya adalah Semi
   - Juni, Juli atau Agustus, musimnya adalah Panas
1. Periksa apakah suatu hari adalah hari akhir pekan atau hari kerja. Skrip Anda akan menerima hari sebagai input.

```sh
  Hari apa hari ini? Sabtu
  Sabtu adalah akhir pekan.

  Hari apa hari ini? satuRa
  Sabtu adalah akhir pekan.

  Hari apa hari ini? Jumat
  Jumat adalah hari kerja.

  Hari apa hari ini? jUMat
  Jumat adalah hari kerja.
```

### Latihan: Level 3

1. Tulis program yang menyebutkan jumlah hari dalam sebulan.

```sh
  Masukkan bulan: Januari
  Januari memiliki 31 hari.

  Masukkan bulan: JANUARI
  Januari memiliki 31 hari

  Masukkan bulan: Februari
  Februari memiliki 28 hari.

  Masukkan bulan: FEBruari
  Februari memiliki 28 hari.
```

1. Tulis program yang menyebutkan jumlah hari dalam sebulan, sekarang pertimbangkan tahun kabisat.


🎉 SELAMAT ! 🎉
