# 📙 Hari 22

## DOM(Document Object Model)-Hari 2

### Membuat Elemen

Untuk membuat elemen HTML kita menggunakan nama tag. Membuat elemen HTML menggunakan JavaScript sangat sederhana dan mudah. Kita menggunakan metode _document.createElement()_. Metode ini menerima nama tag elemen HTML sebagai parameter string.

```js
// syntax
document.createElement('tagname')
```

```html
<!DOCTYPE html>
<html>

<head>
    <title>Document Object Model:30 Days Of JavaScript</title>
</head>

<body>

    <script>
        let title = document.createElement('h1')
        title.className = 'title'
        title.style.fontSize = '24px'
        title.textContent = 'Creating HTML element DOM Day 2'

        console.log(title)
    </script>
</body>

</html>
```

### Membuat banyak elemen

Untuk membuat banyak elemen kita harus menggunakan perulangan. Dengan perulangan kita dapat membuat elemen HTML sebanyak yang kita inginkan. Setelah kita membuat elemen, kita dapat menetapkan nilai ke berbagai properti objek HTML.

```html
<!DOCTYPE html>
<html>

<head>
    <title>Document Object Model:30 Days Of JavaScript</title>
</head>

<body>

    <script>
        let title
        for (let i = 0; i < 3; i++) {
            title = document.createElement('h1')
            title.className = 'title'
            title.style.fontSize = '24px'
            title.textContent = i
            console.log(title)
        }
    </script>
</body>

</html>
```

### Menambahkan child ke elemen parent

Untuk melihat elemen yang dibuat pada dokumen HTML, kita harus menambahkannya ke parent sebagai elemen child. Kita dapat mengakses body dokumen HTML menggunakan *document.body*. *document.body* mendukung metode *appendChild()*. Lihat contoh di bawah.

```html
<!DOCTYPE html>
<html>

<head>
    <title>Document Object Model:30 Days Of JavaScript</title>
</head>

<body>

    <script>
        // membuat banyak elemen dan menambahkannya ke elemen parent
        let title
        for (let i = 0; i < 3; i++) {
            title = document.createElement('h1')
            title.className = 'title'
            title.style.fontSize = '24px'
            title.textContent = i
            document.body.appendChild(title)
        }
    </script>
</body>
</html>
```

### Menghapus elemen child dari node parent

Setelah membuat HTML, kita mungkin ingin menghapus elemen dan kita dapat menggunakan metode *removeChild()*.

**Contoh:**

```html
<!DOCTYPE html>
<html>

<head>
    <title>Document Object Model:30 Days Of JavaScript</title>
</head>

<body>
    <h1>Removing child Node</h1>
    <h2>Asabeneh Yetayeh challenges in 2020</h1>
    <ul>
        <li>30DaysOfPython Challenge Done</li>
        <li>30DaysOfJavaScript Challenge Done</li>
        <li>30DaysOfReact Challenge Coming</li>
        <li>30DaysOfFullStack Challenge Coming</li>
        <li>30DaysOfDataAnalysis Challenge Coming</li>
        <li>30DaysOfReactNative Challenge Coming</li>
        <li>30DaysOfMachineLearning Challenge Coming</li>
    </ul>

    <script>
        const ul = document.querySelector('ul')
        const lists = document.querySelectorAll('li')
        for (const list of lists) {
            ul.removeChild(list)

        }
    </script>
</body>

</html>
```

Seperti yang telah kita lihat di bagian sebelumnya, ada cara yang lebih baik untuk menghilangkan semua elemen HTML inner atau children dari elemen parent menggunakan properti *innerHTML*.

```html
<!DOCTYPE html>
<html>

<head>
    <title>Document Object Model:30 Days Of JavaScript</title>
</head>

<body>
    <h1>Removing child Node</h1>
    <h2>Asabeneh Yetayeh challenges in 2020</h1>
    <ul>
        <li>30DaysOfPython Challenge Done</li>
        <li>30DaysOfJavaScript Challenge Done</li>
        <li>30DaysOfReact Challenge Coming</li>
        <li>30DaysOfFullStack Challenge Coming</li>
        <li>30DaysOfDataAnalysis Challenge Coming</li>
        <li>30DaysOfReactNative Challenge Coming</li>
        <li>30DaysOfMachineLearning Challenge Coming</li>
    </ul>

    <script>
        const ul = document.querySelector('ul')
        ul.innerHTML = ''
    </script>
</body>

</html>
```

Potongan kode di atas menghapus semua elemen child.

---

🌕 Anda sangat istimewa, Anda terus berkembang setiap hari. Sekarang, Anda tahu cara menghancurkan elemen DOM yang dibuat saat diperlukan. Anda telah mempelajari DOM dan sekarang Anda memiliki kemampuan untuk membangun dan mengembangkan aplikasi. Tersisa hanya delapan hari menuju kehebatan. Sekarang lakukan beberapa latihan untuk otak dan otot Anda.

## Latihan

### Latihan: Level 1

1. Buat sebuah container div pada dokumen HTML dan buat angka 0 hingga 100 secara dinamis lalu tambahkan ke container div tersebut.
   - Background angka genap berwarna hijau
   - Background angka ganjil berwarna kuning
   - Background angka prima berwarna merah

![Number Generator](../images/projects/dom_min_project_day_number_generators_2.1.png)

### Latihan: Level 2

1. Gunakan array countries untuk menampilkan semua negara. Lihat desainnya.

![World Countries List](../images/projects/dom_min_project_countries_aray_day_2.2.png)

### Latihan: Level 3

Periksa persyaratan proyek ini dari kedua gambar (jpg dan gif). Semua data dan CSS telah diimplementasikan hanya menggunakan JavaScript. Data dapat ditemukan di folder starter project_3. Tombol dropdown telah dibuat menggunakan elemen HTML [*details*](https://www.w3schools.com/tags/tag_details.asp).

![Challenge Information](../images/projects/dom_mini_project_challenge_info_day_2.3.gif)

![Challenge Information](../images/projects/dom_mini_project_challenge_info_day_2.3.png)

🎉 SELAMAT ! 🎉
