# 📘 Hari 14

## Penanganan Error

JavaScript itu bahasa yang tipe datanya loose (ga terlalu ketat). Jadi kadang-kadang kamu bakal dapetin error runtime pas nyoba akses variabel yang belum didefinisiin atau manggil fungsi yang nggak ada. Namanya juga belajar, error itu temen akrab kita!

JavaScript, mirip kayak Python atau Java, nyediain mekanisme penanganan error buat nangkep error runtime pake blok try-catch-finally. Jadi kamu nggak perlu panik kalo ada error, tinggal tangkep aja!

```js
try {
  // code that may throw an error
} catch (err) {
  // code to be executed if an error occurs
} finally {
  // code to be executed regardless of an error occurs or not
}
```

**try**: bungkus kode yang "mencurigakan" yang mungkin bakal lempar error di blok try. Di sini kita ngetes kode, apakah error atau nggak pas dieksekusi.

**catch**: tulis kode yang bakal jalan pas error terjadi. Blok catch bisa punya parameter yang ngasih info tentang error-nya. Biasanya dipake buat nge-log error atau nampilin pesan yang ramah ke pengguna.

**finally**: blok finally bakal selalu dieksekusi, error atau nggak dia tetep jalan. Cocok buat beres-beres atau reset variabel yang mungkin udah berubah sebelum error di blok try.

**Contoh:**

```js
try {
  let lastName = 'Yetayeh'
  let fullName = fistName + ' ' + lastName
} catch (err) {
  console.log(err)
}
```

```sh
ReferenceError: fistName is not defined
    at <anonymous>:4:20
```

```js
try {
  let lastName = 'Yetayeh'
  let fullName = fistName + ' ' + lastName
} catch (err) {
  console.error(err) // we can use console.log() or console.error()
} finally {
  console.log('In any case I will be executed')
}
```

```sh
ReferenceError: fistName is not defined
    at <anonymous>:4:20
In any case it  will be executed
```

Blok catch nerima satu parameter. Biasanya kita kasih nama e, err, atau error. Parameter ini berupa objek yang punya properti name dan message. Coba kita liat deh.

```js
try {
  let lastName = 'Yetayeh'
  let fullName = fistName + ' ' + lastName
} catch (err) {
  console.log('Name of the error', err.name)
  console.log('Error message', err.message)
} finally {
  console.log('In any case I will be executed')
}
```

```sh
Name of the error ReferenceError
Error message fistName is not defined
In any case I will be executed
```

throw: pernyataan throw ini keren banget, dia bikin kita bisa bikin error kustom sendiri. Kita bisa lempar string, number, boolean, atau objek. Pake throw buat bikin exception bikinan sendiri. Setiap yang kamu lempar, itu yang jadi nilai exception-nya.

```js
throw 'Error2' // generates an exception with a string value
throw 42 // generates an exception with the value 42
throw true // generates an exception with the value true
throw new Error('Required') // generates an error object with the message of Required
```

```js
const throwErrorExampleFun = () => {
  let message
  let x = prompt('Enter a number: ')
  try {
    if (x == '') throw 'empty'
    if (isNaN(x)) throw 'not a number'
    x = Number(x)
    if (x < 5) throw 'too low'
    if (x > 10) throw 'too high'
  } catch (err) {
    console.log(err)
  }
}
throwErrorExampleFun()
```

### Tipe Error

- ReferenceError: Terjadi referensi yang nggak valid. Dilempar kalau kita pake variabel yang belum dideklarasiin.

```js
let firstName = 'Asabeneh'
let fullName = firstName + ' ' + lastName

console.log(fullName)
```

```sh
Uncaught ReferenceError: lastName is not defined
    at <anonymous>:2:35
```

- SyntaxError: Ada yang salah sama sintaks kodenya.

```js
let square = 2 x 2
console.log(square)

console.log('Hello, world')
```

```sh
Uncaught SyntaxError: Unexpected identifier
```

- TypeError: Kesalahan tipe data nih.

```js
let num = 10
console.log(num.toLowerCase())
```

```sh
Uncaught TypeError: num.toLowerCase is not a function
    at <anonymous>:2:17
```

Ini beberapa error umum yang mungkin sering kamu temuin pas ngoding. Paham error itu penting banget, karena dari situ kamu bisa tau salahnya di mana dan bisa debug kode dengan lebih cepat. Jangan takut error ya!

🌕 Kamu makin jago nih! Sekarang kamu udah ngerti gimana cara nanganin error dan bisa nulis aplikasi yang tangguh yang bisa ngadepin input user yang nggak terduga. Kamu baru aja nuntasin tantangan hari ke-14 dan udah 14 langkah lebih dekat menuju level dewa. Yuk gaskeun latihan!

## Latihan

### Latihan: Level 1

Praktik

### Latihan: Level 2

Praktik

### Latihan: Level 3

Praktik

🎉 SELAMAT ! 🎉
