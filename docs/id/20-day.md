# 📘 Hari 20

## Menulis kode yang bersih (clean code)

### Panduan Gaya JavaScript (JavaScript Style Guide)

Panduan gaya JavaScript itu kayak "rule of thumb" — seperangkat standar yang ngejelasin gimana kode JavaScript seharusnya ditulis dan diorganisir. Di bagian ini kita bakal ngobrolin panduan JavaScript dan gimana cara nulis kode yang bersih biar enak dilihat.

JavaScript itu bahasa pemrograman, dan kayak bahasa manusia, dia punya sintaks. Sintaks JavaScript harus ditulis ngikutin pedoman gaya tertentu biar nyaman dan simpel.

### Kenapa sih kita butuh panduan gaya?

Bayangin nih, kamu selama ini ngoding sendirian santuy-santuy aja. Terus tiba-tiba harus kerja bareng tim. Sebenernya gak masalah gimana pun kamu nulis kode selama kodenya jalan. Tapi pas kamu kerja di tim berisi 10 atau 20 atau bahkan lebih developer di satu proyek dan codebase yang sama, kode bakal jadi berantakan dan susah di-maintain kalau gak ada pedoman yang diikutin. Nah lho!

Kamu bisa bikin pedoman dan konvensi sendiri, atau bisa juga adaptasi dari pedoman yang udah established dan terkenal. Yuk kita liat pedoman yang paling umum dikenal.

Panduan Gaya JavaScript yang Paling Umum

- Airbnb JavaScript Style Guide
- JavaScript Standard Style Guide
- Google JavaScript Style Guide

#### Airbnb JavaScript Style Guide

Airbnb punya salah satu panduan gaya JavaScript paling populer di internet. Panduan ini udah mencakup hampir semua aspek JavaScript dan diadopsi banyak developer dan perusahaan. Cek aja [panduan gaya Airbnb](https://github.com/airbnb/javascript). Saya juga rekomen banget buat nyobain. Gaya mereka gampang dipake dan simpel dipahami.

#### Standard JavaScript Style Guide

Pedoman ini gak sepopuler Airbnb sih, tapi tetep worth it buat dilirik. Mereka ngehilangin titik koma di [panduan gaya](https://standardjs.com/) mereka. Unik ya!

#### Google JavaScript Style Guide

Jujur nih saya gak banyak ngomong soal pedoman Google dan belum pernah pake, tapi saya saranin kamu liat dari [tautan](https://google.github.io/styleguide/jsguide.html) ini.

### Konvensi Penulisan JavaScript

Di tantangan ini kita juga pake konvensi dan panduan penulisan JavaScript umum. Konvensi penulisan itu pedoman gaya buat programming yang dikembangin sama individu, tim, atau perusahaan.

Konvensi penulisan bantu:

- nulis kode yang bersih
- ningkatin keterbacaan kode
- ningkatin reusability dan maintainability kode

Konvensi penulisan mencakup:

- Aturan penamaan dan deklarasi buat variabel
- Aturan penamaan dan deklarasi buat fungsi
- Aturan penggunaan spasi, indentasi, dan komentar
- Praktik dan prinsip pemrograman

#### Konvensi yang digunakan di 30DaysOfJavaScript

Di tantangan ini kita ngikutin konvensi JavaScript reguler, tapi saya juga nambahin preferensi penulisan pribadi nih:

- Kita pake camelCase buat variabel dan fungsi.
- Semua nama variabel dimulai dengan huruf.
- Kita pilih pake *const* buat konstanta, array, objek, dan fungsi. Alih-alih double quotes, kita pilih pake single quotes atau backtick. Single quotes makin populer lho!
- Kita juga ngilangin titik koma dari kode kita, tapi ini sih masalah selera pribadi aja.
- Spasi di sekitar operator aritmatika, operator penugasan, dan setelah koma
- Arrow function alih-alih deklarasi fungsi
- Explicit return alih-alih implicit return kalo fungsinya cuma satu baris
- Gak pake koma di akhir nilai terakhir sebuah objek
- Kita lebih prefer +=, -=, *= /=, **= alih-alih versi yang lebih panjang
- Pas kita pake console.log(), selalu pake string tag biar tau dari mana konsol itu berasal

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

Kita prefer bikin nama array dalam bentuk jamak (plural):

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

Sekarang kamu pasti udah jago banget soal deklarasi fungsi, function expression, arrow function, dan anonymous function. Di tantangan ini kita condong pake arrow function dibanding fungsi lainnya. Tapi inget, arrow function bukan pengganti fungsi lain ya! Arrow function dan deklarasi fungsi itu gak sepenuhnya sama. Jadi kamu harus tau kapan pake yang mana. Saya bakal bahas detailnya di bagian lain nanti. Kita bakal pake explicit return alih-alih implicit return kalo fungsinya satu baris.

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

`new Date().toLocaleString()` juga bisa dipake buat nampilin tanggal dan waktu saat ini. Metode `toLocaleString()` nerima argumen yang beda-beda. Kamu bisa pelajarin lebih lanjut soal tanggal dan waktu dari [tautan](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/toLocaleString) ini.

#### Perulangan (Loops)

Kita udah bahas banyak jenis perulangan di tantangan ini. For loop biasa, while loop, do while loop, for of loop, forEach loop, dan for in loop.
Yuk liat gimana kita makenya:

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

Kita deklarasiin objek literal pake *const*.

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

Kita udah bahas if, if else, if else if else, switch, dan operator ternary di tantangan-tantangan sebelumnya.

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

Kita deklarasiin kelas pake CamelCase yang dimulai dengan huruf kapital.

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

Apapun panduan gaya yang kamu ikutin, yang penting konsisten ya! Ikutin beberapa paradigma pemrograman dan pola desain. Inget, kalau kamu gak nulis kode dengan urutan atau cara tertentu, kode kamu bakal susah dibaca. Jadi, bantulah diri kamu sendiri atau orang lain yang bakal baca kode kamu dengan nulis kode yang gampang dibaca. Oke gas!

🌕 Kamu udah makin rapi dan pro! Sekarang kamu tau cara nulis kode yang bersih, jadi siapapun yang ngerti JavaScript bakal paham kode kamu. Kamu terus maju dan udah 20 langkah lebih maju menuju kehebatan. Luar biasa!

🎉 SELAMAT ! 🎉
