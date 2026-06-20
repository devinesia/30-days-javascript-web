# 📔 Hari 8

## Scope (Ruang Lingkup)

Variabel adalah bagian fundamental dalam pemrograman. Kita mendeklarasikan variabel untuk menyimpan berbagai tipe data. Untuk mendeklarasikan variabel kita menggunakan kata kunci _var_, _let_ dan _const_. Sebuah variabel dapat dideklarasikan pada scope yang berbeda. Di bagian ini, kita akan melihat scope variabel, scope variabel ketika kita menggunakan var atau let.
Scope variabel dapat berupa:

- Global
- Local

Variabel dapat dideklarasikan pada scope global atau lokal. Kita akan melihat kedua scope global dan lokal.
Apa pun yang dideklarasikan tanpa let, var atau const memiliki scope pada level global.

Mari kita bayangkan kita memiliki file scope.js.

### Window Global Object

Tanpa menggunakan `console.log()` buka browser Anda dan periksa, Anda akan melihat nilai a dan b jika Anda menulis a atau b di browser. Itu berarti a dan b sudah tersedia di window.

```js
//scope.js
a = 'JavaScript' // mendeklarasikan variabel tanpa let atau const membuatnya tersedia di objek window dan ini ditemukan di mana saja
b = 10 // ini adalah variabel scope global dan ditemukan di objek window
function letsLearnScope() {
  console.log(a, b)
  if (true) {
    console.log(a, b)
  }
}
console.log(a, b) // dapat diakses
```

### Global scope

Variabel yang dideklarasikan secara global dapat diakses di mana saja dalam file yang sama. Tetapi istilah global bersifat relatif. Bisa global terhadap file atau bisa global relatif terhadap beberapa blok kode.

```js
//scope.js
let a = 'JavaScript' // adalah global scope, akan ditemukan di mana saja dalam file ini
let b = 10 // adalah global scope, akan ditemukan di mana saja dalam file ini
function letsLearnScope() {
  console.log(a, b) // JavaScript 10, dapat diakses
  if (true) {
    let a = 'Python'
    let b = 100
    console.log(a, b) // Python 100
  }
  console.log(a, b)
}
letsLearnScope()
console.log(a, b) // JavaScript 10, dapat diakses
```

### Local scope

Variabel yang dideklarasikan sebagai lokal hanya dapat diakses di blok kode tertentu.

- Block Scope
- Function Scope

```js
//scope.js
let a = 'JavaScript' // adalah global scope, akan ditemukan di mana saja dalam file ini
let b = 10 // adalah global scope, akan ditemukan di mana saja dalam file ini
// Function scope
function letsLearnScope() {
  console.log(a, b) // JavaScript 10, dapat diakses
  let value = false
// block scope
  if (true) {
    // kita dapat mengakses dari dalam fungsi dan di luar fungsi tetapi 
    // variabel yang dideklarasikan di dalam if tidak akan dapat diakses di luar blok if
    let a = 'Python'
    let b = 20
    let c = 30
    let d = 40
    value = !value
    console.log(a, b, c, value) // Python 20 30 true
  }
  // kita tidak dapat mengakses c karena scope c hanya di dalam blok if
  console.log(a, b, value) // JavaScript 10 true
}
letsLearnScope()
console.log(a, b) // JavaScript 10, dapat diakses
```

Sekarang, Anda sudah memahami scope. Variabel yang dideklarasikan dengan *var* hanya ter-scope ke fungsi tetapi variabel yang dideklarasikan dengan *let* atau *const* adalah block scope (blok fungsi, blok if, blok loop, dll). Blok di JavaScript adalah kode di antara dua kurung kurawal ({}).

```js
//scope.js
function letsLearnScope() {
  var gravity = 9.81
  console.log(gravity)

}
// console.log(gravity), Uncaught ReferenceError: gravity is not defined

if (true){
  var gravity = 9.81
  console.log(gravity) // 9.81
}
console.log(gravity)  // 9.81

for(var i = 0; i < 3; i++){
  console.log(i) // 0, 1, 2
}
console.log(i) // 3

```

Di ES6 ke atas sudah ada *let* dan *const*, jadi Anda tidak akan menderita karena sifat licik *var*. Ketika kita menggunakan *let*, variabel kita adalah block scoped dan tidak akan mempengaruhi bagian lain dari kode kita.

```js
//scope.js
function letsLearnScope() {
  // Anda bisa menggunakan let atau const, tetapi gravity adalah konstanta, saya lebih suka menggunakan const
  const gravity = 9.81
  console.log(gravity)

}
// console.log(gravity), Uncaught ReferenceError: gravity is not defined

if (true){
  const  gravity = 9.81
  console.log(gravity) // 9.81
}
// console.log(gravity), Uncaught ReferenceError: gravity is not defined

for(let i = 0; i < 3; i++){
  console.log(i) // 0, 1, 2
}
// console.log(i), Uncaught ReferenceError: i is not defined

```

Scope *let* dan *const* adalah sama. Perbedaannya hanya pada reassigning (penetapan ulang). Kita tidak dapat mengubah atau menetapkan ulang nilai variabel `const`. Saya sangat menyarankan Anda untuk menggunakan *let* dan *const*, dengan menggunakan *let* dan *const* Anda akan menulis kode yang bersih dan menghindari kesalahan yang sulit di-debug. Sebagai aturan praktis, Anda dapat menggunakan *let* untuk nilai apa pun yang berubah, *const* untuk nilai konstan apa pun, dan untuk array, objek, arrow function, dan function expression.

## 📔 Objek (Object)

Segala sesuatu bisa menjadi objek dan objek memiliki properti dan properti memiliki nilai, jadi objek adalah pasangan kunci-nilai (key-value pair). Urutan kunci tidak dipertahankan, atau tidak ada urutan.
Untuk membuat objek literal, kita menggunakan dua kurung kurawal.

### Membuat objek kosong

Objek kosong

```js
const person = {}
```

### Membuat objek dengan nilai

Sekarang, objek person memiliki properti firstName, lastName, age, location, skills dan isMarried. Nilai dari properti atau kunci bisa berupa string, number, boolean, objek, null, undefined atau fungsi.

Mari kita lihat beberapa contoh objek. Setiap kunci memiliki nilai dalam objek.

```js
const rectangle = {
  length: 20,
  width: 20
}
console.log(rectangle) // {length: 20, width: 20}

const person = {
  firstName: 'Asabeneh',
  lastName: 'Yetayeh',
  age: 250,
  country: 'Finland',
  city: 'Helsinki',
  skills: [
    'HTML',
    'CSS',
    'JavaScript',
    'React',
    'Node',
    'MongoDB',
    'Python',
    'D3.js'
  ],
  isMarried: true
}
console.log(person)
```

### Mengambil nilai dari objek

Kita dapat mengakses nilai objek menggunakan dua metode:

- menggunakan . diikuti oleh nama kunci jika nama kunci adalah satu kata
- menggunakan kurung siku dan tanda kutip

```js
const person = {
  firstName: 'Asabeneh',
  lastName: 'Yetayeh',
  age: 250,
  country: 'Finland',
  city: 'Helsinki',
  skills: [
    'HTML',
    'CSS',
    'JavaScript',
    'React',
    'Node',
    'MongoDB',
    'Python',
    'D3.js'
  ],
  getFullName: function() {
    return `${this.firstName}${this.lastName}`
  },
  'phone number': '+3584545454545'
}

// mengakses nilai menggunakan .
console.log(person.firstName)
console.log(person.lastName)
console.log(person.age)
console.log(person.location) // undefined

// nilai dapat diakses menggunakan kurung siku dan nama kunci
console.log(person['firstName'])
console.log(person['lastName'])
console.log(person['age'])
console.log(person['age'])
console.log(person['location']) // undefined

// misalnya untuk mengakses nomor telepon kita hanya menggunakan metode kurung siku
console.log(person['phone number'])
```

### Membuat metode objek

Sekarang, objek person memiliki properti getFullName. getFullName adalah fungsi di dalam objek person dan kita menyebutnya metode objek. Kata kunci _this_ merujuk pada objek itu sendiri. Kita dapat menggunakan kata _this_ untuk mengakses nilai dari berbagai properti objek. Kita tidak dapat menggunakan arrow function sebagai metode objek karena kata this merujuk ke window di dalam arrow function, bukan ke objek itu sendiri. Contoh objek:

```js
const person = {
  firstName: 'Asabeneh',
  lastName: 'Yetayeh',
  age: 250,
  country: 'Finland',
  city: 'Helsinki',
  skills: [
    'HTML',
    'CSS',
    'JavaScript',
    'React',
    'Node',
    'MongoDB',
    'Python',
    'D3.js'
  ],
  getFullName: function() {
    return `${this.firstName} ${this.lastName}`
  }
}

console.log(person.getFullName())
// Asabeneh Yetayeh
```

### Menetapkan kunci baru untuk objek

Objek adalah struktur data yang mutable (dapat diubah) dan kita dapat memodifikasi konten objek setelah dibuat.

Menetapkan kunci baru dalam objek

```js
const person = {
  firstName: 'Asabeneh',
  lastName: 'Yetayeh',
  age: 250,
  country: 'Finland',
  city: 'Helsinki',
  skills: [
    'HTML',
    'CSS',
    'JavaScript',
    'React',
    'Node',
    'MongoDB',
    'Python',
    'D3.js'
  ],
  getFullName: function() {
    return `${this.firstName} ${this.lastName}`
  }
}
person.nationality = 'Ethiopian'
person.country = 'Finland'
person.title = 'teacher'
person.skills.push('Meteor')
person.skills.push('SasS')
person.isMarried = true

person.getPersonInfo = function() {
  let skillsWithoutLastSkill = this.skills
    .splice(0, this.skills.length - 1)
    .join(', ')
  let lastSkill = this.skills.splice(this.skills.length - 1)[0]

  let skills = `${skillsWithoutLastSkill}, and ${lastSkill}`
  let fullName = this.getFullName()
  let statement = `${fullName} is a ${this.title}.\nHe lives in ${this.country}.\nHe teaches ${skills}.`
  return statement
}
console.log(person)
console.log(person.getPersonInfo())
```

```sh
Asabeneh Yetayeh is a teacher.
He lives in Finland.
He teaches HTML, CSS, JavaScript, React, Node, MongoDB, Python, D3.js, Meteor, and SasS.
```

### Metode Objek (Object Methods)

Ada berbagai metode untuk memanipulasi objek. Mari kita lihat beberapa metode yang tersedia.

_Object.assign_: Untuk menyalin objek tanpa memodifikasi objek asli

```js
const person = {
  firstName: 'Asabeneh',
  age: 250,
  country: 'Finland',
  city:'Helsinki',
  skills: ['HTML', 'CSS', 'JS'],
  title: 'teacher',
  address: {
    street: 'Heitamienkatu 16',
    pobox: 2002,
    city: 'Helsinki'
  },
  getPersonInfo: function() {
    return `I am ${this.firstName} and I live in ${this.city}, ${this.country}. I am ${this.age}.`
  }
}

//Object methods: Object.assign, Object.keys, Object.values, Object.entries
//hasOwnProperty

const copyPerson = Object.assign({}, person)
console.log(copyPerson)
```

#### Mendapatkan kunci objek menggunakan Object.keys()

_Object.keys_: Untuk mendapatkan kunci atau properti dari objek sebagai array

```js
const keys = Object.keys(copyPerson)
console.log(keys) //['firstName', 'age', 'country','city', 'skills','title', 'address', 'getPersonInfo']
const address = Object.keys(copyPerson.address)
console.log(address) //['street', 'pobox', 'city']
```

#### Mendapatkan nilai objek menggunakan Object.values()

_Object.values_: Untuk mendapatkan nilai dari objek sebagai array

```js
const values = Object.values(copyPerson)
console.log(values)
```

#### Mendapatkan kunci dan nilai objek menggunakan Object.entries()

_Object.entries_: Untuk mendapatkan kunci dan nilai dalam array

```js
const entries = Object.entries(copyPerson)
console.log(entries)
```

#### Memeriksa properti menggunakan hasOwnProperty()

_hasOwnProperty_: Untuk memeriksa apakah kunci atau properti tertentu ada dalam objek

```js
console.log(copyPerson.hasOwnProperty('name'))
console.log(copyPerson.hasOwnProperty('score'))
```

🌕 Anda luar biasa. Sekarang, Anda sudah terisi penuh dengan kekuatan objek. Anda baru saja menyelesaikan tantangan hari ke-8 dan Anda selangkah lebih maju menuju kehebatan. Sekarang lakukan beberapa latihan untuk otak dan otot Anda.

## 💻 Latihan

### Latihan: Level 1

1. Buat objek kosong bernama dog
1. Cetak objek dog di konsol
1. Tambahkan properti name, legs, color, age dan bark untuk objek dog. Properti bark adalah metode yang mengembalikan _woof woof_
1. Dapatkan nilai name, legs, color, age dan bark dari objek dog
1. Tetapkan properti baru pada objek dog: breed, getDogInfo

### Latihan: Level 2

1. Temukan orang yang memiliki banyak skill di objek users.
1. Hitung pengguna yang logged in, hitung pengguna yang memiliki poin lebih besar atau sama dengan 50 dari objek berikut.

```js
 const users = {
   Alex: {
     email: "alex@alex.com",
     skills: ["HTML", "CSS", "JavaScript"],
     age: 20,
     isLoggedIn: false,
     points: 30
   },
   Asab: {
     email: "asab@asab.com",
     skills: ["HTML", "CSS", "JavaScript", "Redux", "MongoDB", "Express", "React", "Node"],
     age: 25,
     isLoggedIn: false,
     points: 50
   },
   Brook: {
     email: "daniel@daniel.com",
     skills: ["HTML", "CSS", "JavaScript", "React", "Redux"],
     age: 30,
     isLoggedIn: true,
     points: 50
   },
   Daniel: {
     email: "daniel@alex.com",
     skills: ["HTML", "CSS", "JavaScript", "Python"],
     age: 20,
     isLoggedIn: false,
     points: 40
   },
   John: {
     email: "john@john.com",
     skills: ["HTML", "CSS", "JavaScript", "React", "Redux", "Node.js"],
     age: 20,
     isLoggedIn: true,
     points: 50
   },
   Thomas: {
     email: "thomas@thomas.com",
     skills: ["HTML", "CSS", "JavaScript", "React"],
     age: 20,
     isLoggedIn: false,
     points: 40
   },
   Paul: {
     email: "paul@paul.com",
     skills: ["HTML", "CSS", "JavaScript", "MongoDB", "Express", "React", "Node"],
     age: 20,
     isLoggedIn: false,
     points: 40
   }
 }
```

1. Temukan orang yang merupakan MERN stack developer dari objek users
1. Tetapkan nama Anda di objek users tanpa memodifikasi objek users asli
1. Dapatkan semua kunci atau properti dari objek users
1. Dapatkan semua nilai dari objek users
1. Gunakan objek countries untuk mencetak nama negara, ibu kota, populasi, dan bahasa.

### Latihan: Level 3

1. Buat objek literal bernama _personAccount_. Objek ini memiliki properti _firstName, lastName, incomes, expenses_ dan memiliki metode _totalIncome, totalExpense, accountInfo, addIncome, addExpense_ dan _accountBalance_. Incomes adalah kumpulan pendapatan dan deskripsinya dan expenses adalah kumpulan pengeluaran dan deskripsinya.
2. **** Pertanyaan: 2, 3 dan 4 didasarkan pada dua array berikut: users dan products ()

  ```js
      const users = [
      {
          _id: 'ab12ex',
          username: 'Alex',
          email: 'alex@alex.com',
          password: '123123',
          createdAt:'08/01/2020 9:00 AM',
          isLoggedIn: false
      },
      {
          _id: 'fg12cy',
          username: 'Asab',
          email: 'asab@asab.com',
          password: '123456',
          createdAt:'08/01/2020 9:30 AM',
          isLoggedIn: true
      },
      {
          _id: 'zwf8md',
          username: 'Brook',
          email: 'brook@brook.com',
          password: '123111',
          createdAt:'08/01/2020 9:45 AM',
          isLoggedIn: true
      },
      {
          _id: 'eefamr',
          username: 'Martha',
          email: 'martha@martha.com',
          password: '123222',
          createdAt:'08/01/2020 9:50 AM',
          isLoggedIn: false
      },
      {
          _id: 'ghderc',
          username: 'Thomas',
          email: 'thomas@thomas.com',
          password: '123333',
          createdAt:'08/01/2020 10:00 AM',
          isLoggedIn: false
      }
      ];

      const products = [
    {
      _id: 'eedfcf',
      name: 'mobile phone',
      description: 'Huawei Honor',
      price: 200,
      ratings: [
        { userId: 'fg12cy', rate: 5 },
        { userId: 'zwf8md', rate: 4.5 }
      ],
      likes: []
    },
    {
      _id: 'aegfal',
      name: 'Laptop',
      description: 'MacPro: System Darwin',
      price: 2500,
      ratings: [],
      likes: ['fg12cy']
    },
    {
      _id: 'hedfcg',
      name: 'TV',
      description: 'Smart TV:Procaster',
      price: 400,
      ratings: [{ userId: 'fg12cy', rate: 5 }],
      likes: ['fg12cy']
    }
  ]
  ```

  Bayangkan Anda mendapatkan koleksi users di atas dari database MongoDB.
    a. Buat fungsi bernama signUp yang memungkinkan pengguna untuk ditambahkan ke koleksi. Jika pengguna sudah ada, beri tahu pengguna bahwa dia sudah memiliki akun.  
    b. Buat fungsi bernama signIn yang memungkinkan pengguna untuk masuk ke aplikasi  

3. Array products memiliki tiga elemen dan masing-masing memiliki enam properti.
    a. Buat fungsi bernama rateProduct yang menilai produk
    b. Buat fungsi bernama averageRating yang menghitung rata-rata penilaian suatu produk  

4. Buat fungsi bernama likeProduct. Fungsi ini akan membantu untuk menyukai produk jika belum disukai dan menghapus like jika sudah disukai.


🎉 SELAMAT ! 🎉
