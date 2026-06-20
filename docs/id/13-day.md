# 📘 Hari 13

## Metode Objek Console

Di bagian ini, kita akan membahas tentang console dan metode objek console. Pemula biasanya tidak tahu mana yang harus digunakan: console.log(), document.write() atau document.getElementById.

Kita menggunakan metode objek console untuk menampilkan output di konsol browser dan kita menggunakan document.write untuk menampilkan output di dokumen browser (viewport). Kedua metode ini hanya digunakan untuk tujuan pengujian dan debugging. Metode console adalah alat pengujian dan debugging paling populer di browser. Kita menggunakan document.getElementById() saat ingin berinteraksi dengan DOM menggunakan JavaScript. Kita akan membahas DOM di bagian lain.

Selain metode console.log() yang terkenal, console menyediakan metode-metode lainnya.

### console.log()

Kita menggunakan console.log() untuk menampilkan output di konsol browser. Kita dapat mensubstitusi nilai dan juga dapat memberi gaya pada output logging menggunakan %c.

- Menampilkan output di konsol browser

```js
console.log('30 Days of JavaScript')
```

```sh
30 Days of JavaScript
```

- Substitusi

```js
console.log('%d %s of JavaScript', 30, 'Days')
```

```sh
30 Days of JavaScript
```

- CSS

Kita dapat memberi gaya pada pesan logging menggunakan CSS. Salin kode berikut dan tempelkan di konsol browser untuk melihat hasilnya.

```js
console.log('%c30 Days Of JavaScript', 'color:green') // log output is green
console.log(
  '%c30 Days%c %cOf%c %cJavaScript%c',
  'color:green',
  '',
  'color:red',
  '',
  'color:yellow'
) // log output green red and yellow text
```

### console.warn()

Kita menggunakan console.warn() untuk memberikan peringatan di browser. Misalnya untuk menginformasikan atau memperingatkan deprecation versi paket atau praktik buruk. Salin kode berikut dan tempelkan di konsol browser untuk melihat pesan peringatan.

```js
console.warn('This is a warning')
console.warn(
  'You are using React. Do not touch the DOM. Virtual DOM will take care of handling the DOM!'
)
console.warn('Warning is different from error')
```

### console.error()

Metode console.error() menampilkan pesan error.

```js
console.error('This is an error message')
console.error('We all make mistakes')
```

### console.table()

Metode console.table() menampilkan data sebagai tabel di konsol. Menampilkan data tabular sebagai tabel. console.table() menerima satu argumen data yang wajib, yang harus berupa array atau objek, dan satu parameter kolom opsional tambahan.

Mari kita mulai dengan array sederhana. Kode di bawah menampilkan tabel dengan dua kolom. Kolom indeks untuk menampilkan indeks dan kolom nilai untuk menampilkan nama.

```js
const names = ['Asabeneh', 'Brook', 'David', 'John']
console.table(names)
```

Mari kita juga periksa hasil dari objek. Ini membuat tabel dengan dua kolom: kolom indeks yang berisi kunci dan kolom nilai yang berisi nilai objek.

```js
const user = {
  name: 'Asabeneh',
  title: 'Programmer',
  country: 'Finland',
  city: 'Helsinki',
  age: 250
}
console.table(user)
```

Periksa contoh lainnya dengan menyalin dan menempelkan di konsol browser.

```js
const countries = [
  ['Finland', 'Helsinki'],
  ['Sweden', 'Stockholm'],
  ['Norway', 'Oslo']
]
console.table(countries)
```

```js
const users = [
  {
    name: 'Asabeneh',
    title: 'Programmer',
    country: 'Finland',
    city: 'Helsinki',
    age: 250
  },
  {
    name: 'Eyob',
    title: 'Teacher',
    country: 'Sweden',
    city: 'London',
    age: 25
  },
  {
    name: 'Asab',
    title: 'Instructor',
    country: 'Norway',
    city: 'Oslo',
    age: 22
  },
  {
    name: 'Matias',
    title: 'Developer',
    country: 'Denmark',
    city: 'Copenhagen',
    age: 28
  }
]
console.table(users)
```

### console.time()

Memulai timer yang dapat Anda gunakan untuk melacak berapa lama suatu operasi berjalan. Anda memberi setiap timer nama unik, dan dapat memiliki hingga 10.000 timer berjalan pada satu halaman. Saat Anda memanggil console.timeEnd() dengan nama yang sama, browser akan menampilkan waktu, dalam milidetik, yang berlalu sejak timer dimulai.

```js
const countries = [
  ['Finland', 'Helsinki'],
  ['Sweden', 'Stockholm'],
  ['Norway', 'Oslo']
]

console.time('Regular for loop')
for (let i = 0; i < countries.length; i++) {
  console.log(countries[i][0], countries[i][1])
}
console.timeEnd('Regular for loop')

console.time('for of loop')
for (const [name, city] of countries) {
  console.log(name, city)
}
console.timeEnd('for of loop')

console.time('forEach loop')
countries.forEach(([name, city]) => {
  console.log(name, city)
})
console.timeEnd('forEach loop')
```

```sh
Finland Helsinki
Sweden Stockholm
Norway Oslo
Regular for loop: 0.34716796875ms
Finland Helsinki
Sweden Stockholm
Norway Oslo
for of loop: 0.26806640625ms
Finland Helsinki
Sweden Stockholm
Norway Oslo
forEach loop: 0.358154296875ms
```

Berdasarkan output di atas, regular for loop lebih lambat daripada for of atau forEach loop.

### console.info()

Menampilkan pesan informasi di konsol browser.

```js
console.info('30 Days Of JavaScript challenge is trending on Github')
console.info('30 Days Of fullStack challenge might be released')
console.info('30 Days Of HTML and CSS challenge might be released')
```

### console.assert()

Metode console.assert() menulis pesan error ke konsol jika asersi bernilai false. Jika asersi bernilai true, tidak terjadi apa-apa. Parameter pertama adalah ekspresi asersi. Jika ekspresi ini false, pesan error Assertion failed akan ditampilkan.

```js
console.assert(4 > 3, '4 is greater than 3') // no result
console.assert(3 > 4, '3 is not greater than 4') // Assertion failed: 3 is not greater than 4

for (let i = 0; i <= 10; i += 1) {
  let errorMessage = `${i} is not even`
  console.log('the # is ' + i)
  console.assert(i % 2 === 0, { number: i, errorMessage: errorMessage })
}
```

### console.group()

console.group() dapat membantu mengelompokkan berbagai grup log. Salin kode berikut dan tempelkan di konsol browser untuk melihat grupnya.

```js
const names = ['Asabeneh', 'Brook', 'David', 'John']
const countries = [
  ['Finland', 'Helsinki'],
  ['Sweden', 'Stockholm'],
  ['Norway', 'Oslo']
]
const user = {
  name: 'Asabeneh',
  title: 'Programmer',
  country: 'Finland',
  city: 'Helsinki',
  age: 250
}
const users = [
  {
    name: 'Asabeneh',
    title: 'Programmer',
    country: 'Finland',
    city: 'Helsinki',
    age: 250
  },
  {
    name: 'Eyob',
    title: 'Teacher',
    country: 'Sweden',
    city: 'London',
    age: 25
  },
  {
    name: 'Asab',
    title: 'Instructor',
    country: 'Norway',
    city: 'Oslo',
    age: 22
  },
  {
    name: 'Matias',
    title: 'Developer',
    country: 'Denmark',
    city: 'Copenhagen',
    age: 28
  }
]

console.group('Names')
console.log(names)
console.groupEnd()

console.group('Countries')
console.log(countries)
console.groupEnd()

console.group('Users')
console.log(user)
console.log(users)
console.groupEnd()
```

### console.count()

Ini mencetak berapa kali console.count() dipanggil. Menerima parameter label string. Sangat membantu untuk menghitung berapa kali sebuah fungsi dipanggil. Dalam contoh berikut, metode console.count() akan berjalan tiga kali.

```js
const func = () => {
  console.count('Function has been called')
}
func()
func()
func()
```

```sh
Function has been called: 1
Function has been called: 2
Function has been called: 3
```

### console.clear()

console.clear() membersihkan konsol browser.

🌕 Pertahankan kerja bagus Anda. Teruslah berusaha, langit adalah batasnya! Anda baru saja menyelesaikan tantangan hari ke-13 dan Anda 13 langkah lebih maju menuju kehebatan. Sekarang lakukan beberapa latihan untuk otak dan otot Anda.

## Latihan

### Latihan: Level 1

1.  Tampilkan array countries sebagai tabel
2.  Tampilkan objek countries sebagai tabel
3.  Gunakan console.group() untuk mengelompokkan log

### Latihan: Level 2

1. 10 > 2 \* 10 gunakan console.assert()
2. Tulis pesan peringatan menggunakan console.warn()
3. Tulis pesan error menggunakan console.error()

### Latihan: Level 3

1. Periksa perbedaan kecepatan di antara perulangan berikut: while, for, for of, forEach

🎉 SELAMAT! 🎉
