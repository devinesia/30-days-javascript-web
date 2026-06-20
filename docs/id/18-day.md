# 📘 Hari 18

## Promise

Kita sebagai manusia suka banget kasih atau nerima janji buat ngelakuin sesuatu di waktu tertentu kan? Kalau kita nepatin janji, orang lain seneng. Tapi kalau kita ingkarin? Nah, itu bisa bikin kecewa. Promise di JavaScript tuh persis kayak gitu!

Jadi Promise adalah cara keren buat nanganin operasi asinkron di JavaScript. Promise ngebolehin handler dengan nilai sukses atau alasan kegagalan dari suatu aksi asinkron. Ini bikin metode asinkron bisa ngembaliin nilai kayak metode sinkron: alih-alih langsung ngembaliin nilai akhir, metode asinkron ngembaliin sebuah promise buat nyediain nilai itu nanti di masa depan. Paham kan?

Sebuah Promise tuh bisa berada di salah satu state berikut:

- pending: state awal, belum fulfilled maupun rejected.
- fulfilled: berarti operasi udah selesai dengan sukses, mantap!
- rejected: berarti operasi gagal, yaah~

Promise yang pending bisa jadi fulfilled dengan sebuah nilai, atau rejected dengan alasan (error). Pas salah satu dari opsi ini terjadi, handler terkait yang diantrekan pake metode then bakal dipanggil. (FYI: kalau promise udah fulfilled atau rejected pas handler ditambahin, handler tetep bakal dipanggil, jadi gak ada race condition antara penyelesaian operasi asinkron dan penambahan handler-nya.)

Karena metode Promise.prototype.then() dan Promise.prototype.catch() ngembaliin promise, keduanya bisa di-chain (dirantai). Cakep!

## Callbacks

Biar bener-bener paham promise, yuk kita ngerti callback dulu. Dari kode di bawah kamu bakal liat bedanya callback dan promise.

- call back
  Nih kita liat fungsi callback yang bisa nerima dua parameter. Parameter pertama err, kedua result. Kalau parameter err false, berarti gak ada error. Sebaliknya, bakal ngembaliin error.

Di kasus ini err punya nilai dan bakal ngembaliin blok err.

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

Nah di kasus ini err false dan bakal ngembaliin blok else yaitu result.

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

Kita bisa bikin promise pake Promise constructor. Caranya gampang: pake keyword `new` diikuti kata `Promise` terus tanda kurung. Di dalem tanda kurung, dia nerima fungsi `callback`. Fungsi callback promise punya dua parameter yaitu fungsi _`resolve`_ dan _`reject`_.

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

Promise di atas udah diselesaikan (settled) dengan resolve.
Yuk kita liat contoh lain pas promise diselesaikan dengan reject.

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

Fetch API adalah antarmuka kece buat ngambil sumber daya (termasuk lewat jaringan). Buat yang pernah pake XMLHttpRequest pasti berasa familiar, cuma API baru ini lebih powerful dan fleksibel. Di tantangan ini kita bakal pake fetch buat ngambil url dan API. Selain itu, yuk kita liat demo penggunaan promise buat ngakses sumber daya jaringan pake fetch API.

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

Async dan await tuh cara yang elegan banget buat nanganin promise. Gampang dipahami dan bersih banget pas ditulis. Recommended parah!

```js
const square = async function (n) {
  return n * n
}

square(2)
```

```sh
Promise {<resolved>: 4}
```

Kata _async_ di depan sebuah fungsi berarti fungsi itu bakal ngembaliin promise. Fungsi square di atas, alih-alih ngembaliin nilai, dia ngembaliin promise. Nah, gimana cara ngakses nilai dari promise? Gampang! Pake keyword _await_.

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

Nah sekarang, kayak yang kamu liat dari contoh di atas, nulis async di depan fungsi bikin promise dan buat dapetin nilai dari promise kita pake await. Async dan await tuh soulmate, satu gak bisa ada tanpa yang lain. Mereka berdua jalan bareng terus~

Yuk kita ambil data API pake metode promise dan juga metode async dan await.

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

🌕 Kamu keren! Kamu nepatin janji kamu dan udah nyampe hari ke-18. Tepatin terus janji kamu dan selesaikan tantangan dengan resolve. Kamu udah 18 langkah lebih maju menuju kehebatan. Sekarang gaskeun latihan buat otak dan otot kamu!

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
