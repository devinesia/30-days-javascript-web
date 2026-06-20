# 📔 Hari 8

## Scope (Ruang Lingkup)

Variabel tuh bagian fundamental banget dalam pemrograman. Kita deklarasiin variabel buat nyimpen berbagai tipe data. Buat deklarasiin variabel, kita pakai kata kunci _var_, _let_ dan _const_. Sebuah variabel bisa dideklarasiin di scope yang beda-beda. Di bagian ini, kita bakal bahas scope variabel, terutama pas kita pakai var atau let.
Scope variabel bisa berupa:

- Global
- Local

Variabel bisa dideklarasiin di scope global atau lokal. Yuk kita bahas dua-duanya.
Apa pun yang dideklarasiin tanpa let, var atau const punya scope di level global.

Bayangin kita punya file scope.js ya.

### Window Global Object

Tanpa pake `console.log()` buka browser kamu terus cek deh, nanti kamu bakal lihat nilai a dan b kalau kamu ketik a atau b di browser. Itu artinya a dan b udah tersedia di window, global banget!

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

Variabel yang dideklarasiin secara global bisa diakses di mana aja dalam file yang sama. Tapi istilah global itu relatif ya. Bisa global terhadap file, atau bisa global relatif terhadap beberapa blok kode.

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

Variabel yang dideklarasiin sebagai lokal cuma bisa diakses di blok kode tertentu doang.

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

Oke, sekarang kamu udah paham scope. Variabel yang dideklarasiin pake *var* cuma ter-scope ke fungsi, tapi variabel yang dideklarasiin pake *let* atau *const* adalah block scope (blok fungsi, blok if, blok loop, dll). Blok di JavaScript tuh kode di antara dua kurung kurawal ({}). Simpel kan!

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

Di ES6 ke atas udah ada *let* dan *const*, jadi kamu nggak bakal pusing-pusing lagi ngadepin sifat liciknya *var*. Kalau kita pakai *let*, variabel kita block scoped dan nggak bakal ganggu bagian lain dari kode. Cakep banget kan!

```js
//scope.js
function letsLearnScope() {
  // Kamu bisa menggunakan let atau const, tetapi gravity adalah konstanta, saya lebih suka menggunakan const
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

Scope *let* dan *const* itu sama. Bedanya cuma di reassigning (penetapan ulang). Kita nggak bisa ngubah atau netapin ulang nilai variabel `const`. Saran gue sih, pakai *let* dan *const* aja ya. Dengan *let* dan *const*, kamu bakal nulis kode yang bersih dan terhindar dari error yang susah di-debug. Rule of thumb-nya gini: pakai *let* buat nilai yang bisa berubah, *const* buat nilai konstan, dan juga buat array, objek, arrow function, dan function expression.

## 📔 Objek (Object)

Segala sesuatu bisa jadi objek dan objek punya properti, terus properti punya nilai. Jadi intinya, objek itu pasangan kunci-nilai (key-value pair). Urutan kunci nggak dijaga ya, alias nggak ada urutan tertentu.
Buat bikin objek literal, kita pakai dua kurung kurawal.

### Membuat objek kosong

Objek kosong, gampang banget!

```js
const person = {}
```

### Membuat objek dengan nilai

Nah, sekarang objek person punya properti firstName, lastName, age, location, skills dan isMarried. Nilai dari properti atau kunci bisa berupa string, number, boolean, objek, null, undefined atau fungsi. Fleksibel abis!

Yuk lihat beberapa contoh objek. Setiap kunci punya nilai di dalam objek.

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

Kita bisa ngakses nilai objek pake dua metode:

- pake . diikuti nama kunci (kalau nama kuncinya cuma satu kata)
- pake kurung siku dan tanda kutip

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

Sekarang, objek person punya properti getFullName. getFullName itu fungsi di dalam objek person dan kita nyebutnya metode objek. Kata kunci _this_ nunjuk ke objek itu sendiri. Kita bisa pakai kata _this_ buat ngakses nilai dari berbagai properti objek. Tapi inget ya, kita nggak bisa pakai arrow function sebagai metode objek karena kata this di arrow function nunjuk ke window, bukan ke objek itu sendiri. Contoh objek:

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

Objek itu struktur data yang mutable (bisa diubah) dan kita bisa modifikasi konten objek setelah dibuat. Asik kan!

Nambahin kunci baru di objek:

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

Ada berbagai metode buat manipulasi objek nih. Yuk kita lihat beberapa metode yang tersedia!

_Object.assign_: Buat menyalin objek tanpa modifikasi objek asli

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

_Object.keys_: Buat dapetin kunci atau properti dari objek sebagai array

```js
const keys = Object.keys(copyPerson)
console.log(keys) //['firstName', 'age', 'country','city', 'skills','title', 'address', 'getPersonInfo']
const address = Object.keys(copyPerson.address)
console.log(address) //['street', 'pobox', 'city']
```

#### Mendapatkan nilai objek menggunakan Object.values()

_Object.values_: Buat dapetin nilai dari objek sebagai array

```js
const values = Object.values(copyPerson)
console.log(values)
```

#### Mendapatkan kunci dan nilai objek menggunakan Object.entries()

_Object.entries_: Buat dapetin kunci dan nilai dalam array

```js
const entries = Object.entries(copyPerson)
console.log(entries)
```

#### Memeriksa properti menggunakan hasOwnProperty()

_hasOwnProperty_: Buat ngecek apakah kunci atau properti tertentu ada di dalam objek

```js
console.log(copyPerson.hasOwnProperty('name'))
console.log(copyPerson.hasOwnProperty('score'))
```

🌕 Kamu luar biasa, gaes! Sekarang kamu udah terisi penuh dengan kekuatan objek. Kamu baru aja nyelesein tantangan hari ke-8 dan selangkah lebih dekat menuju kehebatan. Gaskeun sekarang latihan buat otak dan otot kamu!

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
1. Tetapkan nama kamu di objek users tanpa memodifikasi objek users asli
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

  Bayangkan kamu mendapatkan koleksi users di atas dari database MongoDB.
    a. Buat fungsi bernama signUp yang memungkinkan pengguna untuk ditambahkan ke koleksi. Jika pengguna sudah ada, beri tahu pengguna bahwa dia sudah memiliki akun.  
    b. Buat fungsi bernama signIn yang memungkinkan pengguna untuk masuk ke aplikasi  

3. Array products memiliki tiga elemen dan masing-masing memiliki enam properti.
    a. Buat fungsi bernama rateProduct yang menilai produk
    b. Buat fungsi bernama averageRating yang menghitung rata-rata penilaian suatu produk  

4. Buat fungsi bernama likeProduct. Fungsi ini akan membantu untuk menyukai produk jika belum disukai dan menghapus like jika sudah disukai.


🎉 SELAMAT ! 🎉
