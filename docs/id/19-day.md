# 📘 Hari 19

## Closure

JavaScript tuh unik banget! Dia ngebolehin kita nulis fungsi di dalem fungsi luar (outer function). Kita bisa nulis fungsi dalem (inner function) sebanyak yang kita mau. Nah, kalau inner function ngakses variabel dari outer function, itu yang dinamakan closure. Simpel kan?

```js
function outerFunction() {
    let count = 0;
    function innerFunction() {
        count++
        return count
    }

    return innerFunction
}
const innerFunc = outerFunction()

console.log(innerFunc())
console.log(innerFunc())
console.log(innerFunc())
```

```sh
1
2
3
```

Mantap kan? Yuk liat lebih banyak contoh inner function nih:

```js
function outerFunction() {
    let count = 0;
    function plusOne() {
        count++
        return count
    }
    function minusOne() {
        count--
        return count
    }

    return {
        plusOne:plusOne(),
        minusOne:minusOne()
    }
}
const innerFuncs = outerFunction()

console.log(innerFuncs.plusOne)
console.log(innerFuncs.minusOne)
```

```sh
1
0
```

🌕 Kamu lagi bikin kemajuan yang oke banget nih! Keep the momentum, terusin kerja keren kamu. Sekarang gaskeun latihan buat otak dan otot kamu!

## Latihan

### Latihan: Level 1

1. Buat sebuah closure yang memiliki satu fungsi dalam (inner function).

### Latihan: Level 2

1. Buat sebuah closure yang memiliki tiga fungsi dalam (inner function).

### Latihan: Level 3

1. Buat sebuah fungsi luar personAccount. Ia memiliki variabel dalam firstname, lastname, incomes, expenses. Ia memiliki fungsi dalam totalIncome, totalExpense, accountInfo, addIncome, addExpense, dan accountBalance. Incomes adalah sekumpulan pemasukan beserta deskripsinya dan expenses juga sekumpulan pengeluaran beserta deskripsinya.

🎉 SELAMAT ! 🎉
