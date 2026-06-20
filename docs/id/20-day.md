# 📘 Hari 20

## Menulis kode yang bersih (clean code)

### Panduan Gaya JavaScript (JavaScript Style Guide)

Panduan gaya JavaScript adalah seperangkat standar yang menjelaskan bagaimana kode JavaScript harus ditulis dan diorganisir. Di bagian ini, kita akan membahas panduan JavaScript dan cara menulis kode yang bersih.

JavaScript adalah bahasa pemrograman dan seperti bahasa manusia, ia memiliki sintaksis. Sintaksis JavaScript harus ditulis mengikuti pedoman gaya tertentu demi kenyamanan dan kesederhanaan.

### Mengapa kita membutuhkan panduan gaya

Anda telah berkoding sendiri untuk waktu yang lama tetapi sekarang tampaknya harus bekerja dalam tim. Tidak masalah bagaimana pun Anda menulis kode selama kode itu berjalan, namun ketika Anda bekerja dalam tim yang terdiri dari 10 atau 20 atau lebih developer pada satu proyek dan basis kode yang sama, kode akan menjadi berantakan dan sulit dikelola jika tidak ada pedoman yang diikuti.

Anda dapat mengembangkan pedoman dan konvensi sendiri atau Anda juga dapat mengadaptasi pedoman yang sudah berkembang baik. Mari kita lihat pedoman yang paling umum dikenal.
Panduan Gaya JavaScript yang Paling Umum

- Airbnb JavaScript Style Guide
- JavaScript Standard Style Guide
- Google JavaScript Style Guide

#### Airbnb JavaScript Style Guide

Airbnb memiliki salah satu panduan gaya JavaScript paling populer di internet. Panduan ini mencakup hampir setiap aspek JavaScript dan diadopsi oleh banyak developer dan perusahaan. Anda dapat melihat [panduan gaya Airbnb](https://github.com/airbnb/javascript). Saya juga merekomendasikan untuk mencobanya. Gaya mereka sangat mudah digunakan dan sederhana untuk dipahami.

#### Standard JavaScript Style Guide

Pedoman ini tidak sepopuler Airbnb tetapi layak untuk dilihat. Mereka menghilangkan titik koma dalam [panduan gaya](https://standardjs.com/) mereka.

#### Google JavaScript Style Guide

Saya tidak banyak bicara tentang pedoman Google dan saya belum menggunakannya, tetapi saya sarankan Anda untuk melihatnya dari [tautan](https://google.github.io/styleguide/jsguide.html) ini.

### Konvensi Penulisan JavaScript

Dalam tantangan ini juga kita menggunakan konvensi dan panduan penulisan JavaScript umum. Konvensi penulisan adalah pedoman gaya untuk pemrograman yang dikembangkan oleh individu, tim, atau perusahaan.

Konvensi penulisan membantu:

- menulis kode yang bersih
- meningkatkan keterbacaan kode
- meningkatkan penggunaan kembali (reusability) dan kemudahan pemeliharaan kode (maintainability)

Konvensi penulisan mencakup

- Aturan penamaan dan deklarasi untuk variabel
- Aturan penamaan dan deklarasi untuk fungsi
- Aturan penggunaan spasi, indentasi, dan komentar
- Praktik dan prinsip pemrograman

#### Konvensi yang digunakan di 30DaysOfJavaScript

Dalam tantangan ini kita mengikuti konvensi JavaScript reguler tetapi saya juga menambahkan preferensi penulisan saya.

- Kita menggunakan camelCase untuk variabel dan fungsi.
- Semua nama variabel dimulai dengan huruf.
- Kita memilih untuk menggunakan *const* untuk konstanta, array, objek, dan fungsi. Alih-alih tanda kutip ganda, kita memilih menggunakan tanda kutip tunggal atau backtick. Tanda kutip tunggal semakin populer.
- Kita juga menghilangkan titik koma dari kode kita tetapi ini masalah preferensi pribadi.
- Spasi di sekitar operator aritmatika, operator penugasan, dan setelah koma
- Arrow function alih-alih deklarasi fungsi
- Explicit return alih-alih implicit return jika fungsinya satu baris
- Tidak ada koma di akhir nilai terakhir dari sebuah objek
- Kita lebih memilih +=, -=, *= /=, **= alih-alih versi yang lebih panjang
- Saat kita menggunakan console.log(), baik untuk mencetak dengan string tag untuk mengidentifikasi dari mana konsol itu berasal

#### Variabel

```js

let firstName = 'Asabeneh'
let lastName = 'Yetayeh'
let country = 'Finland'
let city = 'Helsinki'

const PI = Math.PI
const gravity = 9.81
```

#### Array

Kita memilih untuk membuat nama array dalam bentuk jamak (plural)

- names
- numbers
- countries
- languages
- skills
- fruits
- vegetables

```js
// arrays
const names = ['Asabeneh', 'Mathias', 'Elias', 'Brook']
const numbers = [0, 3.14, 9.81, 37, 98.6, 100]
const countries = ['Finland', 'Denmark', 'Sweden', 'Norway', 'Iceland']
const languages = ['Amharic', 'Arabic', 'English', 'French', 'Spanish']
const skills = ['HTML', 'CSS', 'JavaScript', 'React', 'Python']
const fruits = ['banana', 'orange', 'mango', 'lemon']
const vegetables = ['Tomato', 'Potato', 'Cabbage', 'Onion', 'Carrot']
```

#### Fungsi

Sekarang Anda sudah sangat familiar dengan deklarasi fungsi, expression function, arrow function, dan anonymous function. Dalam tantangan ini kita cenderung menggunakan arrow function dibandingkan fungsi lainnya. Arrow function bukanlah pengganti untuk fungsi lainnya. Selain itu, arrow function dan deklarasi fungsi tidak persis sama. Jadi Anda harus tahu kapan menggunakannya dan kapan tidak. Saya akan membahas perbedaannya secara detail di bagian lain. Kita akan menggunakan explicit return alih-alih implicit return jika fungsinya satu baris.

```js
// function which return full name of a person
const printFullName = (firstName, lastName) => firstName + ' ' + lastName

// function which calculates a square of a number
const square = (n) => n * n

// a function which generate random hexa colors
const hexaColor = () => {
  const str = '0123456789abcdef'
  let hexa = '#'
  let index
  for (let i = 0; i < 6; i++) {
    index = Math.floor(Math.random() * str.length)
    hexa += str[index]
  }
  return hexa
}

// a function which shows date and time
const showDateTime = () => {
  const now = new Date()
  const year = now.getFullYear()
  const month = now.getMonth() + 1
  const date = now.getDate()
  let hours = now.getHours()
  let minutes = now.getMinutes()
  if (hours < 10) {
    hours = '0' + hours
  }
  if (minutes < 10) {
    minutes = '0' + minutes
  }

  const dateMonthYear = date + '.' + month + '.' + year
  const time = hours + ':' + minutes
  const fullTime = dateMonthYear + ' ' + time
  return fullTime
}
```

`new Date().toLocaleString()` juga dapat digunakan untuk menampilkan tanggal dan waktu saat ini. Metode `toLocaleString()` menerima argumen yang berbeda. Anda dapat mempelajari lebih lanjut tentang tanggal dan waktu dari [tautan](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/toLocaleString) ini.

#### Perulangan (Loops)

Kita telah membahas banyak jenis perulangan dalam tantangan ini. For loop biasa, while loop, do while loop, for of loop, forEach loop, dan for in loop.
Mari kita lihat bagaimana kita menggunakannya:

```js
for (let i = 0; i < n; i++){
    console.log()
}

// declaring an array variable
const names = ['Asabeneh', 'Mathias', 'Elias', 'Brook']

// iterating an array using regular for loop
let len = names.length;
for(let i = 0; i < len; i++){
    console.log(names[i].toUpperCase())
}


// iterating an array using for of
for( const name of names) {
    console.log(name.toUpperCase())
}

// iterating array using forEach 
names.forEach((name) => name.toUpperCase())


const person = {
  firstName: 'Asabeneh',
  lastName: 'Yetayeh',
  age: 250,
  country: 'Finland',
  city: 'Helsinki',
  skills: ['HTML','CSS','JavaScript','React','Node','MongoDB','Python','D3.js'],
  isMarried: true
}
for(const key in person) {
    console.log(key)
}

```

#### Objek

Kita mendeklarasikan objek literal dengan *const*.

```js
// declaring object literal
const person = {
  firstName: 'Asabeneh',
  lastName: 'Yetayeh',
  age: 250,
  country: 'Finland',
  city: 'Helsinki',
  skills: ['HTML','CSS','JavaScript','TypeScript', 'React','Node','MongoDB','Python','D3.js'],
  isMarried: true
}
// iterating through object keys
for(const key in person) {
    console.log(key, person[key])
}

```

#### Kondisional

Kita telah membahas if, if else, if else if else, switch, dan operator ternary di tantangan-tantangan sebelumnya.

```js
 // syntax
if (condition) {
  // this part of code run for truthy condition
} else {
  // this part of code run for false condition
}
```

```js
 // if else
let num = 3
if (num > 0) {
  console.log(`${num} is a positive number`)
} else {
  console.log(`${num} is a negative number`)
}
//  3 is a positive number
```

```js
 // if else if else if else

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
 // Switch More Examples
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

```js
 // ternary

 let isRaining = true
isRaining
  ? console.log('You need a rain coat.')
  : console.log('No need for a rain coat.')
```

#### Kelas (Classes)

Kita mendeklarasikan kelas dengan CamelCase yang dimulai dengan huruf kapital.

```js
// syntax
class ClassName {
    // code goes here
}
```

```js
// defining class
class Person {
  constructor(firstName, lastName) {
    console.log(this) // Check the output from here
    this.firstName = firstName
    this.lastName = lastName
  }
}

```

Apapun panduan gaya yang Anda ikuti, tetaplah konsisten. Ikuti beberapa paradigma pemrograman dan pola desain. Ingat, jika Anda tidak menulis kode dalam urutan atau cara tertentu, akan sulit untuk membaca kode Anda. Jadi, bantulah diri Anda sendiri atau orang lain yang akan membaca kode Anda dengan menulis kode yang mudah dibaca.

🌕 Anda rapi. Sekarang, Anda tahu cara menulis kode yang bersih, sehingga siapa pun yang mengerti bahasa Inggris dapat memahami kode Anda. Anda selalu maju dan Anda telah 20 langkah lebih maju menuju kehebatan.

🎉 SELAMAT ! 🎉
