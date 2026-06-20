# 📔 Hari 6

## Perulangan (Loop)

Sebagian besar aktivitas yang kita lakukan dalam hidup penuh dengan pengulangan. Bayangkan jika saya meminta Anda mencetak angka dari 0 sampai 100 menggunakan `console.log()`. Untuk mengimplementasikan tugas sederhana ini mungkin memakan waktu 2 sampai 5 menit, tugas yang membosankan dan berulang seperti ini dapat dilakukan menggunakan loop. Jika Anda lebih suka menonton video, Anda bisa melihat [video tutorial](https://www.youtube.com/channel/UCM4xOopkYiPwJqyKsSqL9mw)

Dalam bahasa pemrograman, untuk menjalankan tugas berulang kita menggunakan berbagai jenis loop. Contoh berikut adalah loop yang umum digunakan di JavaScript dan bahasa pemrograman lainnya.

### for Loop

```js
// Struktur for loop
for(initialization, condition, increment/decrement){
  // kode di sini
}
```

```js
for(let i = 0; i <= 5; i++){
  console.log(i)
}

// 0 1 2 3 4 5
```

```js
for(let i = 5; i >= 0; i--){
  console.log(i)
}

// 5 4 3 2 1 0
```

```js
for(let i = 0; i <= 5; i++){
  console.log(`${i} * ${i} = ${i * i}`)
}
```

```sh
0 * 0 = 0
1 * 1 = 1
2 * 2 = 4
3 * 3 = 9
4 * 4 = 16
5 * 5 = 25
```

```js
const countries = ['Finland', 'Sweden', 'Denmark', 'Norway', 'Iceland']
const newArr = []
for(let i = 0; i < countries.length; i++){
  newArr.push(countries[i].toUpperCase())
}

// ["FINLAND", "SWEDEN", "DENMARK", "NORWAY", "ICELAND"]
```

Menjumlahkan semua elemen dalam array

```js
const numbers = [1, 2, 3, 4, 5]
let sum = 0
for(let i = 0; i < numbers.length; i++){
  sum  = sum + numbers[i]  // bisa disingkat, sum += numbers[i]

}

console.log(sum)  // 15
```

Membuat array baru berdasarkan array yang sudah ada

```js
const numbers = [1, 2, 3, 4, 5]
const newArr = []
let sum = 0
for(let i = 0; i < numbers.length; i++){
  newArr.push( numbers[i] ** 2)

}

console.log(newArr)  // [1, 4, 9, 16, 25]
```

```js
const countries = ['Finland', 'Sweden', 'Norway', 'Denmark', 'Iceland']
const newArr = []
for(let i = 0; i < countries.length; i++){
  newArr.push(countries[i].toUpperCase())
}

console.log(newArr)  // ["FINLAND", "SWEDEN", "NORWAY", "DENMARK", "ICELAND"]
```

### while loop

```js
let i = 0
while (i <= 5) {
  console.log(i)
  i++
}

// 0 1 2 3 4 5
```

### do while loop

```js
let i = 0
do {
  console.log(i)
  i++
} while (i <= 5)

// 0 1 2 3 4 5
```

### for of loop

Kita menggunakan for of loop untuk array. Ini adalah cara yang sangat praktis untuk mengiterasi array jika kita tidak tertarik pada indeks setiap elemen dalam array.

```js
for (const element of arr) {
  // kode di sini
}
```

```js

const numbers = [1, 2, 3, 4, 5]

for (const num of numbers) {
  console.log(num)
}

// 1 2 3 4 5

for (const num of numbers) {
  console.log(num * num)
}

// 1 4 9 16 25

// menjumlahkan semua angka dalam array
let sum = 0
for (const num of numbers) {
  sum = sum + num  
	// bisa juga disingkat seperti ini, sum += num
  // setelah ini kita akan menggunakan sintaks yang lebih singkat (+=, -=, *=, /= dll)
}
console.log(sum) // 15

const webTechs = [
  'HTML',
  'CSS',
  'JavaScript',
  'React',
  'Redux',
  'Node',
  'MongoDB'
]

for (const tech of webTechs) {
  console.log(tech.toUpperCase())
}

// HTML CSS JAVASCRIPT REACT NODE MONGODB

for (const tech of webTechs) {
  console.log(tech[0]) // hanya mengambil huruf pertama setiap elemen,  H C J R N M
}

```

```js
const countries = ['Finland', 'Sweden', 'Norway', 'Denmark', 'Iceland']
const newArr = []
for(const country of countries){
  newArr.push(country.toUpperCase())
}

console.log(newArr)  // ["FINLAND", "SWEDEN", "NORWAY", "DENMARK", "ICELAND"]
```

### break

Break digunakan untuk menghentikan suatu loop.

```js
for(let i = 0; i <= 5; i++){
  if(i == 3){
    break
  }
  console.log(i)
}

// 0 1 2
```

Kode di atas berhenti jika 3 ditemukan dalam proses iterasi.

### continue

Kita menggunakan kata kunci *continue* untuk melewati iterasi tertentu.

```js
for(let i = 0; i <= 5; i++){
  if(i == 3){
    continue
  }
  console.log(i)
}

// 0 1 2 4 5
```

🌕 Anda sangat berani, Anda sudah sampai sejauh ini. Sekarang, Anda telah memiliki kekuatan untuk mengotomatisasi tugas-tugas yang berulang dan membosankan. Anda baru saja menyelesaikan tantangan hari ke-6 dan Anda selangkah lebih maju menuju kehebatan. Sekarang lakukan beberapa latihan untuk otak dan otot Anda.

## 💻 Latihan: Hari 6

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

  const mernStack = ['MongoDB', 'Express', 'React', 'Node']
  ```

1. Iterasi 0 sampai 10 menggunakan for loop, lakukan hal yang sama menggunakan while dan do while loop
2. Iterasi 10 sampai 0 menggunakan for loop, lakukan hal yang sama menggunakan while dan do while loop
3. Iterasi 0 sampai n menggunakan for loop
4. Tulis loop yang membuat pola berikut menggunakan `console.log()`:

   ```js
       #
       ##
       ###
       ####
       #####
       ######
       #######
   ```

5. Gunakan loop untuk mencetak pola berikut:

   ```sh
   0 x 0 = 0
   1 x 1 = 1
   2 x 2 = 4
   3 x 3 = 9
   4 x 4 = 16
   5 x 5 = 25
   6 x 6 = 36
   7 x 7 = 49
   8 x 8 = 64
   9 x 9 = 81
   10 x 10 = 100
   ```

6. Gunakan loop untuk mencetak pola berikut

   ```sh
    i    i^2   i^3
    0    0     0
    1    1     1
    2    4     8
    3    9     27
    4    16    64
    5    25    125
    6    36    216
    7    49    343
    8    64    512
    9    81    729
    10   100   1000
   ```

7. Gunakan for loop untuk iterasi dari 0 sampai 100 dan cetak hanya bilangan genap
8. Gunakan for loop untuk iterasi dari 0 sampai 100 dan cetak hanya bilangan ganjil
9. Gunakan for loop untuk iterasi dari 0 sampai 100 dan cetak hanya bilangan prima
10. Gunakan for loop untuk iterasi dari 0 sampai 100 dan cetak jumlah semua bilangan.

    ```sh
    The sum of all numbers from 0 to 100 is 5050.
    ```

11. Gunakan for loop untuk iterasi dari 0 sampai 100 dan cetak jumlah semua bilangan genap dan jumlah semua bilangan ganjil.

    ```sh
    The sum of all evens from 0 to 100 is 2550. And the sum of all odds from 0 to 100 is 2500.
    ```

12. Gunakan for loop untuk iterasi dari 0 sampai 100 dan cetak jumlah semua bilangan genap dan jumlah semua bilangan ganjil. Cetak jumlah bilangan genap dan jumlah bilangan ganjil sebagai array

    ```sh
      [2550, 2500]
    ```

13. Buat script kecil yang menghasilkan array berisi 5 angka acak
14. Buat script kecil yang menghasilkan array berisi 5 angka acak dan angka-angkanya harus unik
15. Buat script kecil yang menghasilkan id acak enam karakter:

    ```sh
    5j2khz
    ```

### Latihan: Level 2

1. Buat script kecil yang menghasilkan id acak dengan jumlah karakter berapa pun:

    ```sh
      fe3jo1gl124g
    ```

    ```sh
      xkqci4utda1lmbelpkm03rba
    ```

1. Tulis script yang menghasilkan bilangan heksadesimal acak.

    ```sh
    '#ee33df'
    ```

1. Tulis script yang menghasilkan warna rgb acak.

    ```sh
    rgb(240,180,80)
    ```

1. Menggunakan array countries di atas, buat array baru berikut.

    ```sh
    ["ALBANIA", "BOLIVIA", "CANADA", "DENMARK", "ETHIOPIA", "FINLAND", "GERMANY", "HUNGARY", "IRELAND", "JAPAN", "KENYA"]
    ```

1. Menggunakan array countries di atas, buat array untuk panjang setiap negara.

    ```sh
    [7, 7, 6, 7, 8, 7, 7, 7, 7, 5, 5]
    ```

1. Gunakan array countries untuk membuat array dari array berikut:

    ```sh
      [
      ['Albania', 'ALB', 7],
      ['Bolivia', 'BOL', 7],
      ['Canada', 'CAN', 6],
      ['Denmark', 'DEN', 7],
      ['Ethiopia', 'ETH', 8],
      ['Finland', 'FIN', 7],
      ['Germany', 'GER', 7],
      ['Hungary', 'HUN', 7],
      ['Ireland', 'IRE', 7],
      ['Iceland', 'ICE', 7],
      ['Japan', 'JAP', 5],
      ['Kenya', 'KEN', 5]
    ]
    ```

2. Di array countries di atas, periksa apakah ada negara yang mengandung kata 'land'. Jika ada negara yang mengandung 'land', cetak sebagai array. Jika tidak ada negara yang mengandung kata 'land', cetak 'All these countries are without land'.

    ```sh
    ['Finland','Ireland', 'Iceland']
    ```

3. Di array countries di atas, periksa apakah ada negara yang berakhiran substring 'ia'. Jika ada negara yang berakhiran dengan itu, cetak sebagai array. Jika tidak ada negara yang mengandung kata 'ai', cetak 'These are countries ends without ia'.

    ```sh
    ['Albania', 'Bolivia','Ethiopia']
    ```

4. Menggunakan array countries di atas, temukan negara dengan jumlah karakter terbanyak.

      ```sh
      Ethiopia
      ```

5. Menggunakan array countries di atas, temukan negara yang hanya memiliki 5 karakter.

    ```sh
    ['Japan', 'Kenya']
    ```

6. Temukan kata terpanjang di array webTechs
7. Gunakan array webTechs untuk membuat array dari array berikut:

    ```sh
    [["HTML", 4], ["CSS", 3],["JavaScript", 10],["React", 5],["Redux", 5],["Node", 4],["MongoDB", 7]]
    ```

8. Aplikasi yang dibuat menggunakan MongoDB, Express, React, dan Node disebut aplikasi MERN stack. Buat akronim MERN menggunakan array mernStack
9. Iterasi array, ["HTML", "CSS", "JS", "React", "Redux", "Node", "Express", "MongoDB"] menggunakan for loop atau for of loop dan cetak setiap item.
10. Ini adalah array buah, ['banana', 'orange', 'mango', 'lemon'] balik urutannya menggunakan loop tanpa menggunakan metode reverse.
11. Cetak semua elemen array seperti yang ditunjukkan di bawah ini.

    ```js
      const fullStack = [
        ['HTML', 'CSS', 'JS', 'React'],
        ['Node', 'Express', 'MongoDB']
      ]
    ````

    ```sh
      HTML
      CSS
      JS
      REACT
      NODE
      EXPRESS
      MONGODB
    ```

### Latihan: Level 3

1. Salin array countries (Hindari mutasi)
1. Array bersifat mutable. Buat salinan array yang tidak mengubah array asli. Urutkan array yang disalin dan simpan dalam variabel sortedCountries
1. Urutkan array webTechs dan array mernStack
1. Ekstrak semua negara yang mengandung kata 'land' dari [array countries](https://github.com/Asabeneh/30DaysOfJavaScript/tree/master/data/countries.js) dan cetak sebagai array
1. Temukan negara dengan jumlah karakter terbanyak di [array countries](https://github.com/Asabeneh/30DaysOfJavaScript/tree/master/data/countries.js)
1. Ekstrak semua negara yang mengandung kata 'land' dari [array countries](https://github.com/Asabeneh/30DaysOfJavaScript/tree/master/data/countries.js) dan cetak sebagai array
1. Ekstrak semua negara yang hanya memiliki empat karakter dari [array countries](https://github.com/Asabeneh/30DaysOfJavaScript/tree/master/data/countries.js) dan cetak sebagai array
1. Ekstrak semua negara yang mengandung dua kata atau lebih dari [array countries](https://github.com/Asabeneh/30DaysOfJavaScript/tree/master/data/countries.js) dan cetak sebagai array
1. Balik [array countries](https://github.com/Asabeneh/30DaysOfJavaScript/tree/master/data/countries.js) dan kapitalisasi setiap negara lalu simpan sebagai array

🎉 SELAMAT ! 🎉
