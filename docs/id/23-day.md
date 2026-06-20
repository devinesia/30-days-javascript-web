# 📙 Hari 23

## DOM(Document Object Model)-Hari 3

### Event Listener

Event HTML yang umum: onclick, onchange, onmouseover, onmouseout, onkeydown, onkeyup, onload.
Kita dapat menambahkan metode event listener ke objek DOM apa pun. Kita menggunakan metode **_addEventListener()_** untuk mendengarkan berbagai jenis event pada elemen HTML. Metode _addEventListener()_ menerima dua argumen, sebuah event listener dan sebuah callback function.

```js
selectedElement.addEventListener('eventlistner', function(e) {
  // aktivitas yang ingin Anda lakukan setelah event akan berada di sini
})
// atau

selectedElement.addEventListener('eventlistner', e => {
  // aktivitas yang ingin Anda lakukan setelah event akan berada di sini
})
```

#### Click

Untuk melampirkan event listener ke elemen, pertama kita pilih elemen tersebut kemudian kita lampirkan metode addEventListener. Event listener menerima jenis event dan callback function sebagai argumen.

Berikut adalah contoh event jenis click.

**Contoh: click**

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Document Object Model</title>
  </head>

  <body>
    <button>Click Me</button>

    <script>
      const button = document.querySelector('button')
      button.addEventListener('click', e => {
        console.log('e gives the event listener object:', e)
        console.log('e.target gives the selected element: ', e.target)
        console.log(
          'e.target.textContent gives content of selected element: ',
          e.target.textContent
        )
      })
    </script>
  </body>
</html>
```

Event juga dapat dilampirkan langsung ke elemen HTML sebagai inline script.

**Contoh: onclick**

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Document Object Model</title>
  </head>

  <body>
    <button onclick="clickMe()">Click Me</button>
    <script>
      const clickMe = () => {
        alert('We can attach event on HTML element')
      }
    </script>
  </body>
</html>
```

#### Double Click

Untuk melampirkan event listener ke elemen, pertama kita pilih elemen tersebut kemudian kita lampirkan metode addEventListener. Event listener menerima jenis event dan callback function sebagai argumen.

Berikut adalah contoh event jenis double click.
**Contoh: dblclick**

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Document Object Model</title>
  </head>

  <body>
    <button>Click Me</button>
    <script>
      const button = document.querySelector('button')
      button.addEventListener('dblclick', e => {
        console.log('e gives the event listener object:', e)
        console.log('e.target gives the selected element: ', e.target)
        console.log(
          'e.target.textContent gives content of selected element: ',
          e.target.textContent
        )
      })
    </script>
  </body>
</html>
```

#### Mouse Enter

Untuk melampirkan event listener ke elemen, pertama kita pilih elemen tersebut kemudian kita lampirkan metode addEventListener. Event listener menerima jenis event dan callback function sebagai argumen.

Berikut adalah contoh event jenis mouse enter.

**Contoh: mouseenter**

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Document Object Model</title>
  </head>

  <body>
    <button>Click Me</button>
    <script>
      const button = document.querySelector('button')
      button.addEventListener('mouseenter', e => {
        console.log('e gives the event listener object:', e)
        console.log('e.target gives the selected element: ', e.target)
        console.log(
          'e.target.textContent gives content of selected element: ',
          e.target.textContent
        )
      })
    </script>
  </body>
</html>
```

Sekarang Anda sudah familiar dengan metode addEventListener dan cara melampirkan event listener. Ada banyak jenis event listener. Tetapi dalam tantangan ini kita akan fokus pada event yang paling umum dan penting.
Daftar event:

- click - saat elemen diklik
- dblclick - saat elemen diklik dua kali
- mouseenter - saat pointer mouse masuk ke elemen
- mouseleave - saat pointer mouse meninggalkan elemen
- mousemove - saat pointer mouse bergerak di atas elemen
- mouseover - saat pointer mouse bergerak di atas elemen
- mouseout - saat pointer mouse keluar dari elemen
- input - saat nilai dimasukkan ke field input
- change - saat nilai berubah pada field input
- blur - saat elemen tidak fokus
- keydown - saat sebuah tombol ditekan
- keyup - saat sebuah tombol dilepas
- keypress - saat kita menekan tombol apa pun
- onload - saat browser telah selesai memuat halaman

Uji jenis event di atas dengan mengganti jenis event pada potongan kode di atas.

### Mendapatkan nilai dari elemen input

Kita biasanya mengisi formulir dan formulir menerima data. Field formulir dibuat menggunakan elemen HTML input. Mari kita bangun aplikasi kecil yang memungkinkan kita menghitung indeks massa tubuh seseorang menggunakan dua field input, satu tombol, dan satu tag p.

### input value

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Document Object Model:30 Days Of JavaScript</title>
  </head>

  <body>
    <h1>Body Mass Index Calculator</h1>

    <input type="text" id="mass" placeholder="Mass in Kilogram" />
    <input type="text" id="height" placeholder="Height in meters" />
    <button>Calculate BMI</button>

    <script>
      const mass = document.querySelector('#mass')
      const height = document.querySelector('#height')
      const button = document.querySelector('button')

      let bmi
      button.addEventListener('click', () => {
        bmi = mass.value / height.value ** 2
        alert(`your bmi is ${bmi.toFixed(2)}`)
        console.log(bmi)
      })
    </script>
  </body>
</html>
```

#### event input dan change

Pada contoh di atas, kita berhasil mendapatkan nilai input dari dua field input dengan mengklik tombol. Bagaimana jika kita ingin mendapatkan nilai tanpa mengklik tombol? Kita dapat menggunakan jenis event _change_ atau _input_ untuk mendapatkan data langsung dari field input saat field sedang fokus. Mari kita lihat bagaimana kita akan menanganinya.

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Document Object Model:30 Days Of JavaScript</title>
  </head>

  <body>
    <h1>Data Binding using input or change event</h1>

    <input type="text" placeholder="say something" />
    <p></p>

    <script>
      const input = document.querySelector('input')
      const p = document.querySelector('p')

      input.addEventListener('input', e => {
        p.textContent = e.target.value
      })
    </script>
  </body>
</html>
```

#### event blur

Berbeda dengan _input_ atau _change_, event _blur_ terjadi saat field input tidak dalam keadaan fokus.

```js
<!DOCTYPE html>
<html>

<head>
    <title>Document Object Model:30 Days Of JavaScript</title>
</head>

<body>
    <h1>Giving feedback using blur event</h1>

    <input type="text" id="mass" placeholder="say something" />
    <p></p>

    <script>
        const input = document.querySelector('input')
        const p = document.querySelector('p')

        input.addEventListener('blur', (e) => {
            p.textContent = 'Field is required'
            p.style.color = 'red'

        })
    </script>
</body>

</html>
```

#### keypress, keydown dan keyup

Kita dapat mengakses semua kode tombol keyboard menggunakan berbagai jenis event listener. Mari kita gunakan keypress dan dapatkan keyCode dari setiap tombol keyboard.

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Document Object Model:30 Days Of JavaScript</title>
  </head>

  <body>
    <h1>Key events: Press any key</h1>

    <script>
      document.body.addEventListener('keypress', e => {
        alert(e.keyCode)
      })
    </script>
  </body>
</html>
```

---

🌕 Anda sangat istimewa, Anda terus berkembang setiap hari. Sekarang, Anda tahu cara menangani berbagai jenis event DOM. Tersisa hanya tujuh hari menuju kehebatan. Sekarang lakukan beberapa latihan untuk otak dan otot Anda.

## Latihan

### Latihan: Level 1

1. Membuat angka dan menandai bilangan genap, ganjil, dan prima dengan tiga warna berbeda. Lihat gambar di bawah.

![Number Generator](../images/projects/dom_min_project_number_generator_day_3.1.gif)

1. Membuat kode keyboard menggunakan event listener. Gambar di bawah.

![Keyboard key](../images/projects/dom_min_project_keycode_day_3.2.gif)

🎉 SELAMAT ! 🎉
