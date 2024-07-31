## Daftar Isi
- [Fungsi](#fungsi)
   + [Pendefinisian Fungsi](#pendefinisian-fungsi)
   + [Prototipe Fungsi](#prototipe-fungsi)
   + [Parameter Fungsi](#parameter-fungsi)
   + [Nilai *return* Fungsi](#nilai-return-fungsi)
- [Fungsi Rekursif](#fungsi-rekursif)
   + [*Recursive Case* dan *Base Case*](#recursive-case-dan-base-case)

***

# Fungsi

## Pengenalan Fungsi
Fungsi adalah sebuah kumpulan **statement** untuk melakukan tugas spesifik, yang bisa membutuhkan *input* ataupun tidak, untuk menghasilkan *output* yang sesuai.

Secara umum, fungsi dibedakan menjadi dua, yakni fungsi *Standard Library* dan fungsi yang dibuat pengguna. **Fungsi *Standard Library*** adalah fungsi bawaan yang telah disertakan dalam *library* standar, misal fungsi cout, cin yang ada di dalam *library* <iostream>. Sedangkan **fungsi yang dibuat oleh pengguna** (*user-defined*) adalah fungsi yang sengaja dibuat oleh pengguna untuk memenuhi keperluan pengguna dalam membuat program.

## Tujuan Fungsi
Tujuan dibuatnya fungsi secara umum adalah untuk membuat program menjadi lebih modular. Fungsi digunakan ketika ingin menjalankan serangkaian perintah secara berulang kali, terkadang dengan input yang berbeda, dengan tujuan **tidak mengulang penulisan kode berkali-kali**, serta apabila nantinya program mengalami bug akan mempermudah proses perbaikan.

## Pendefinisian Fungsi
Sebelum fungsi dapat digunakan dan bisa dipanggil, perlu dilakukan pendefinisan terlebih dahulu. **Pendefinisian** ditujukan untuk mendefinisikan apa yang fungsi tersebut lakukan ketika fungsi tersebut dipanggil.

Berikut adalah sintaks untuk melakukan pendefinisan fungsi:

```
<return_type> <nama_fungsi>(<parameter1>, <parameter2>, ...)
{
    statement;
    statement;
    ...
    ...
    ...
}
```

Berikut adalah contoh fungsi untuk mencetak string **"Aku Sebuah Fungsi."**:

```cpp
void cetak()
{
    cout << "Aku Sebuah Fungsi\n";
}
 
int main()
{
    cetak();
    return 0;
}
```

## Prototipe Fungsi
Selain menggunakan pendefisian langsung seperti cara sebelumnya, fungsi juga dapat dibuat dengan prototipe. **Prototipe fungsi** (atau biasa disebut *interface* fungsi) adalah deklarasi dari sebuah fungsi tanpa definisinya. Deklarasi sebuah fungsi berisi return type, nama fungsi, dan parameter yang terlibat.

Untuk menuliskan prototipe fungsi, sintaksnya sebagai berikut:

```
// Deklarasi
<return_type> <nama_fungsi>(<parameter1>, <parameter2>, ...);
```

Contoh kode program menggunakan prototipe fungsi:

```cpp
// Prototipe Fungsi
void cetak();
 
int main()
{
    cetak();
    return 0;
}
 
// Definisi Fungsi cetak()
void cetak()
{
    cout << "Aku Sebuah Fungsi\n"
}
```

## Parameter Fungsi
**Parameter** pada fungsi bersifat layaknya input yang diberikan kepada sebuah fungsi. Jumlah parameter pada sebuah fungsi bisa dibuat sebanyak-banyaknya sesuai kebutuhan.

Penulisan parameter fungsi sama dengan pendefinisian variabel dan tiap parameter dipisahkan oleh operator (,).

```
<tipe_data> <nama_parameter_1> , <tipe_data> <nama_parameter_2>, ...
```

Contoh:
```cpp
void cetak(string str)
{
    cout << str << "\n";
}
 
void jumlah(int a, int b)
{
    int hasil = a + b;
    cout << hasil << "\n";
}
```

## Pemanggilan Fungsi
Untuk memanggil fungsi, dilakukan dengan menulis nama fungsinya diikuti dengan tanda `()`. Apabila fungsi tersebut memiliki parameter maka di dalam tanda `()` dituliskan nilai/variabel/objek untuk dijadikan yang kita sebut dengan argumen dan dipisahkan tiap argumen dengan operator `,`. Argumen-argumen yang dimasukkan harus sesuai dengan tipe data parameter fungsinya.

Contoh pemanggilan fungsi:

```cpp
int main()
{
    cetak();
    tambahkan(2,5);
    cetak("Halo, dunia");
}
```

## Nilai *return* Fungsi
Jika kita menginginkan fungsi yang kita jalankan menghasilkan sebuah nilai atau sederhananya menghasilkan sebuah output, kita bisa menambahkan *keyword* `return` dan mendefinisikan *return type* dari fungsi tersebut. Fungsi yang memiliki *return type* bukan `void` pasti memiliki *return value*. Nilai yang dikembalikan oleh fungsi tersebut memiliki tipe data yang bersesuaian dengan *return type*-nya.

Saat menemui *statement* `return` pada fungsi, maka fungsi tersebut akan berhenti dari titik dimana `return` tersebut terdapat, kemudian kembali ke bagian kode yang memanggil fungsi tersebut.

Misal kita ingin mendapatkan hasil dari penjumlahan dua bilangan menggunakan fungsi bernama `jumlah()`.

```cpp
#include <iostream>
using namespace std;
 
int jumlah(int a, int b);
 
int main()
{
    int x = 2, y = 3, hasil;
    hasil = jumlah(x, y);
    cout << hasil << "\n";
    return 0;
}
 
int jumlah(int a, int b)
{
    int hasil = a;
    hasil += b;
    return hasil;
}
```

# Fungsi Rekursif

## Pengenalan Rekursi
**Rekursi** merujuk kepada definisi suatu hal yang dilakukan secara berulang-ulang.

![image](https://miro.medium.com/max/719/1*y3-7Dh1DIsm5Ut9OZjmXTg.jpeg)

Gambar diatas juga merupakan salah satu representasi definisi dari rekursi. Di dalam dunia pemrograman istilah rekursi digunakan untuk menggambarkan fungsi yang bersifat rekursif.

**Fungsi yang bersifat rekursif** adalah fungsi yang memanggil dirinya sendiri didalam fungsi tersebut.
Perhatikan contoh program di bawah:

```cpp
#include <iostream>
using namespace std;
 
void rekursi(int n)
{
    cout << n << "\n";
    rekursi(n+1);       // memanggil dirinya sendiri
}
 
int main()
{
    rekursi(1);
    return 0;
}
```

Fungsi `rekursi()` merupakan fungsi yang bersifat rekusif karena didalamnya memanggil fungsi `rekursi()` itu sendiri.

## *Recursive Case* dan *Base Case*
Program sebelumnya akan terus mencetak tanpa henti karena fungsi tersebut tidak tahu kapan dirinya harus berhenti untuk memanggil dirinya sendiri. Karena dari itu kita perlu _**base case**_ pada sebuah fungsi rekursif.

_**Base Case**_ adalah sebuah kasus atau kondisi yang kita berikan kepada sebuah fungsi rekursif untuk berhenti memanggil dirinya lagi atau disebut juga terminating condition.

_**Recursive Case**_ adalah kasus dimana sebuah fungsi diharuskan untuk memanggil dirinya sendiri, dalam kata lain sebuah fungsi tersebut belum mencapai _base case_-nya.

Kita ambil contoh fungsi rekursif untuk memangkatkan suatu bilangan bulat. Didefinisikan perpangkatan sebuah bilangan **a** pangkat **m** sebagai **`power(a, m)`**, berarti dapat dituliskan:

<a href="https://www.codecogs.com/eqnedit.php?latex=power(a,&space;m)=a\times&space;a\times&space;a\times&space;\cdots&space;(m-kali)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?power(a,&space;m)=a\times&space;a\times&space;a\times&space;\cdots&space;(m-kali)" title="power(a, m)=a\times a\times a\times \cdots (m-kali)" /></a>

Atau dapat didefinisikan sebagai fungsi rekursif:

<a href="https://www.codecogs.com/eqnedit.php?latex=power(a,&space;m)=a\times&space;power(a,m-1)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?power(a,&space;m)=a\times&space;power(a,m-1)" title="power(a, m)=a\times power(a,m-1)" /></a>

Dengan *base case*-nya adalah:

<a href="https://www.codecogs.com/eqnedit.php?latex=power(a,&space;0)=&space;1" target="_blank"><img src="https://latex.codecogs.com/gif.latex?power(a,&space;0)=&space;1" title="power(a, 0)= 1" /></a>

Dapat diperhatikan bahwa *base case* dari fungsi `power(a, m)` adalah ketika `power(a, 0)` yang menghasilkan 1. Ketika sudah mencapai *base case*, maka tidak perlu melakukan pemanggilan fungsi itu lagi.

```cpp
#include <iostream>
using namespace std;
 
int power(int a, int m)
{
    if (m == 0) return 1;       // base case
    return (a * power(a, m-1)); // recursive case
}
 
int main()
{
    cout << power(2,3) << "\n";
    return 0;
}
```
