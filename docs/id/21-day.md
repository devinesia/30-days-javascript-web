# 📙 Hari 21

## Document Object Model (DOM) - Hari 1

Dokumen HTML terstruktur sebagai Objek JavaScript. Setiap elemen HTML memiliki properti yang berbeda yang dapat membantu untuk memanipulasinya. Dimungkinkan untuk mendapatkan, membuat, menambahkan, atau menghapus elemen HTML menggunakan JavaScript. Lihat contoh di bawah ini. Memilih elemen HTML menggunakan JavaScript mirip dengan memilih menggunakan CSS. Untuk memilih elemen HTML, kita menggunakan nama tag, id, nama kelas, atau atribut lainnya.

### Mendapatkan Elemen (Getting Element)

Kita dapat mengakses elemen yang sudah dibuat menggunakan JavaScript. Untuk mengakses atau mendapatkan elemen kita menggunakan metode yang berbeda. Kode di bawah ini memiliki empat elemen _h1_. Mari kita lihat berbagai metode untuk mengakses elemen _h1_.

```html
<!DOCTYPE html>
  <html lang="en">
    <head>
      <title>Document Object Model</title>
    </head>
    <body>

     <h1 class='title' id='first-title'>First Title</h1>
     <h1 class='title' id='second-title'>Second Title</h1>
     <h1 class='title' id='third-title'>Third Title</h1>
     <h1></h1>

    </body>
  </html>
```

#### Mendapatkan elemen berdasarkan nama tag

**_getElementsByTagName()_**: menerima nama tag sebagai parameter string dan metode ini mengembalikan objek HTMLCollection. HTMLCollection adalah objek mirip array dari elemen HTML. Properti length menyediakan ukuran koleksi. Setiap kali kita menggunakan metode ini, kita mengakses elemen individual menggunakan indeks atau setelah melakukan loop melalui setiap item individual. HTMLCollection tidak mendukung semua metode array, oleh karena itu kita harus menggunakan for loop biasa alih-alih forEach.

```js
// syntax
document.getElementsByTagName('tagname')
```

```js
const allTitles = document.getElementsByTagName('h1')

console.log(allTitles) //HTMLCollections
console.log(allTitles.length) // 4

for (let i = 0; i < allTitles.length; i++) {
  console.log(allTitles[i]) // prints each elements in the HTMLCollection
}
```

#### Mendapatkan elemen berdasarkan nama kelas

Metode **_getElementsByClassName()_** mengembalikan objek HTMLCollection. HTMLCollection adalah daftar mirip array dari elemen HTML. Properti length menyediakan ukuran koleksi. Dimungkinkan untuk melakukan loop melalui semua elemen HTMLCollection. Lihat contoh di bawah ini.

```js
//syntax
document.getElementsByClassName('classname')
```

```js
const allTitles = document.getElementsByClassName('title')

console.log(allTitles) //HTMLCollections
console.log(allTitles.length) // 4

for (let i = 0; i < allTitles.length; i++) {
  console.log(allTitles[i]) // prints each elements in the HTMLCollection
}
```

#### Mendapatkan elemen berdasarkan id

**_getElementById()_** menargetkan satu elemen HTML. Kita mengirimkan id tanpa # sebagai argumen.

```js
//syntax
document.getElementById('id')
```

```js
let firstTitle = document.getElementById('first-title')
console.log(firstTitle) // <h1>First Title</h1>
```

#### Mendapatkan elemen menggunakan metode querySelector

Metode _document.querySelector_ dapat memilih elemen HTML berdasarkan nama tag, id, atau nama kelas.

**_querySelector_**: dapat digunakan untuk memilih elemen HTML berdasarkan nama tag, id, atau kelas. Jika nama tag digunakan, ia hanya memilih elemen pertama.

```js
let firstTitle = document.querySelector('h1') // select the first available h1 element
let firstTitle = document.querySelector('#first-title') // select id with first-title
let firstTitle = document.querySelector('.title') // select the first available element with class title
```

**_querySelectorAll_**: dapat digunakan untuk memilih elemen html berdasarkan nama tag atau kelas. Ia mengembalikan nodeList yang merupakan objek mirip array yang mendukung metode array. Kita dapat menggunakan **_for loop_** atau **_forEach_** untuk melakukan loop melalui setiap elemen nodeList.

```js
const allTitles = document.querySelectorAll('h1') # selects all the available h1 elements in the page

console.log(allTitles.length) // 4
for (let i = 0; i < allTitles.length; i++) {
  console.log(allTitles[i])
}

allTitles.forEach(title => console.log(title))
const allTitles = document.querySelectorAll('.title') // the same goes for selecting using class
```

### Menambahkan atribut

Atribut ditambahkan di tag pembuka HTML yang memberikan informasi tambahan tentang elemen. Atribut HTML umum: id, class, src, style, href, disabled, title, alt. Mari kita tambahkan id dan class untuk judul keempat.

```js
const titles = document.querySelectorAll('h1')
titles[3].className = 'title'
titles[3].id = 'fourth-title'
```

#### Menambahkan atribut menggunakan setAttribute

Metode **_setAttribute()_** menetapkan atribut html apa pun. Ia menerima dua parameter: tipe atribut dan nama atribut.
Mari kita tambahkan atribut class dan id untuk judul keempat.

```js
const titles = document.querySelectorAll('h1')
titles[3].setAttribute('class', 'title')
titles[3].setAttribute('id', 'fourth-title')
```

#### Menambahkan atribut tanpa setAttribute

Kita dapat menggunakan metode pengaturan objek biasa untuk menetapkan atribut tetapi ini tidak dapat berfungsi untuk semua elemen. Beberapa atribut adalah properti objek DOM dan dapat ditetapkan secara langsung. Misalnya id dan class.

```js
//another way to setting an attribute
titles[3].className = 'title'
titles[3].id = 'fourth-title'
```

#### Menambahkan kelas menggunakan classList

Metode classList adalah metode yang baik untuk menambahkan kelas tambahan. Ia tidak menimpa kelas asli jika sebuah kelas sudah ada, melainkan menambahkan kelas tambahan untuk elemen tersebut.

```js
//another way to setting an attribute: append the class, doesn't over ride
titles[3].classList.add('title', 'header-title')
```

#### Menghapus kelas menggunakan remove

Mirip dengan menambahkan, kita juga dapat menghapus kelas dari sebuah elemen. Kita dapat menghapus kelas tertentu dari sebuah elemen.

```js
//another way to setting an attribute: append the class, doesn't over ride
titles[3].classList.remove('title', 'header-title')
```

### Menambahkan Teks ke elemen HTML

Sebuah HTML adalah blok bangunan dari tag pembuka, tag penutup, dan konten teks. Kita dapat menambahkan konten teks menggunakan properti _textContent_ atau _innerHTML_.

#### Menambahkan Konten Teks menggunakan textContent

Properti _textContent_ digunakan untuk menambahkan teks ke elemen HTML.

```js
const titles = document.querySelectorAll('h1')
titles[3].textContent = 'Fourth Title'
```

#### Menambahkan Konten Teks menggunakan innerHTML

Banyak orang bingung antara _textContent_ dan _innerHTML_. _textContent_ dimaksudkan untuk menambahkan teks ke elemen HTML, namun innerHTML dapat menambahkan teks atau elemen HTML sebagai anak (child).

##### Konten Teks (Text Content)

Kita menetapkan properti objek HTML *textContent* ke sebuah teks.

```js
const titles = document.querySelectorAll('h1')
titles[3].textContent = 'Fourth Title'
```

##### Inner HTML

Kita menggunakan properti innerHTML ketika kita ingin mengganti atau menambahkan konten anak yang benar-benar baru ke elemen induk.
Nilai yang kita tetapkan akan berupa string dari elemen HTML.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>JavaScript for Everyone:DOM</title>
  </head>
  <body>
    <div class="wrapper">
        <h1>Asabeneh Yetayeh challenges in 2020</h1>
        <h2>30DaysOfJavaScript Challenge</h2>
        <ul></ul>
    </div>
    <script>
    const lists = `
    <li>30DaysOfPython Challenge Done</li>
            <li>30DaysOfJavaScript Challenge Ongoing</li>
            <li>30DaysOfReact Challenge Coming</li>
            <li>30DaysOfFullStack Challenge Coming</li>
            <li>30DaysOfDataAnalysis Challenge Coming</li>
            <li>30DaysOfReactNative Challenge Coming</li>
            <li>30DaysOfMachineLearning Challenge Coming</li>`
  const ul = document.querySelector('ul')
  ul.innerHTML = lists
    </script>
  </body>
</html>
```

Properti innerHTML juga dapat memungkinkan kita untuk menghapus semua anak dari elemen induk. Alih-alih menggunakan removeChild(), saya merekomendasikan metode berikut.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>JavaScript for Everyone:DOM</title>
  </head>
  <body>
    <div class="wrapper">
        <h1>Asabeneh Yetayeh challenges in 2020</h1>
        <h2>30DaysOfJavaScript Challenge</h2>
        <ul>
            <li>30DaysOfPython Challenge Done</li>
            <li>30DaysOfJavaScript Challenge Ongoing</li>
            <li>30DaysOfReact Challenge Coming</li>
            <li>30DaysOfFullStack Challenge Coming</li>
            <li>30DaysOfDataAnalysis Challenge Coming</li>
            <li>30DaysOfReactNative Challenge Coming</li>
            <li>30DaysOfMachineLearning Challenge Coming</li>
        </ul>
    </div>
    <script>
  const ul = document.querySelector('ul')
  ul.innerHTML = ''
    </script>
  </body>
</html>
```

### Menambahkan style

#### Menambahkan Style Warna

Mari kita tambahkan beberapa style ke judul kita. Jika elemen memiliki indeks genap, kita beri warna hijau, jika tidak merah.

```js
const titles = document.querySelectorAll('h1')
titles.forEach((title, i) => {
  title.style.fontSize = '24px' // all titles will have 24px font size
  if (i % 2 === 0) {
    title.style.color = 'green'
  } else {
    title.style.color = 'red'
  }
})
```

#### Menambahkan Style Warna Latar Belakang

Mari kita tambahkan beberapa style ke judul kita. Jika elemen memiliki indeks genap, kita beri warna hijau, jika tidak merah.

```js
const titles = document.querySelectorAll('h1')
titles.forEach((title, i) => {
  title.style.fontSize = '24px' // all titles will have 24px font size
  if (i % 2 === 0) {
    title.style.backgroundColor = 'green'
  } else {
    title.style.backgroundColor = 'red'
  }
})
```

#### Menambahkan Style Ukuran Font

Mari kita tambahkan beberapa style ke judul kita. Jika elemen memiliki indeks genap, kita beri 20px, jika tidak 30px.

```js
const titles = document.querySelectorAll('h1')
titles.forEach((title, i) => {
  title.style.fontSize = '24px' // all titles will have 24px font size
  if (i % 2 === 0) {
    title.style.fontSize = '20px'
  } else {
    title.style.fontSize = '30px'
  }
})
```

Seperti yang Anda perhatikan, properti CSS ketika kita menggunakannya di JavaScript akan menjadi camelCase. Properti CSS berikut berubah dari background-color menjadi backgroundColor, font-size menjadi fontSize, font-family menjadi fontFamily, margin-bottom menjadi marginBottom.

---

🌕 Sekarang, Anda terisi penuh dengan kekuatan super, Anda telah menyelesaikan bagian paling penting dan menantang dari tantangan ini dan JavaScript secara umum. Anda telah mempelajari DOM dan sekarang Anda memiliki kemampuan untuk membangun dan mengembangkan aplikasi. Sekarang lakukan beberapa latihan untuk otak dan otot Anda.

## Latihan

### Latihan: Level 1

1. Buat file index.html dan letakkan empat elemen p seperti di atas: Dapatkan paragraf pertama dengan menggunakan **_document.querySelector(tagname)_** dan nama tag
2. Dapatkan masing-masing paragraf menggunakan **_document.querySelector('#id')_** dan dengan id mereka
3. Dapatkan semua p sebagai nodeList menggunakan **_document.querySelectorAll(tagname)_** dan dengan nama tag mereka
4. Loop melalui nodeList dan dapatkan konten teks dari setiap paragraf
5. Tetapkan konten teks ke paragraf keempat, **_Fourth Paragraph_**
6. Tetapkan atribut id dan class untuk semua paragraf menggunakan metode pengaturan atribut yang berbeda

### Latihan: Level 2

1. Ubah style setiap paragraf menggunakan JavaScript (mis. color, background, border, font-size, font-family)
1. Pilih semua paragraf dan loop melalui setiap elemen dan beri paragraf pertama dan ketiga warna hijau, dan paragraf kedua dan keempat warna merah
1. Tetapkan konten teks, id, dan class ke setiap paragraf

### Latihan: Level 3

#### DOM: Mini project 1

1. Kembangkan aplikasi berikut, gunakan elemen HTML berikut untuk memulai. Anda akan mendapatkan kode yang sama di folder starter. Terapkan semua style dan fungsionalitas hanya menggunakan JavaScript.

   - Warna tahun berubah setiap 1 detik
   - Warna latar belakang tanggal dan waktu berubah setiap detik
   - Tantangan yang selesai memiliki latar belakang hijau
   - Tantangan yang sedang berjalan memiliki latar belakang kuning
   - Tantangan yang akan datang memiliki latar belakang merah

```html
<!-- index.html -->
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>JavaScript for Everyone:DOM</title>
  </head>
  <body>
    <div class="wrapper">
        <h1>Asabeneh Yetayeh challenges in 2020</h1>
        <h2>30DaysOfJavaScript Challenge</h2>
        <ul>
            <li>30DaysOfPython Challenge Done</li>
            <li>30DaysOfJavaScript Challenge Ongoing</li>
            <li>30DaysOfReact Challenge Coming</li>
            <li>30DaysOfFullStack Challenge Coming</li>
            <li>30DaysOfDataAnalysis Challenge Coming</li>
            <li>30DaysOfReactNative Challenge Coming</li>
            <li>30DaysOfMachineLearning Challenge Coming</li>
        </ul>
    </div>
  </body>
</html>
```

![Project 1](../images/projects/dom_min_project_challenge_info_day_1.1.gif)

![Project 2](../images/projects/dom_min_project_challenge_info_day_1.1.png)

🎉 SELAMAT ! 🎉
