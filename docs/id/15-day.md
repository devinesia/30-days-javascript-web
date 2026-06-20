# 📘 Hari 15

## Class

JavaScript itu bahasa pemrograman berorientasi objek. Semua yang ada di JavaScript adalah objek, lengkap dengan properti dan method-nya masing-masing. Nah, kita bikin class buat ngebuat objek. Class itu kayak blueprint atau "cetak biru" gitu deh buat bikin objek. Kita instansiasi class buat bikin objek. Class nentuin atribut dan perilaku objek, sedangkan objek adalah realisasi dari class tersebut.

Begitu kita bikin class, kita bisa bikin objek darinya kapan aja sesuka hati. Proses bikin objek dari class ini disebut instansiasi class.

Di bagian objek sebelumnya, kita udah liat gimana bikin object literal. Object literal itu singleton, jadi cuma satu. Kalau kita pengen dapetin objek serupa, ya harus nulis ulang. Nah class memungkinkan kita bikin banyak objek tanpa nulis ulang. Ini ngebantu banget ngurangin duplikasi kode. Mantap kan?

### Mendefinisikan Class

Buat definisiin class di JavaScript, kita butuh kata kunci _class_, nama class dalam **CamelCase**, dan blok kode (dua kurung kurawal). Yuk kita bikin class bernama Person.

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

Oke, kita udah bikin class Person, tapi masih kosong isinya. Belum ada apa-apa.

### Instansiasi Class

Instansiasi class artinya bikin objek dari class. Kita butuh kata kunci _new_ dan panggil nama class setelah `new`.

Yuk bikin objek person dari class Person.

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

Tuh, kita udah berhasil bikin objek person. Tapi karena class-nya belum punya properti apa-apa, objeknya juga kosong.

Sekarang kita pake class constructor buat ngasih properti yang beda-beda ke class.

### Constructor Class

Constructor adalah fungsi bawaan yang bikin kita bisa bikin blueprint buat objek. Fungsi constructor dimulai dengan kata kunci `constructor` diikuti tanda kurung. Di dalam tanda kurung, kita masukin properti objek sebagai parameter. Terus kita pake kata kunci _this_ buat ngehubungin parameter constructor dengan class.

Constructor class Person di bawah ini punya properti firstName dan lastName. Properti ini dihubungin ke class Person pake kata kunci _this_. _This_ itu merujuk ke class itu sendiri ya.

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

Semua kunci objek masih undefined nih. Setiap instansiasi, kita harus ngasih nilai propertinya. Yuk sekarang kita kasih nilai pas instansiasi.

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

Nah kan, udah keisi! Seperti yang udah kita bilang dari awal, begitu class udah jadi, kita bisa bikin banyak objek dari class itu. Gaskeun, bikin banyak objek person pake class Person!

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

Pake class Person, kita bisa bikin tiga objek person. Tapi class ini masih sepi properti nih. Yuk tambahin lebih banyak properti!

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

Properti di fungsi constructor bisa punya nilai default, sama kayak fungsi reguler lainnya. Enak kan?

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

Constructor di dalam class adalah fungsi bawaan yang bikin kita bisa bikin blueprint. Di dalam class, kita juga bisa bikin method class. Method itu ya fungsi JavaScript yang ada di dalam class. Yuk kita bikin beberapa method.

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

Pas bikin class, kadang ada properti yang pengen kita kasih nilai awal. Misalnya nih, kalo kamu main game, skor awal pasti nol. Jadi kita bisa kasih skor awal nol. Atau skill awal yang nanti bakal bertambah seiring waktu.

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

Sebuah method bisa berupa method reguler, getter, atau setter. Yuk kita liat getter dan setter.

### getter

Method get bikin kita bisa akses nilai dari objek. Kita nulis method get pake kata kunci _get_ diikuti fungsi. Daripada akses properti langsung dari objek, kita pake getter buat dapetin nilainya. Cek nih.

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

Method setter bikin kita bisa modifikasi nilai properti tertentu. Kita nulis method setter pake kata kunci _set_ diikuti fungsi. Liat nih.

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

Jangan bingung ya bedanya method reguler sama getter. Kalau kamu udah bisa bikin method reguler, udah bagus kok. Yuk kita tambahin method reguler bernama getPersonInfo di class Person.

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

Kata kunci `static` ngedefinisiin static method untuk sebuah class. Static method nggak dipanggil di instance class, tapi dipanggil langsung di class itu sendiri. Biasanya ini fungsi utilitas, kayak fungsi buat bikin atau ngeklon objek. Contoh static method: _Date.now()_. Method _now_ dipanggil langsung dari class.

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

Static method itu method yang bisa dipake sebagai fungsi utilitas.

## Inheritance (Pewarisan)

Pake inheritance, kita bisa ngakses semua properti dan method dari class induk (parent). Ini ngurangin duplikasi kode banget. Masih inget class induk Person? Sekarang kita bikin anak-anaknya. Class anak bisa berupa Student, Teacher, dsb.

```js
// syntax
class ChildClassName extends {
 // code goes here
}
```

Oke, yuk kita bikin class anak Student dari class induk Person!

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

Nah, kita berhasil ngakses semua method di class Person dan make-nya di class anak Student. Kita bisa ngustomisasi method induk dan nambah properti tambahan ke class anak. Kalau mau ngustomisasi method plus nambah properti, kita perlu pake fungsi constructor di class anak juga. Di dalam constructor, kita panggil fungsi `super()` buat ngakses semua properti dari class induk. Class Person nggak punya gender, jadi sekarang kita kasih properti gender ke class anak Student. Kalau nama method yang sama dipake di class anak, method induk bakal ketimpa (overridden).

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

Nah, sekarang method getPersonInfo udah ditimpa (overridden) dan udah bisa ngenalin apakah orangnya laki-laki atau perempuan. Cakep!

🌕 Kamu makin gokil! Sekarang kamu udah kenal class dan punya kekuatan buat ngubah segalanya jadi objek. Kamu udah setengah jalan menuju level dewa JavaScript. Mantap! Yuk sekarang latihan biar makin nempel di otak!

## Latihan

### Latihan Level 1

1. Buat class Animal. Class-nya bakal punya properti name, age, color, legs, terus bikin berbagai method ya
2. Buat class anak Dog dan Cat dari class Animal.

### Latihan Level 2

1. Override method yang udah kamu buat di class Animal

### Latihan Level 3

1. Yuk kita coba bikin program yang ngitung ukuran pemusatan data dari suatu sampel (mean, median, mode) dan ukuran penyebaran (range, variance, standar deviasi). Plus cari min, max, count, percentile, dan distribusi frekuensi dari sampel. Kamu bisa bikin class bernama Statistics dan bikin semua fungsi yang ngelakuin perhitungan statistik sebagai method di class Statistics. Cek output di bawah ini ya.

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

1. Buat class bernama PersonAccount. Class ini punya properti firstname, lastname, incomes, expenses dan method totalIncome, totalExpense, accountInfo, addIncome, addExpense, dan accountBalance. Incomes adalah sekumpulan pendapatan plus deskripsinya, expenses juga sekumpulan pengeluaran plus deskripsinya.

🎉 SELAMAT ! 🎉
