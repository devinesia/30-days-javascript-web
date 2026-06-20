# 📘 Hari 17

## HTML5 Web Storage

Eh, udah hari ke-17 aja nih! Kali ini kita bakal ngomongin Web Storage. Jadi Web Storage (sessionStorage dan localStorage) tuh API HTML5 baru yang cakep banget dan punya banyak keunggulan dibanding cookie jadul. Sebelum ada HTML5, data aplikasi harus disimpen di cookie dan ikut dikirim di setiap request server — ribet banget kan? Nah, Web storage jauh lebih aman, dan data gede pun bisa disimpen secara lokal tanpa bikin performa website kamu turun. Batas penyimpanan cookie di kebanyakan browser tuh cuma sekitar 4 KB per cookie, sedangkan Web Storage bisa nyimpen data yang jauh lebih gede (minimal 5MB lho!) dan gak pernah ditransfer ke server. Mantap kan? Semua situs dari origin yang sama bisa nyimpen dan ngakses data yang sama.

Data yang disimpen bisa diakses pake JavaScript, yang artinya kamu bisa manfaatin client-side scripting buat ngelakuin banyak hal yang sebelumnya cuma bisa pake server-side programming dan database relasional. Keren! Ada dua objek Web Storage:

- sessionStorage
- localStorage

localStorage tuh mirip sama sessionStorage, cuma bedanya data di localStorage gak punya waktu kedaluwarsa. Sedangkan data di sessionStorage bakal ilang begitu sesi halaman berakhir — yaa pas halaman ditutup gitu deh.

Oh iya, perlu diinget juga nih: data yang disimpen di localStorage atau sessionStorage itu spesifik buat protokol halamannya.

Kunci dan nilainya selalu berupa string ya (catetan: mirip kayak object, kunci integer bakal otomatis dikonversi jadi string).

![web_storage](../images/web_storage.png)

### sessionStorage

sessionStorage cuma tersedia di dalam tab atau jendela browser aja. Fungsinya buat nyimpen data dalam satu sesi halaman web. Jadi gini, kalau jendela ditutup, data sesinya langsung ilang deh. Karena sessionStorage dan localStorage punya method yang mirip-mirip, kita bakal fokus ke localStorage aja ya.

### localStorage

localStorage HTML5 adalah bagian dari web storage API yang dipake buat nyimpen data di browser tanpa data kedaluwarsa. Data bakal tetep ada di browser bahkan setelah browser ditutup! localStorage tetep eksis di antara sesi browser. Artinya data masih tersedia pas browser ditutup dan dibuka lagi, dan juga langsung tersedia di antara tab dan jendela. Praktis banget!

Data Web Storage, di kedua kasus, gak tersedia di antara browser yang berbeda lho. Misalnya, object storage yang dibuat di Firefox gak bisa diakses di Internet Explorer — sama kayak cookie. Ada lima method buat ngoprek local storage:
_setItem(), getItem(), removeItem(), clear(), key()_

### Kasus Penggunaan Web Storage

Beberapa kasus di mana Web Storage berguna banget:

- nyimpen data sementara
- nyimpen produk yang dimasukin user ke keranjang belanjanya
- data bisa tersedia di antara request halaman, beberapa tab browser, dan juga di antara sesi browser pake localStorage
- bisa dipake offline sepenuhnya pake localStorage
- Web Storage bisa jadi peningkatan performa yang gede banget pas beberapa data statis disimpen di client buat ngurangin jumlah request berikutnya. Bahkan gambar pun bisa disimpen dalam string pake encoding Base64 lho!
- bisa dipake buat metode autentikasi user

Buat contoh-contoh di atas, udah jelas banget kita pake localStorage. Mungkin kamu bertanya-tanya, lah terus kapan dong kita pake sessionStorage?

Nah, sessionStorage cocok banget pas kita mau data langsung ilang begitu jendela ditutup. Atau, misalnya kita gak mau aplikasi saling ganggu dengan aplikasi yang sama yang kebuka di jendela lain. Skenario kayak gini paling pas pake sessionStorage.

Oke, sekarang yuk kita liat gimana cara pake API Web Storage ini!

## Objek HTML5 Web Storage

HTML web storage nyediain dua objek buat nyimpen data di client:

- window.localStorage - nyimpen data tanpa tanggal kedaluwarsa
- window.sessionStorage - nyimpen data buat satu sesi (data ilang pas tab browser ditutup). Sebagian besar browser modern udah support Web Storage, tapi tetep ada baiknya cek dukungan browser buat localStorage dan sessionStorage. Yuk kita liat method yang tersedia buat objek Web Storage.

Objek Web Storage:

- _localStorage_ - buat nampilin objek localStorage
- _localStorage.clear()_ - buat ngehapus semua yang ada di local storage
- _localStorage.setItem()_ - buat nyimpen data di localStorage. Method ini nerima parameter key dan value.
- _localStorage.getItem()_ - buat nampilin data yang disimpen di localStorage. Method ini nerima key sebagai parameter.
- _localStorage.removeItem()_ - buat ngehapus item yang tersimpan dari localStorage. Method ini nerima key sebagai parameter.
- _localStorage.key()_ - buat nampilin data yang disimpen di localStorage. Method ini nerima index sebagai parameter.

![local_storage](../images/local_storage.png)

### Menyimpan Item ke localStorage

Pas kita nyimpen data di localStorage, data bakal disimpen sebagai string. Jadi kalo kita nyimpen array atau objek, kita harus stringify dulu biar formatnya tetep kejaga. Kalo enggak, ya struktur array atau objek dari data aslinya bakal ilang.

Kita nyimpen data di localStorage pake method _localStorage.setItem_.

```js
//syntax
localStorage.setItem('key', 'value')
```

- Menyimpan string di localStorage

```js
localStorage.setItem('firstName', 'Asabeneh') // since the value is string we do not stringify it
console.log(localStorage)
```

```sh
Storage {firstName: 'Asabeneh', length: 1}
```

- Menyimpan number di local storage

```js
localStorage.setItem('age', 200)
console.log(localStorage)
```

```sh
 Storage {age: '200', firstName: 'Asabeneh', length: 2}
```

- Menyimpan array di localStorage. Kalau kita nyimpen array, objek, atau array objek, harus di-stringify dulu ya. Liat contoh di bawah nih:

```js
const skills = ['HTML', 'CSS', 'JS', 'React']
//Skills array has to be stringified first to keep the format.
const skillsJSON = JSON.stringify(skills, undefined, 4)
localStorage.setItem('skills', skillsJSON)
console.log(localStorage)
```

```sh
Storage {age: '200', firstName: 'Asabeneh', skills: 'HTML,CSS,JS,React', length: 3}
```

```js
let skills = [
  { tech: 'HTML', level: 10 },
  { tech: 'CSS', level: 9 },
  { tech: 'JS', level: 8 },
  { tech: 'React', level: 9 },
  { tech: 'Redux', level: 10 },
  { tech: 'Node', level: 8 },
  { tech: 'MongoDB', level: 8 }
]

let skillJSON = JSON.stringify(skills)
localStorage.setItem('skills', skillJSON)
```

- Menyimpan objek di localStorage. Sebelum nyimpen objek ke localStorage, objeknya harus di-stringify dulu ya!

```js
const user = {
  firstName: 'Asabeneh',
  age: 250,
  skills: ['HTML', 'CSS', 'JS', 'React']
}

const userText = JSON.stringify(user, undefined, 4)
localStorage.setItem('user', userText)
```

### Mengambil Item dari localStorage

Kita ngambil data dari local storage pake method _localStorage.getItem()_.

```js
//syntax
localStorage.getItem('key')
```

```js
let firstName = localStorage.getItem('firstName')
let age = localStorage.getItem('age')
let skills = localStorage.getItem('skills')
console.log(firstName, age, skills)
```

```sh
 'Asabeneh', '200', '['HTML','CSS','JS','React']'
```

Nah liat deh, skills-nya masih dalam format string. Yuk kita pake JSON.parse() buat nguraiin jadi array normal.

```js
let skills = localStorage.getItem('skills')
let skillsObj = JSON.parse(skills, undefined, 4)
console.log(skillsObj)
```

```sh
['HTML','CSS','JS','React']
```

### Membersihkan localStorage

Method clear bakal ngebersihin semua yang tersimpan di local storage. Gampang banget!

```js
localStorage.clear()
```

🌕 Kamu hebat, tekad kamu kuat! Sekarang kamu udah kenal Web Storage dan tau cara nyimpen data kecil di browser client. Kamu udah 17 langkah lebih maju menuju kehebatan. Sekarang gaskeun latihan buat otak dan otot kamu!

## Latihan

### Latihan: Level 1

1. Simpan nama depan, nama belakang, umur, negara, kota kamu di localStorage browser kamu.

### Latihan: Level 2

1. Buat objek student. Objek student akan memiliki kunci firstName, lastName, age, skills, country, enrolled, dan nilai untuk kunci-kunci tersebut. Simpan objek student di localStorage browser kamu.

### Latihan: Level 3

1. Buat objek bernama personAccount. Objek ini memiliki properti firstname, lastname, incomes, expenses dan method totalIncome, totalExpense, accountInfo, addIncome, addExpense, dan accountBalance. Incomes adalah sekumpulan pendapatan beserta deskripsinya dan expenses juga merupakan sekumpulan pengeluaran beserta deskripsinya.

🎉 SELAMAT ! 🎉
