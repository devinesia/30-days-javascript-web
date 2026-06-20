# 📘 Hari 13

## Metode Objek Console

Di sesi kali ini, kita bakal bahas tentang console dan berbagai metode objek console. Pemula biasanya suka bingung: pakenya console.log(), document.write(), atau document.getElementById() ya?

Nah gini, kita pake metode objek console buat nampilin output di konsol browser, dan document.write buat nampilin output di dokumen browser (viewport). Dua metode ini sebenernya cuma dipake buat testing dan debugging aja. Console itu alat testing dan debugging paling populer di browser, jadi wajib banget kamu kuasai. Kalau document.getElementById() dipake saat kita mau interaksi sama DOM pake JavaScript. Tenang, kita bakal bahas DOM nanti di sesi terpisah.

Selain console.log() yang udah terkenal itu, console juga punya banyak metode keren lainnya. Yuk kita eksplor!

### console.log()

console.log() kita pake buat nampilin output di konsol browser. Kita bisa substitusi nilai dan bahkan ngasih gaya (styling) ke output logging pake %c. Keren kan?

- Nampilin output di konsol browser

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

Kita bisa ngasih style ke pesan logging pake CSS. Coba deh salin kode ini dan tempel di konsol browser buat liat hasilnya.

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

console.warn() dipake buat ngasih peringatan di browser. Misalnya ngasih tau soal deprecation versi paket atau praktik yang kurang baik. Coba salin dan tempel di konsol browser deh, biar liat gimana pesan peringatannya.

```js
console.warn('This is a warning')
console.warn(
  'You are using React. Do not touch the DOM. Virtual DOM will take care of handling the DOM!'
)
console.warn('Warning is different from error')
```

### console.error()

console.error() buat nampilin pesan error.

```js
console.error('This is an error message')
console.error('We all make mistakes')
```

### console.table()

console.table() nampilin data dalam bentuk tabel di konsol. Berguna banget buat liat data tabular. console.table() nerima satu argumen data wajib, harus array atau objek, plus satu parameter kolom opsional.

Yuk kita coba dengan array sederhana. Kode di bawah nampilin tabel dua kolom: kolom indeks dan kolom nilai.

```js
const names = ['Asabeneh', 'Brook', 'David', 'John']
console.table(names)
```

Kita juga cek hasil dari objek nih. Nanti dia bikin tabel dengan dua kolom: kolom indeks yang isinya kunci dan kolom nilai yang isinya value objek.

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

Coba juga contoh lainnya, salin dan tempel di konsol browser.

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

Ini buat mulaiin timer yang bisa kamu pake buat ngelacak seberapa lama suatu operasi berjalan. Kamu bisa kasih nama unik buat setiap timer, dan bisa punya sampe 10.000 timer berjalan dalam satu halaman. Pas kamu panggil console.timeEnd() dengan nama yang sama, browser bakal nampilin waktu dalam milidetik yang udah berlalu sejak timer dimulai. Cakep buat ngetes performa!

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

Dari output di atas, keliatan kan kalau regular for loop lebih lambat daripada for of atau forEach loop.

### console.info()

Nampilin pesan informasi di konsol browser.

```js
console.info('30 Days Of JavaScript challenge is trending on Github')
console.info('30 Days Of fullStack challenge might be released')
console.info('30 Days Of HTML and CSS challenge might be released')
```

### console.assert()

console.assert() nulis pesan error ke konsol kalau asersinya false. Kalau asersinya true, ya udah nggak terjadi apa-apa. Parameter pertama adalah ekspresi asersi. Kalau ekspresinya false, bakal muncul pesan error "Assertion failed".

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

console.group() bisa bantu kamu ngelompokkin berbagai grup log. Coba salin dan tempel di konsol browser buat liat grupnya.

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

Ini ngitung berapa kali console.count() dipanggil. Nerima parameter label string. Berguna banget buat ngitung berapa kali suatu fungsi dieksekusi. Di contoh ini, console.count() bakal jalan tiga kali.

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

console.clear() bersihin konsol browser. Simpel banget!

🌕 Tetep jaga semangatmu! Terus gas, langit itu batasnya! Kamu baru aja nuntasin tantangan hari ke-13 dan sekarang udah 13 langkah lebih dekat menuju level dewa. Yuk sekarang latihan biar skill kamu makin terasah!

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
