# 📔 Hari 10

## Set

Set itu kumpulan elemen. Set cuma bisa berisi elemen unik ya, nggak boleh ada yang dobel! Yuk kita lihat cara bikin set di bagian berikut.

### Membuat set kosong

```js
const companies = new Set()
console.log(companies)
```

```sh
Set(0) {}
```

### Membuat set dari array

```js
const languages = [
  'English',
  'Finnish',
  'English',
  'French',
  'Spanish',
  'English',
  'French',
]

const setOfLanguages = new Set(languages)
console.log(setOfLanguages)
```

```sh
Set(4) {"English", "Finnish", "French", "Spanish"}
```

Set adalah objek yang bisa diiterasi dan kita bisa ngiterasi setiap elemennya. Simpel!

```js
const languages = [
  'English',
  'Finnish',
  'English',
  'French',
  'Spanish',
  'English',
  'French',
]

const setOfLanguages = new Set(languages)

for (const language of setOfLanguages) {
  console.log(language)
}
```

```sh
  English
  Finnish
  French
  Spanish
```

### Menambahkan elemen ke set

```js
const companies = new Set() // creating an empty set
console.log(companies.size) // 0

companies.add('Google') // add element to the set
companies.add('Facebook')
companies.add('Amazon')
companies.add('Oracle')
companies.add('Microsoft')
console.log(companies.size) // 5 elements in the set
console.log(companies)
```

```sh
Set(5) {"Google", "Facebook", "Amazon", "Oracle", "Microsoft"}
```

Kita juga bisa pakai perulangan buat nambahin elemen ke set. Nih contohnya:

```js
const companies = ['Google', 'Facebook', 'Amazon', 'Oracle', 'Microsoft']
setOfCompanies = new Set()
for (const company of companies) {
  setOfCompanies.add(company)
}
```

```sh
Set(5) {"Google", "Facebook", "Amazon", "Oracle", "Microsoft"}

```

### Menghapus elemen dari set

Kita bisa hapus elemen dari set pake metode delete. Gampang banget!

```js
console.log(companies.delete('Google'))
console.log(companies.size) // 4 elements left in the set
```

### Memeriksa elemen dalam set

Metode has bisa bantu kita ngecek apakah elemen tertentu ada di dalam set.

```js
console.log(companies.has('Apple')) // false
console.log(companies.has('Facebook')) // true
```

### Mengosongkan set

Ini bakal hapus semua elemen dari set. Bersih kinclong!

```js
companies.clear()
console.log(companies)
```

```sh
Set(0) {}
```

Lihat contoh di bawah buat lebih paham cara pakai set.

```js
const languages = [
  'English',
  'Finnish',
  'English',
  'French',
  'Spanish',
  'English',
  'French',
]
const langSet = new Set(languages)
console.log(langSet) // Set(4) {"English", "Finnish", "French", "Spanish"}
console.log(langSet.size) // 4

const counts = []
const count = {}

for (const l of langSet) {
  const filteredLang = languages.filter((lng) => lng === l)
  console.log(filteredLang) // ["English", "English", "English"]
  counts.push({ lang: l, count: filteredLang.length })
}
console.log(counts)
```

```js
[
  { lang: 'English', count: 3 },
  { lang: 'Finnish', count: 1 },
  { lang: 'French', count: 2 },
  { lang: 'Spanish', count: 1 },
]
```

Kasus penggunaan lain dari set, misalnya buat ngitung item unik dalam array. Cakep!

```js
const numbers = [5, 3, 2, 5, 5, 9, 4, 5]
const setOfNumbers = new Set(numbers)

console.log(setOfNumbers)
```

```sh
Set(5) {5, 3, 2, 9, 4}
```

### Gabungan (Union) set

Buat nyari gabungan dua set bisa dilakukan pake spread operator. Nih kita cari gabungan set A dan set B (A U B)

```js
let a = [1, 2, 3, 4, 5]
let b = [3, 4, 5, 6]
let c = [...a, ...b]

let A = new Set(a)
let B = new Set(b)
let C = new Set(c)

console.log(C)
```

```sh
Set(6) {1, 2, 3, 4, 5,6}
```

### Irisan (Intersection) set

Buat nyari irisan dua set bisa dilakukan pake filter. Nih kita cari irisan set A dan set B (A ∩ B)

```js
let a = [1, 2, 3, 4, 5]
let b = [3, 4, 5, 6]

let A = new Set(a)
let B = new Set(b)

let c = a.filter((num) => B.has(num))
let C = new Set(c)

console.log(C)
```

```sh
Set(3) {3, 4, 5}
```

### Selisih (Difference) set

Buat nyari selisih antara dua set bisa dilakukan pake filter. Nih kita cari selisih set A dan set B (A \ B)

```js
let a = [1, 2, 3, 4, 5]
let b = [3, 4, 5, 6]

let A = new Set(a)
let B = new Set(b)

let c = a.filter((num) => !B.has(num))
let C = new Set(c)

console.log(C)
```

```sh
Set(2) {1, 2}
```

## Map

### Membuat Map kosong

```js
const map = new Map()
console.log(map)
```

```sh
Map(0) {}
```

### Membuat Map dari array

```js
countries = [
  ['Finland', 'Helsinki'],
  ['Sweden', 'Stockholm'],
  ['Norway', 'Oslo'],
]
const map = new Map(countries)
console.log(map)
console.log(map.size)
```

```sh
Map(3) {"Finland" => "Helsinki", "Sweden" => "Stockholm", "Norway" => "Oslo"}
3
```

### Menambahkan nilai ke Map

```js
const countriesMap = new Map()
console.log(countriesMap.size) // 0
countriesMap.set('Finland', 'Helsinki')
countriesMap.set('Sweden', 'Stockholm')
countriesMap.set('Norway', 'Oslo')
console.log(countriesMap)
console.log(countriesMap.size)
```

```sh
Map(3) {"Finland" => "Helsinki", "Sweden" => "Stockholm", "Norway" => "Oslo"}
3
```

### Mengambil nilai dari Map

```js
console.log(countriesMap.get('Finland'))
```

```sh
Helsinki
```

### Memeriksa kunci dalam Map

Periksa apakah kunci ada di dalam map pake metode _has_. Ini ngembaliin _true_ atau _false_. Simpel kan!

```js
console.log(countriesMap.has('Finland'))
```

```sh
true
```

Ambil semua nilai dari map pake perulangan:

```js
for (const country of countriesMap) {
  console.log(country)
}
```

```sh
(2) ["Finland", "Helsinki"]
(2) ["Sweden", "Stockholm"]
(2) ["Norway", "Oslo"]
```

```js
for (const [country, city] of countriesMap){
 console.log(country, city)
}
```

```sh
Finland Helsinki
Sweden Stockholm
Norway Oslo
```

🌕 Kamu udah mencapai tonggak besar, gilak! Udah nggak terhentikan lagi nih. Gas terus! Kamu baru aja nyelesein tantangan hari ke-10 dan selangkah lebih dekat menuju kehebatan. Sekarang latihan buat otak dan otot kamu, yuk!

## Latihan

### Latihan: Level 1

```js
const a = [4, 5, 8, 9]
const b = [3, 4, 5, 7]
const countries = ['Finland', 'Sweden', 'Norway']
```

1. Buat set kosong
2. Buat set berisi 0 hingga 10 menggunakan perulangan
3. Hapus elemen dari set
4. Kosongkan set
5. Buat set berisi 5 elemen string dari array
6. Buat map dari negara dan jumlah karakter negaranya

### Latihan: Level 2

1. Cari gabungan a dan b
2. Cari irisan a dan b
3. Cari selisih a dan b

### Latihan: Level 3

1. Berapa banyak bahasa yang ada dalam file objek countries.

1. \*\*\* Gunakan data countries untuk menemukan 10 bahasa yang paling banyak digunakan:

```js
   // Output Anda seharusnya terlihat seperti ini
   console.log(mostSpokenLanguages(countries, 10))
   [
     { English: 91 },
     { French: 45 },
     { Arabic: 25 },
     { Spanish: 24 },
     { Russian: 9 },
     { Portuguese: 9 },
     { Dutch: 8 },
     { German: 7 },
     { Chinese: 5 },
     { Swahili: 4 },
     { Serbian: 4 }
   ]

  // Output Anda seharusnya terlihat seperti ini
  console.log(mostSpokenLanguages(countries, 3))
  [
  {English:91},
  {French:45},
  {Arabic:25}
  ]
```

🎉 SELAMAT! 🎉
