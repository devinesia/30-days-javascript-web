# 📘 Hari 19

## Closure

JavaScript memungkinkan penulisan fungsi di dalam fungsi luar (outer function). Kita dapat menulis sebanyak mungkin fungsi dalam (inner function) yang kita inginkan. Jika fungsi dalam mengakses variabel dari fungsi luar, maka itu disebut closure.

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

Mari kita lihat lebih banyak contoh fungsi dalam (inner function).

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

🌕 Anda sedang membuat kemajuan. Pertahankan momentum Anda, teruskan kerja baik. Sekarang lakukan beberapa latihan untuk otak dan otot Anda.

## Latihan

### Latihan: Level 1

1. Buat sebuah closure yang memiliki satu fungsi dalam (inner function).

### Latihan: Level 2

1. Buat sebuah closure yang memiliki tiga fungsi dalam (inner function).

### Latihan: Level 3

1. Buat sebuah fungsi luar personAccount. Ia memiliki variabel dalam firstname, lastname, incomes, expenses. Ia memiliki fungsi dalam totalIncome, totalExpense, accountInfo, addIncome, addExpense, dan accountBalance. Incomes adalah sekumpulan pemasukan beserta deskripsinya dan expenses juga sekumpulan pengeluaran beserta deskripsinya.

🎉 SELAMAT ! 🎉
