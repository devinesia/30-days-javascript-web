# 📘 Hari 18

## Promise

Kita sebagai manusia memberi atau menerima janji untuk melakukan suatu aktivitas di suatu waktu. Jika kita menepati janji, kita membuat orang lain senang, tetapi jika kita tidak menepatinya, hal itu dapat menimbulkan kekecewaan. Promise dalam JavaScript memiliki kesamaan dengan contoh di atas.

Promise adalah cara untuk menangani operasi asinkron di JavaScript. Promise memungkinkan handler dengan nilai sukses atau alasan kegagalan dari suatu aksi asinkron. Ini memungkinkan metode asinkron mengembalikan nilai seperti metode sinkron: alih-alih langsung mengembalikan nilai akhir, metode asinkron mengembalikan sebuah promise untuk menyediakan nilai tersebut di suatu waktu di masa depan.

Sebuah Promise berada dalam salah satu state berikut:

- pending: state awal, belum fulfilled maupun rejected.
- fulfilled: berarti operasi telah selesai dengan sukses.
- rejected: berarti operasi telah gagal.

Promise yang pending dapat menjadi fulfilled dengan sebuah nilai, atau rejected dengan sebuah alasan (error). Ketika salah satu dari opsi ini terjadi, handler terkait yang diantrekan oleh metode then dari promise akan dipanggil. (Jika promise sudah fulfilled atau rejected saat handler terkait ditambahkan, handler akan tetap dipanggil, sehingga tidak ada race condition antara penyelesaian operasi asinkron dan penambahan handler-nya.)

Karena metode Promise.prototype.then() dan Promise.prototype.catch() mengembalikan promise, keduanya dapat dirantai (chained).

## Callbacks

Untuk memahami promise dengan baik, mari kita pahami callback terlebih dahulu. Mari kita lihat callback berikut. Dari blok kode berikut Anda akan melihat perbedaan antara callback dan promise.

- call back
  Mari kita lihat sebuah fungsi callback yang dapat menerima dua parameter. Parameter pertama adalah err dan yang kedua adalah result. Jika parameter err bernilai false, tidak akan ada error, sebaliknya akan mengembalikan error.

Dalam kasus ini err memiliki nilai dan akan mengembalikan blok err.

```js
//Callback
const doSomething = callback => {
  setTimeout(() => {
    const skills = ['HTML', 'CSS', 'JS']
    callback('It did not go well', skills)
  }, 2000)
}

const callback = (err, result) => {
  if (err) {
    return console.log(err)
  }
  return console.log(result)
}

doSomething(callback)
```

```sh
// after 2 seconds it will print
It did not go well
```

Dalam kasus ini err bernilai false dan akan mengembalikan blok else yaitu result.

```js
const doSomething = callback => {
  setTimeout(() => {
    const skills = ['HTML', 'CSS', 'JS']
    callback(false, skills)
  }, 2000)
}

doSomething((err, result) => {
  if (err) {
    return console.log(err)
  }
  return console.log(result)
})
```

```sh
// after 2 seconds it will print the skills
["HTML", "CSS", "JS"]
```

### Promise constructor

Kita dapat membuat promise menggunakan Promise constructor. Kita dapat membuat promise baru menggunakan kata kunci `new` diikuti kata `Promise` dan diikuti tanda kurung. Di dalam tanda kurung, ia menerima sebuah fungsi `callback`. Fungsi callback promise memiliki dua parameter yaitu fungsi _`resolve`_ dan _`reject`_.

```js
// syntax
const promise = new Promise((resolve, reject) => {
  resolve('success')
  reject('failure')
})
```

```js
// Promise
const doPromise = new Promise((resolve, reject) => {
  setTimeout(() => {
    const skills = ['HTML', 'CSS', 'JS']
    if (skills.length > 0) {
      resolve(skills)
    } else {
      reject('Something wrong has happened')
    }
  }, 2000)
})

doPromise
  .then(result => {
    console.log(result)
  })
  .catch(error => console.log(error))
```

```sh
["HTML", "CSS", "JS"]
```

Promise di atas telah diselesaikan (settled) dengan resolve.
Mari kita lihat contoh lain ketika promise diselesaikan dengan reject.

```js
// Promise
const doPromise = new Promise((resolve, reject) => {
  setTimeout(() => {
    const skills = ['HTML', 'CSS', 'JS']
    if (skills.includes('Node')) {
      resolve('fullstack developer')
    } else {
      reject('Something wrong has happened')
    }
  }, 2000)
})

doPromise
  .then(result => {
    console.log(result)
  })
  .catch(error => console.error(error))
```

```sh
Something wrong has happened
```

## Fetch API

Fetch API menyediakan antarmuka untuk mengambil sumber daya (termasuk melalui jaringan). Ini akan terasa familiar bagi siapa pun yang pernah menggunakan XMLHttpRequest, tetapi API baru ini menyediakan fitur yang lebih kuat dan fleksibel. Dalam tantangan ini kita akan menggunakan fetch untuk meminta url dan API. Selain itu mari kita lihat demonstrasi penggunaan promise dalam mengakses sumber daya jaringan menggunakan fetch API.

```js
const url = 'https://restcountries.com/v2/all' // countries api
fetch(url)
  .then(response => response.json()) // accessing the API data as JSON
  .then(data => {
    // getting the data
    console.log(data)
  })
  .catch(error => console.error(error)) // handling error if something wrong happens
```

## Async dan Await

Async dan await adalah cara yang elegan untuk menangani promise. Mudah dipahami dan bersih untuk ditulis.

```js
const square = async function (n) {
  return n * n
}

square(2)
```

```sh
Promise {<resolved>: 4}
```

Kata _async_ di depan sebuah fungsi berarti fungsi tersebut akan mengembalikan sebuah promise. Fungsi square di atas, alih-alih mengembalikan nilai, ia mengembalikan sebuah promise.

Bagaimana cara mengakses nilai dari promise? Untuk mengakses nilai dari promise, kita akan menggunakan kata kunci _await_.

```js
const square = async function (n) {
  return n * n
}
const value = await square(2)
console.log(value)
```

```sh
4
```

Sekarang, seperti yang Anda lihat dari contoh di atas, menulis async di depan sebuah fungsi membuat sebuah promise dan untuk mendapatkan nilai dari promise kita menggunakan await. Async dan await berjalan bersama, satu tidak dapat ada tanpa yang lain.

Mari kita ambil data API menggunakan metode promise dan metode async dan await.

- promise

```js
const url = 'https://restcountries.com/v2/all'
fetch(url)
  .then(response => response.json())
  .then(data => {
    console.log(data)
  })
  .catch(error => console.error(error))
```

- async dan await

```js
const fetchData = async () => {
  try {
    const response = await fetch(url)
    const countries = await response.json()
    console.log(countries)
  } catch (err) {
    console.error(err)
  }
}
console.log('===== async and await')
fetchData()
```

🌕 Anda nyata dan Anda menepati janji Anda, dan Anda telah mencapai hari ke-18. Tepati janji Anda dan selesaikan tantangan dengan resolve. Anda telah 18 langkah lebih maju menuju kehebatan. Sekarang lakukan beberapa latihan untuk otak dan otot Anda.

## Latihan

```js
const countriesAPI = 'https://restcountries.com/v2/all'
const catsAPI = 'https://api.thecatapi.com/v1/breeds'
```

### Latihan: Level 1

1. Baca countries API menggunakan fetch dan cetak nama negara, ibu kota, bahasa, populasi, dan luas area.

### Latihan: Level 2

1. Cetak semua nama kucing ke dalam variabel catNames.

### Latihan: Level 3

1. Baca cats api dan temukan berat rata-rata kucing dalam satuan metrik.
2. Baca countries api dan temukan 10 negara terbesar.
3. Baca countries api dan hitung total jumlah bahasa di dunia yang digunakan sebagai bahasa resmi.

🎉 SELAMAT ! 🎉
