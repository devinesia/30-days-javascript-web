# 📔 Hari 4 - Yuk Ngoding!

## Kondisional

Pernyataan kondisional dipake buat ngambil keputusan berdasarkan kondisi yang beda-beda.
Secara default, pernyataan dalam skrip JavaScript dieksekusi secara berurutan dari atas ke bawah. Kalau logika pemrosesan memerlukannya, alur eksekusi berurutan bisa diubah dengan dua cara:

- Eksekusi kondisional: sebuah blok yang terdiri dari satu atau lebih pernyataan bakal dieksekusi kalau ekspresi tertentu bernilai true
- Eksekusi berulang: sebuah blok yang terdiri dari satu atau lebih pernyataan bakal dieksekusi secara berulang selama ekspresi tertentu bernilai true. Di bagian ini, kita bakal bahas pernyataan _if_, _else_, _else if_. Operator perbandingan dan logika yang kita pelajari di bagian sebelumnya bakal berguna di sini.

Kondisi bisa diimplementasikan pake cara berikut:

- if
- if else
- if else if else
- switch
- ternary operator

### If

Di JavaScript dan bahasa pemrograman lainnya, kata kunci _if_ dipake buat ngecek apakah suatu kondisi bernilai true dan buat ngeksekusi blok kode. Buat bikin kondisi if, kita perlu kata kunci _if_, kondisi di dalam tanda kurung, dan blok kode di dalam kurung kurawal ({}).

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

Kayak yang kamu lihat di contoh kondisi di atas, 3 lebih gede dari 0, jadi itu angka positif. Kondisinya true dan blok kode dieksekusi. Tapi kalau kondisinya false, kita nggak bakal lihat hasil apa pun.

```js
let isRaining = true
if (isRaining) {
  console.log('Remember to take your rain coat.')
}
```

Hal yang sama berlaku buat kondisi kedua, kalau isRaining false, blok if nggak bakal dieksekusi dan kita nggak lihat output apa pun. Buat lihat hasil dari kondisi falsy, kita harus punya blok lain, yaitu _else_.

### If Else

Kalau kondisi true, blok pertama bakal dieksekusi, kalau nggak, kondisi else bakal dieksekusi.

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

Kondisi terakhir adalah false, makanya blok else dieksekusi. Gimana kalau kita punya lebih dari dua kondisi? Nah, dalam kasus kayak gitu, kita bakal pake kondisi *else if*.

### If Else if Else

Dalam kehidupan sehari-hari, kita ngambil keputusan setiap hari. Kita ngambil keputusan nggak cuma dengan ngecek satu atau dua kondisi, tapi ngambil keputusan berdasarkan banyak kondisi. Sama kayak kehidupan sehari-hari kita, pemrograman juga penuh dengan kondisi. Kita pake *else if* ketika kita punya banyak kondisi.

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

Switch adalah alternatif buat **if else if else else**.
Pernyataan switch dimulai dengan kata kunci *switch* diikuti oleh tanda kurung dan blok kode. Di dalam blok kode kita bakal punya case yang beda-beda. Blok case berjalan kalau nilai dalam tanda kurung pernyataan switch cocok dengan nilai case. Pernyataan break buat ngehentiin eksekusi supaya eksekusi kode nggak lanjut ke bawah setelah kondisi terpenuhi. Blok default berjalan kalau semua case nggak memenuhi kondisi.

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

Cara lain buat nulis kondisional adalah pake operator ternary. Kita udah bahas ini di bagian lain, tapi kita juga harus nyebutin di sini.

```js
let isRaining = true
isRaining
  ? console.log('You need a rain coat.')
  : console.log('No need for a rain coat.')
```

🌕 Kamu luar biasa dan punya potensi yang luar biasa. Kamu baru aja nyelesein tantangan hari ke-4 dan kamu selangkah lebih maju menuju kehebatan. Gaskeun sekarang lakuin latihan buat otak dan otot kamu!  

## 💻 Latihan

### Latihan: Level 1

1. Dapetin input pengguna pake prompt("Enter your age:"). Kalau pengguna berusia 18 tahun atau lebih, kasih umpan balik: 'You are old enough to drive' tapi kalau belum 18, kasih umpan balik lain yang menyatakan buat nunggu jumlah tahun yang diperlukan hingga berusia 18 tahun.

   ```sh
   Masukkan usia Anda: 30
   Anda cukup umur untuk mengemudi.

   Masukkan usia Anda:15
   Anda tinggal 3 tahun lagi untuk mengemudi.
   ```

1. Bandingin nilai myAge dan yourAge pake if … else. Berdasarkan perbandingan, catat hasilnya ke konsol yang menyatakan siapa yang lebih tua (saya atau kamu). Pake prompt("Enter your age:") buat dapetin usia sebagai input.

   ```sh
   Masukkan usia Anda: 30
   Anda 5 tahun lebih tua dari saya.
   ```

1. Kalau a lebih gede dari b, kembalikan 'a is greater than b' kalau nggak 'a is less than b'. Coba implementasiin dengan dua cara

    - pake if else
    - ternary operator.

    ```js
      let a = 4
      let b = 3
    ```

    ```sh
      4 is greater than 3
    ```

1. Angka genap bisa dibagi 2 dan sisanya nol. Gimana cara kamu ngecek apakah suatu angka genap atau nggak pake JavaScript?

    ```sh
    Masukkan angka: 2
    2 adalah angka genap

    Masukkan angka: 9
    9 adalah angka ganjil.
    ```

### Latihan: Level 2

1. Tulis kode yang bisa ngasih nilai kepada siswa sesuai dengan skor mereka:
   - 80-100, A
   - 70-89, B
   - 60-69, C
   - 50-59, D
   - 0-49, F
1. Cek apakah musimnya Gugur, Dingin, Semi, atau Panas.
   Kalau input pengguna adalah:
   - September, Oktober atau November, musimnya adalah Gugur.
   - Desember, Januari atau Februari, musimnya adalah Dingin.
   - Maret, April atau Mei, musimnya adalah Semi
   - Juni, Juli atau Agustus, musimnya adalah Panas
1. Cek apakah suatu hari adalah hari akhir pekan atau hari kerja. Skrip kamu bakal nerima hari sebagai input.

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

1. Tulis program yang nyebutin jumlah hari dalam sebulan.

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

1. Tulis program yang nyebutin jumlah hari dalam sebulan, sekarang pertimbangin tahun kabisat.


🎉 SELAMAT ! 🎉
