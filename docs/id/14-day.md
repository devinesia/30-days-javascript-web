# 📘 Hari 14

## Penanganan Error

JavaScript adalah bahasa dengan tipe data yang longgar (loosely-typed). Terkadang Anda akan mendapatkan error runtime saat mencoba mengakses variabel yang tidak terdefinisi atau memanggil fungsi yang tidak terdefinisi, dan sebagainya.

JavaScript, mirip dengan Python atau Java, menyediakan mekanisme penanganan error untuk menangkap error runtime menggunakan blok try-catch-finally.

```js
try {
  // code that may throw an error
} catch (err) {
  // code to be executed if an error occurs
} finally {
  // code to be executed regardless of an error occurs or not
}
```

**try**: bungkus kode mencurigakan yang mungkin melempar error di dalam blok try. Pernyataan try memungkinkan kita mendefinisikan blok kode yang akan diuji terhadap error saat dieksekusi.

**catch**: tulis kode untuk melakukan sesuatu di blok catch ketika error terjadi. Blok catch dapat memiliki parameter yang akan memberikan informasi error. Blok catch digunakan untuk mencatat error atau menampilkan pesan spesifik kepada pengguna.

**finally**: blok finally akan selalu dieksekusi terlepas dari terjadi tidaknya error. Blok finally dapat digunakan untuk menyelesaikan tugas yang tersisa atau mengatur ulang variabel yang mungkin telah berubah sebelum error terjadi di blok try.

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

Blok catch menerima sebuah parameter. Umumnya kita memberikan e, err, atau error sebagai parameter ke blok catch. Parameter ini adalah sebuah objek dan memiliki properti name dan message. Mari kita gunakan name dan message.

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

throw: pernyataan throw memungkinkan kita membuat error kustom. Kita dapat melempar string, number, boolean, atau objek. Gunakan pernyataan throw untuk melempar exception. Ketika Anda melempar exception, expression menentukan nilai dari exception tersebut. Setiap pernyataan berikut melempar exception:

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

- ReferenceError: Terjadi referensi yang tidak sah. ReferenceError dilempar jika kita menggunakan variabel yang belum dideklarasikan.

```js
let firstName = 'Asabeneh'
let fullName = firstName + ' ' + lastName

console.log(fullName)
```

```sh
Uncaught ReferenceError: lastName is not defined
    at <anonymous>:2:35
```

- SyntaxError: Telah terjadi error sintaks

```js
let square = 2 x 2
console.log(square)

console.log('Hello, world')
```

```sh
Uncaught SyntaxError: Unexpected identifier
```

- TypeError: Telah terjadi error tipe

```js
let num = 10
console.log(num.toLowerCase())
```

```sh
Uncaught TypeError: num.toLowerCase is not a function
    at <anonymous>:2:17
```

Ini adalah beberapa error umum yang mungkin Anda hadapi saat menulis kode. Memahami error dapat membantu Anda mengetahui kesalahan apa yang Anda buat dan akan membantu Anda melakukan debug kode dengan cepat.

🌕 Anda sempurna. Sekarang, Anda tahu cara menangani error dan dapat menulis aplikasi yang tangguh yang menangani input pengguna yang tidak terduga. Anda baru saja menyelesaikan tantangan hari ke-14 dan Anda 14 langkah lebih maju menuju kehebatan. Sekarang lakukan beberapa latihan untuk otak dan otot Anda.

## Latihan

### Latihan: Level 1

Praktik

### Latihan: Level 2

Praktik

### Latihan: Level 3

Praktik

🎉 SELAMAT ! 🎉
