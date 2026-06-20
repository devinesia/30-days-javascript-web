# 📘 Hari 15

## Class

JavaScript adalah bahasa pemrograman berorientasi objek. Segala sesuatu di JavaScript adalah objek, dengan properti dan method-nya masing-masing. Kita membuat class untuk membuat objek. Class itu seperti constructor objek, atau "cetak biru" untuk membuat objek. Kita menginstansiasi class untuk membuat objek. Class mendefinisikan atribut dan perilaku objek, sementara objek, di sisi lain, merepresentasikan class tersebut.

Setelah kita membuat class, kita dapat membuat objek darinya kapan pun kita mau. Membuat objek dari class disebut instansiasi class.

Di bagian objek, kita telah melihat cara membuat object literal. Object literal adalah singleton. Jika kita ingin mendapatkan objek serupa, kita harus menulisnya ulang. Namun, class memungkinkan kita membuat banyak objek. Ini membantu mengurangi jumlah kode dan pengulangan kode.

### Mendefinisikan Class

Untuk mendefinisikan class di JavaScript, kita memerlukan kata kunci _class_, nama class dalam **CamelCase**, dan blok kode (dua kurung kurawal). Mari kita buat class bernama Person.

```sh
// syntax
class ClassName {
    //  code goes here
}

```

**Contoh:**

```js
class Person {
  // code goes here
}
```

Kita telah membuat class Person tetapi belum ada apa pun di dalamnya.

### Instansiasi Class

Instansiasi class berarti membuat objek dari class. Kita memerlukan kata kunci _new_ dan memanggil nama class setelah kata new.

Mari kita buat objek person dari class Person.

```js
class Person {
  // code goes here
}
const person = new Person()
console.log(person)
```

```sh
Person {}
```

Seperti yang Anda lihat, kita telah membuat objek person. Karena class belum memiliki properti apa pun, objeknya juga masih kosong.

Mari kita gunakan constructor class untuk memberikan properti yang berbeda pada class.

### Constructor Class

Constructor adalah fungsi bawaan yang memungkinkan kita membuat cetak biru untuk objek kita. Fungsi constructor dimulai dengan kata kunci constructor diikuti oleh tanda kurung. Di dalam tanda kurung, kita memberikan properti objek sebagai parameter. Kita menggunakan kata kunci _this_ untuk menautkan parameter constructor dengan class.

Constructor class Person berikut memiliki properti firstName dan lastName. Properti ini ditautkan ke class Person menggunakan kata kunci _this_. _This_ merujuk pada class itu sendiri.

```js
class Person {
  constructor(firstName, lastName) {
    console.log(this) // Check the output from here
    this.firstName = firstName
    this.lastName = lastName
  }
}

const person = new Person()

console.log(person)
```

```sh
Person {firstName: undefined, lastName:undefined}
```

Semua kunci objek bernilai undefined. Setiap kali kita melakukan instansiasi, kita harus memberikan nilai propertinya. Mari kita berikan nilai kali ini saat kita menginstansiasi class.

```js
class Person {
  constructor(firstName, lastName) {
    this.firstName = firstName
    this.lastName = lastName
  }
}

const person1 = new Person('Asabeneh', 'Yetayeh')

console.log(person1)
```

```sh
Person {firstName: "Asabeneh", lastName: "Yetayeh"}
```

Seperti yang telah kami nyatakan di awal, setelah kita membuat class, kita dapat membuat banyak objek menggunakan class tersebut. Sekarang, mari kita buat banyak objek person menggunakan class Person.

```js
class Person {
  constructor(firstName, lastName) {
    console.log(this) // Check the output from here
    this.firstName = firstName
    this.lastName = lastName
  }
}

const person1 = new Person('Asabeneh', 'Yetayeh')
const person2 = new Person('Lidiya', 'Tekle')
const person3 = new Person('Abraham', 'Yetayeh')

console.log(person1)
console.log(person2)
console.log(person3)
```

```sh
Person {firstName: "Asabeneh", lastName: "Yetayeh"}
Person {firstName: "Lidiya", lastName: "Tekle"}
Person {firstName: "Abraham", lastName: "Yetayeh"}
```

Menggunakan class Person, kita telah membuat tiga objek person. Seperti yang Anda lihat, class kita belum memiliki banyak properti. Mari kita tambahkan lebih banyak properti ke class.

```js
class Person {
  constructor(firstName, lastName, age, country, city) {
    console.log(this) // Check the output from here
    this.firstName = firstName
    this.lastName = lastName
    this.age = age
    this.country = country
    this.city = city
  }
}

const person1 = new Person('Asabeneh', 'Yetayeh', 250, 'Finland', 'Helsinki')

console.log(person1)
```

```sh
Person {firstName: "Asabeneh", lastName: "Yetayeh", age: 250, country: "Finland", city: "Helsinki"}
```

### Nilai Default dengan Constructor

Properti fungsi constructor dapat memiliki nilai default seperti fungsi reguler lainnya.

```js
class Person {
  constructor(
    firstName = 'Asabeneh',
    lastName = 'Yetayeh',
    age = 250,
    country = 'Finland',
    city = 'Helsinki'
  ) {
    this.firstName = firstName
    this.lastName = lastName
    this.age = age
    this.country = country
    this.city = city
  }
}

const person1 = new Person() // it will take the default values
const person2 = new Person('Lidiya', 'Tekle', 28, 'Finland', 'Espoo')

console.log(person1)
console.log(person2)
```

```sh
Person {firstName: "Asabeneh", lastName: "Yetayeh", age: 250, country: "Finland", city: "Helsinki"}
Person {firstName: "Lidiya", lastName: "Tekle", age: 28, country: "Finland", city: "Espoo"}
```

### Method Class

Constructor di dalam class adalah fungsi bawaan yang memungkinkan kita membuat cetak biru untuk objek. Di dalam class, kita dapat membuat method class. Method adalah fungsi JavaScript di dalam class. Mari kita buat beberapa method class.

```js
class Person {
  constructor(firstName, lastName, age, country, city) {
    this.firstName = firstName
    this.lastName = lastName
    this.age = age
    this.country = country
    this.city = city
  }
  getFullName() {
    const fullName = this.firstName + ' ' + this.lastName
    return fullName
  }
}

const person1 = new Person('Asabeneh', 'Yetayeh', 250, 'Finland', 'Helsinki')
const person2 = new Person('Lidiya', 'Tekle', 28, 'Finland', 'Espoo')

console.log(person1.getFullName())
console.log(person2.getFullName())
```

```sh
Asabeneh Yetayeh
test.js:19 Lidiya Tekle
```

### Properti dengan Nilai Awal

Ketika kita membuat class, untuk beberapa properti kita mungkin memiliki nilai awal. Misalnya, jika Anda bermain game, skor awal Anda adalah nol. Jadi, kita bisa memiliki skor awal atau skor yang bernilai nol. Dengan cara lain, kita mungkin memiliki skill awal dan akan memperoleh skill setelah beberapa waktu.

```js
class Person {
  constructor(firstName, lastName, age, country, city) {
    this.firstName = firstName
    this.lastName = lastName
    this.age = age
    this.country = country
    this.city = city
    this.score = 0
    this.skills = []
  }
  getFullName() {
    const fullName = this.firstName + ' ' + this.lastName
    return fullName
  }
}

const person1 = new Person('Asabeneh', 'Yetayeh', 250, 'Finland', 'Helsinki')
const person2 = new Person('Lidiya', 'Tekle', 28, 'Finland', 'Espoo')

console.log(person1.score)
console.log(person2.score)

console.log(person1.skills)
console.log(person2.skills)
```

```sh
0
0
[]
[]
```

Sebuah method bisa berupa method reguler atau getter atau setter. Mari kita lihat getter dan setter.

### getter

Method get memungkinkan kita mengakses nilai dari objek. Kita menulis method get menggunakan kata kunci _get_ diikuti oleh sebuah fungsi. Alih-alih mengakses properti langsung dari objek, kita menggunakan getter untuk mendapatkan nilainya. Lihat contoh di bawah ini.

```js
class Person {
  constructor(firstName, lastName, age, country, city) {
    this.firstName = firstName
    this.lastName = lastName
    this.age = age
    this.country = country
    this.city = city
    this.score = 0
    this.skills = []
  }
  getFullName() {
    const fullName = this.firstName + ' ' + this.lastName
    return fullName
  }
  get getScore() {
    return this.score
  }
  get getSkills() {
    return this.skills
  }
}

const person1 = new Person('Asabeneh', 'Yetayeh', 250, 'Finland', 'Helsinki')
const person2 = new Person('Lidiya', 'Tekle', 28, 'Finland', 'Espoo')

console.log(person1.getScore) // We do not need parenthesis to call a getter method
console.log(person2.getScore)

console.log(person1.getSkills)
console.log(person2.getSkills)
```

```sh
0
0
[]
[]
```

### setter

Method setter memungkinkan kita memodifikasi nilai properti tertentu. Kita menulis method setter menggunakan kata kunci _set_ diikuti oleh sebuah fungsi. Lihat contoh di bawah ini.

```js
class Person {
  constructor(firstName, lastName, age, country, city) {
    this.firstName = firstName
    this.lastName = lastName
    this.age = age
    this.country = country
    this.city = city
    this.score = 0
    this.skills = []
  }
  getFullName() {
    const fullName = this.firstName + ' ' + this.lastName
    return fullName
  }
  get getScore() {
    return this.score
  }
  get getSkills() {
    return this.skills
  }
  set setScore(score) {
    this.score += score
  }
  set setSkill(skill) {
    this.skills.push(skill)
  }
}

const person1 = new Person('Asabeneh', 'Yetayeh', 250, 'Finland', 'Helsinki')
const person2 = new Person('Lidiya', 'Tekle', 28, 'Finland', 'Espoo')

person1.setScore = 1
person1.setSkill = 'HTML'
person1.setSkill = 'CSS'
person1.setSkill = 'JavaScript'

person2.setScore = 1
person2.setSkill = 'Planning'
person2.setSkill = 'Managing'
person2.setSkill = 'Organizing'

console.log(person1.score)
console.log(person2.score)

console.log(person1.skills)
console.log(person2.skills)
```

```sh
1
1
["HTML", "CSS", "JavaScript"]
["Planning", "Managing", "Organizing"]
```

Jangan bingung dengan perbedaan antara method reguler dan getter. Jika Anda tahu cara membuat method reguler, Anda sudah baik. Mari kita tambahkan method reguler bernama getPersonInfo di class Person.

```js
class Person {
  constructor(firstName, lastName, age, country, city) {
    this.firstName = firstName
    this.lastName = lastName
    this.age = age
    this.country = country
    this.city = city
    this.score = 0
    this.skills = []
  }
  getFullName() {
    const fullName = this.firstName + ' ' + this.lastName
    return fullName
  }
  get getScore() {
    return this.score
  }
  get getSkills() {
    return this.skills
  }
  set setScore(score) {
    this.score += score
  }
  set setSkill(skill) {
    this.skills.push(skill)
  }
  getPersonInfo() {
    let fullName = this.getFullName()
    let skills =
      this.skills.length > 0 &&
      this.skills.slice(0, this.skills.length - 1).join(', ') +
        ` and ${this.skills[this.skills.length - 1]}`
    let formattedSkills = skills ? `He knows ${skills}` : ''

    let info = `${fullName} is ${this.age}. He lives ${this.city}, ${this.country}. ${formattedSkills}`
    return info
  }
}

const person1 = new Person('Asabeneh', 'Yetayeh', 250, 'Finland', 'Helsinki')
const person2 = new Person('Lidiya', 'Tekle', 28, 'Finland', 'Espoo')
const person3 = new Person('John', 'Doe', 50, 'Mars', 'Mars city')

person1.setScore = 1
person1.setSkill = 'HTML'
person1.setSkill = 'CSS'
person1.setSkill = 'JavaScript'

person2.setScore = 1
person2.setSkill = 'Planning'
person2.setSkill = 'Managing'
person2.setSkill = 'Organizing'

console.log(person1.getScore)
console.log(person2.getScore)

console.log(person1.getSkills)
console.log(person2.getSkills)
console.log(person3.getSkills)

console.log(person1.getPersonInfo())
console.log(person2.getPersonInfo())
console.log(person3.getPersonInfo())
```

```sh
1
1
["HTML", "CSS", "JavaScript"]
["Planning", "Managing", "Organizing"]
[]
Asabeneh Yetayeh is 250. He lives Helsinki, Finland. He knows HTML, CSS and JavaScript
Lidiya Tekle is 28. He lives Espoo, Finland. He knows Planning, Managing and Organizing
John Doe is 50. He lives Mars city, Mars.
```

### Static Method

Kata kunci static mendefinisikan static method untuk sebuah class. Static method tidak dipanggil pada instance class. Sebaliknya, mereka dipanggil pada class itu sendiri. Ini sering berupa fungsi utilitas, seperti fungsi untuk membuat atau mengkloning objek. Contoh static method adalah _Date.now()_. Method _now_ dipanggil langsung dari class.

```js
class Person {
  constructor(firstName, lastName, age, country, city) {
    this.firstName = firstName
    this.lastName = lastName
    this.age = age
    this.country = country
    this.city = city
    this.score = 0
    this.skills = []
  }
  getFullName() {
    const fullName = this.firstName + ' ' + this.lastName
    return fullName
  }
  get getScore() {
    return this.score
  }
  get getSkills() {
    return this.skills
  }
  set setScore(score) {
    this.score += score
  }
  set setSkill(skill) {
    this.skills.push(skill)
  }
  getPersonInfo() {
    let fullName = this.getFullName()
    let skills =
      this.skills.length > 0 &&
      this.skills.slice(0, this.skills.length - 1).join(', ') +
        ` and ${this.skills[this.skills.length - 1]}`

    let formattedSkills = skills ? `He knows ${skills}` : ''

    let info = `${fullName} is ${this.age}. He lives ${this.city}, ${this.country}. ${formattedSkills}`
    return info
  }
  static favoriteSkill() {
    const skills = ['HTML', 'CSS', 'JS', 'React', 'Python', 'Node']
    const index = Math.floor(Math.random() * skills.length)
    return skills[index]
  }
  static showDateTime() {
    let now = new Date()
    let year = now.getFullYear()
    let month = now.getMonth() + 1
    let date = now.getDate()
    let hours = now.getHours()
    let minutes = now.getMinutes()
    if (hours < 10) {
      hours = '0' + hours
    }
    if (minutes < 10) {
      minutes = '0' + minutes
    }

    let dateMonthYear = date + '.' + month + '.' + year
    let time = hours + ':' + minutes
    let fullTime = dateMonthYear + ' ' + time
    return fullTime
  }
}

console.log(Person.favoriteSkill())
console.log(Person.showDateTime())
```

```sh
Node
15.1.2020 23:56
```

Static method adalah method yang dapat digunakan sebagai fungsi utilitas.

## Inheritance (Pewarisan)

Menggunakan inheritance, kita dapat mengakses semua properti dan method dari class induk (parent). Ini mengurangi pengulangan kode. Jika Anda ingat, kita memiliki class induk Person dan kita akan membuat anak (children) darinya. Class anak kita bisa berupa student, teacher, dll.

```js
// syntax
class ChildClassName extends {
 // code goes here
}
```

Mari kita buat class anak Student dari class induk Person.

```js
class Student extends Person {
  saySomething() {
    console.log('I am a child of the person class')
  }
}

const s1 = new Student('Asabeneh', 'Yetayeh', 'Finland', 250, 'Helsinki')
console.log(s1)
console.log(s1.saySomething())
console.log(s1.getFullName())
console.log(s1.getPersonInfo())
```

```sh
Student {firstName: "Asabeneh", lastName: "Yetayeh", age: "Finland", country: 250, city: "Helsinki", …}
I am a child of the person class
Asabeneh Yetayeh
Student {firstName: "Asabeneh", lastName: "Yetayeh", age: "Finland", country: 250, city: "Helsinki", …}
Asabeneh Yetayeh is Finland. He lives Helsinki, 250.
```

### Overriding Method

Seperti yang Anda lihat, kita berhasil mengakses semua method di Class Person dan menggunakannya di class anak Student. Kita dapat menyesuaikan method induk, kita dapat menambahkan properti tambahan ke class anak. Jika kita ingin menyesuaikan method dan menambahkan properti tambahan, kita perlu menggunakan fungsi constructor di class anak juga. Di dalam fungsi constructor, kita memanggil fungsi super() untuk mengakses semua properti dari class induk. Class Person tidak memiliki gender, tetapi sekarang mari kita berikan properti gender untuk class anak, Student. Jika nama method yang sama digunakan di class anak, method induk akan ditimpa (overridden).

```js
class Student extends Person {
  constructor(firstName, lastName, age, country, city, gender) {
    super(firstName, lastName, age, country, city)
    this.gender = gender
  }

  saySomething() {
    console.log('I am a child of the person class')
  }
  getPersonInfo() {
    let fullName = this.getFullName()
    let skills =
      this.skills.length > 0 &&
      this.skills.slice(0, this.skills.length - 1).join(', ') +
        ` and ${this.skills[this.skills.length - 1]}`

    let formattedSkills = skills ? `He knows ${skills}` : ''
    let pronoun = this.gender == 'Male' ? 'He' : 'She'

    let info = `${fullName} is ${this.age}. ${pronoun} lives in ${this.city}, ${this.country}. ${formattedSkills}`
    return info
  }
}

const s1 = new Student(
  'Asabeneh',
  'Yetayeh',
  250,
  'Finland',
  'Helsinki',
  'Male'
)
const s2 = new Student('Lidiya', 'Tekle', 28, 'Finland', 'Helsinki', 'Female')
s1.setScore = 1
s1.setSkill = 'HTML'
s1.setSkill = 'CSS'
s1.setSkill = 'JavaScript'

s2.setScore = 1
s2.setSkill = 'Planning'
s2.setSkill = 'Managing'
s2.setSkill = 'Organizing'

console.log(s1)

console.log(s1.saySomething())
console.log(s1.getFullName())
console.log(s1.getPersonInfo())

console.log(s2.saySomething())
console.log(s2.getFullName())
console.log(s2.getPersonInfo())
```

```sh
Student {firstName: "Asabeneh", lastName: "Yetayeh", age: 250, country: "Finland", city: "Helsinki", …}
Student {firstName: "Lidiya", lastName: "Tekle", age: 28, country: "Finland", city: "Helsinki", …}
I am a child of the person class
Asabeneh Yetayeh
Student {firstName: "Asabeneh", lastName: "Yetayeh", age: 250, country: "Finland", city: "Helsinki", …}
Asabeneh Yetayeh is 250. He lives in Helsinki, Finland. He knows HTML, CSS and JavaScript
I am a child of the person class
Lidiya Tekle
Student {firstName: "Lidiya", lastName: "Tekle", age: 28, country: "Finland", city: "Helsinki", …}
Lidiya Tekle is 28. She lives in Helsinki, Finland. He knows Planning, Managing and Organizing
```

Sekarang, method getPersonInfo telah ditimpa (overridden) dan mengidentifikasi apakah orang tersebut laki-laki atau perempuan.

🌕 Anda semakin hebat. Sekarang, Anda sudah mengenal class dan memiliki kekuatan untuk mengubah segalanya menjadi objek. Anda telah mencapai setengah jalan menuju kehebatan. Sekarang lakukan beberapa latihan untuk otak dan otot Anda.

## Latihan

### Latihan Level 1

1. Buat class Animal. Class tersebut akan memiliki properti name, age, color, legs dan buat berbagai method
2. Buat class anak Dog dan Cat dari class Animal.

### Latihan Level 2

1. Override method yang Anda buat di class Animal

### Latihan Level 3

1. Mari kita coba mengembangkan program yang menghitung ukuran pemusatan data dari suatu sampel (mean, median, mode) dan ukuran penyebaran (range, variance, standar deviasi). Selain itu, cari min, max, count, percentile, dan distribusi frekuensi dari sampel. Anda dapat membuat class bernama Statistics dan membuat semua fungsi yang melakukan perhitungan statistik sebagai method untuk class Statistics. Periksa output di bawah ini.

```JS
ages = [31, 26, 34, 37, 27, 26, 32, 32, 26, 27, 27, 24, 32, 33, 27, 25, 26, 38, 37, 31, 34, 24, 33, 29, 26]

console.log('Count:', statistics.count()) // 25
console.log('Sum: ', statistics.sum()) // 744
console.log('Min: ', statistics.min()) // 24
console.log('Max: ', statistics.max()) // 38
console.log('Range: ', statistics.range() // 14
console.log('Mean: ', statistics.mean()) // 30
console.log('Median: ',statistics.median()) // 29
console.log('Mode: ', statistics.mode()) // {'mode': 26, 'count': 5}
console.log('Variance: ',statistics.var()) // 17.5
console.log('Standard Deviation: ', statistics.std()) // 4.2
console.log('Variance: ',statistics.var()) // 17.5
console.log('Frequency Distribution: ',statistics.freqDist()) // [(20.0, 26), (16.0, 27), (12.0, 32), (8.0, 37), (8.0, 34), (8.0, 33), (8.0, 31), (8.0, 24), (4.0, 38), (4.0, 29), (4.0, 25)]
```

```sh
// you output should look like this
console.log(statistics.describe())
Count: 25
Sum:  744
Min:  24
Max:  38
Range:  14
Mean:  30
Median:  29
Mode:  (26, 5)
Variance:  17.5
Standard Deviation:  4.2
Frequency Distribution: [(20.0, 26), (16.0, 27), (12.0, 32), (8.0, 37), (8.0, 34), (8.0, 33), (8.0, 31), (8.0, 24), (4.0, 38), (4.0, 29), (4.0, 25)]
```

1. Buat class bernama PersonAccount. Class ini memiliki properti firstname, lastname, incomes, expenses dan method totalIncome, totalExpense, accountInfo, addIncome, addExpense, dan accountBalance. Incomes adalah sekumpulan pendapatan beserta deskripsinya dan expenses juga merupakan sekumpulan pengeluaran beserta deskripsinya.

🎉 SELAMAT ! 🎉
