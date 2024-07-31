  ## Daftar Isi

- [Control Flow](#control-flow)
- [Percabangan](#percabangan)
    + [If](#percabangan-if)
    + [If-Else](#percabangan-if-else)
    + [If-Else if](#percabangan-if-else-if)
    + [Switch-Case](#percabangan-switch-case)
    + [Operator Kondisional ( ? : )](#operator-kondisional--)
- [Perulangan](#perulangan)
    + [Perulangan While](#perulangan-while)
    + [Perulangan Do-While](#perulangan-do-while)
    + [Perulangan For](#perulangan-for)
    + [Perulangan Bersarang](#perulanganpercabangan-bersarang-nested)
- [Break dan Continue](#break-dan-continue)
- [Infinite Loop](#infinite-loop)
- [Array](#array)
    + [Pengenalan, Deklarasi, Inisialisasi Array](#pengenalan-array)
    + [Mengakses Array](#mengakses-array)
    + [Dimensi Array](#dimensi-array)
- [String](#string)
    + [Pengenalan dan Representasi String](#pengenalan-string)
    + [Fungsi-Fungsi String](#fungsi-fungsi-string)

# Control Flow
Control Flow adalah cara kita mengatur jalan penyataan, instruksi, dan pemanggilan fungsi  suatu program. Tanpa control flow, program kita hanya bergerak dari atas ke bawah saja (**sequential**). Control flow bahasa C++ ada 2, yaitu percabangan (**selection**) dan perulangan (**repetition**). Di Modul ini, kita akan memfokuskan pembahasan di percabangan terlebih dahulu.

# Percabangan
Percabangan memungkinkan kita untuk menentukan kode manakah yang akan kita eksekusi berdasarkan suatu kondisi. Percabangan di bahasa C++ ada 4, yaitu `if`, `if-else`, `if-else if`, dan `switch`.

## Percabangan If

Sintaks yang digunakan dalam percabangan menggunakan `if` adalah sebagai berikut.

```cpp
if (<Ekspresi/Kondisi>) {

    // Kode yang akan dieksekusi jika kondisi tersebut benar

}
```

Cara kerja percabangan `if` yaitu memeriksa dan mengevaluasi suatu kondisi untuk menentukan apakah instruksi selanjutnya dalam _bracket_ akan dijalankan atau tidak oleh program.
- Jika kondisi tersebut bernilai **TRUE (1)**, kode yang di dalam bracket akan **dieksekusi**. 
- Sebaliknya jika kondisi tersebut bernilai **FALSE (0)**, kode yang di dalam bracket **tidak akan dieksekusi**.

Contoh

Sebagai contoh, di dashboard mobil terdapat indikator bahan bakar yang akan **menyala jika bahan bakar yang tersisa kurang dari level tertentu (misal kurang dari 10 liter)** dengan kondisi “Apakah bahan bakar kurang dari 10 liter?”.

Pada kasus ini terdapat kondisi
- **Jika bahan bakar kurang dari 10 liter** maka nyalakan lampu indikator.

```cpp
#include <iostream>
using namespace std;
int main()
{
    int gasoline = 0;
    gasoline = 3;
    if (gasoline < 10) //jika bahan bakar kurang dari 10 liter
    {
        // Apa yang perlu dilakukan ketika kondisi terpenuhi?
        cout << "Lampu Indikator menyala!\n";
    }
}
```

Output

```
Lampu Indikator menyala!
```

## Percabangan If-Else

Sintaks yang digunakan dalam percabangan menggunakan `if-else` adalah sebagai berikut.

```cpp
if (<Ekspresi/Kondisi>) {

    // Kode yang akan dieksekusi jika kondisi tersebut benar

} else {

    // Kode yang akan dieksekusi jika kondisi tersebut salah

}
```

Cara kerja percabangan `if-else` yaitu memeriksa kondisi dalam `if`.
- Jika kondisi tersebut bernilai **TRUE (1)**, Program akan **menjalankan kode di dalam bracket `if`**.
- Sebaliknya jika kondisi tersebut bernilai **FALSE (0)**, kode di bawah **`else`** lah **yang akan dijalankan**.

Sebagai contoh, kita ingin mencari tahu apakah seseorang absen dari kelas atau tidak. **Apabila ia tidak hadir, maka absensinya akan dicoret (bernilai X)**, dan **apabila hadir, maka absensinya akan di centang (bernilai V)**.

Sehingga dari kasus tersebut, didapat dua alternatif kondisi.
- **Apabila ia hadir, maka muncul V**
- **Apabila ia tidak hadir, maka muncul X**

```cpp
#include <iostream>
#define DATANG 1
using namespace std;

int main()
{
    int hadir = DATANG;
    if (hadir) // Jika orang tersebut hadir
    {
        cout << "V\n";
    } else {
        cout << "X\n";
    }
}
```

Output

```
V
```

## Percabangan If-Else if

Sintaks yang digunakan dalam percabangan menggunakan `if-else if` adalah sebagai berikut.

```cpp
if (<Ekspresi/Kondisi>) {

    // Kode yang akan dieksekusi jika kondisi tersebut benar

}else if (<Ekspresi/Kondisi>) {

    // Kode yang akan dieksekusi jika kondisi tersebut salah

}
// Boleh menambahkan else{} apabila perlu
```

Cara kerja percabangan `if-else` yaitu memeriksa kondisi dalam `if`.
- Jika kondisi tersebut bernilai **TRUE (1)**, Program akan **menjalankan kode di dalam bracket `if`**.
- Apabila kondisi pertama tidak memenuhi, maka ia akan memerika kondisi didalam `else-if`, apabila bernilai **TRUE (1)**, maka ia akan **menjalankan perintah dalam bracket tersebut**, apabila tidak maka ia akan menjalankan sequence selanjutnya.
- Apabila kita menyediakan statement else diakhir, maka ketika **seluruh kondisi** `if` dan `else-if` tidak memenuhi atau **FALSE (0)**, maka secara otomatis ia akan **menjalankan perintah di dalam `else`** tersebut.

## Percabangan Switch-Case

Selain penggunaan statement `if` untuk memilih diantara banyak alternatif, terdapat pula statement `switch` yang memiliki fungsi yang sama, untuk memilih diantara banyak alternatif berdasarkan sebuah kondisi. Kondisi pada statemen `switch` berisi ekspresi yang dapat menggunakan sebuah variable tunggal bertipe int atau char yang akan diperiksa nilainya di setiap blok case.

Sintaks untuk Switch-Case:

```cpp
switch(ekspresi) {

    case ekspresi-konstan:
        statement;
        break;

    case ekspresi-konstan:
        statement;
        break;
  
    /* Anda bisa memiliki jumlah case sebanyak mungkin */

    /* Anda harus mengakhiri blok kode Switch-Case dengan "default",
       yaitu bagian kode yang akan dieksekusi jika tidak ada case yang memenuhi */

    default: 
        statement;
}
```

Setiap blok, case harus ditambahkan statement **``break``**, karena apabila tidak maka ia akan tetap menjalankan blok case di bawahnya hingga bertemu `break` lain atau pada akhir blok switch.

Contoh

```cpp
#include <iostream>
using namespace std;

int main()
{
    char platNomor;
    cout << "Masukkan huruf awal plat nomor anda: ";
    cin >> platNomor;

    switch(platNomor)
    {
        case 'L':
            cout << "Surabaya";
            break;

        case 'B':
            cout << "Jakarta";
            break;

        case 'D':
            cout << "Bandung";
            break;

        case 'N':
            cout << "Malang/Lumajang";
            break;

        default:
            cout << "Karakter plat nomor tidak diketahui";
    } 
    return 0;
}
```

Dalam contoh di atas, **ekspresi** yang digunakan adalah **PlatNomor**, di mana **case-case** nya adalah, huruf plat nomor tersebut, L, B, D, N, dan sebagainya.

## Operator Kondisional (` ? : `)

Operator kondisional mempunyai bentuk sintaks sebagai berikut:

```
(ekspresi/kondisi) ? (ekspresi jika TRUE) : (ekspresi jika FALSE);
```

Operator kondisional adalah satu-satunya operator ternary dalam bahasa C++. Operator kondisional bertingkah seperti layaknya percabangan `if - else`. Ekspresi/kondisi yang akan dievaluasi diletakkan sebelum tanda tanya (`?`). Apabila menghasilkan **TRUE**, maka program akan mengeksekusi bagian di **kiri** tanda titik dua. Jika **FALSE**, akan mengeksekusi bagian di **kanan** tanda titik dua.

Contoh:

```cpp
#include <iostream>
using namespace std;

int main()
{
    int mark;
    
    cin >> mark;
    cout << (mark >= 75 ? "Lulus\n" : "Tidak Lulus\n");

    return 0;
}
```

Program di atas ekuivalen dengan:

```cpp
#include <iostream>
using namespace std;

int main()
{
    int mark;
    
    cin >> mark;
    if (mark >= 75) {
        cout << "Lulus\n";
    } else {
        cout << "Tidak Lulus\n";
    }
    return 0;
}
```

# Perulangan

Perulangan atau _looping_ memungkinkan kita untuk mengeksekusi potongan kode berulang-ulang hingga mencapai suatu kondisi. Ada 3 jenis perulangan dalam bahasa C++, yaitu `while`, `do - while`, dan `for`.

## Perulangan While

Perulangan `while` adalah bentuk perulangan yang paling sederhana. Sintaksnya adalah sebagai berikut.

```cpp
//initial value misal, i = 0
while (<Ekspresi/Kondisi>) {
    // Potongan kode yang ingin dieksekusi
    .
    .
    .
    // increment/decrement misalnya, i++
}
```
Cara kerja perulangan `while` mirip dengan `if`. Jika pada **if** potongan kode akan dieksekusi **sekali saja** apabila ekspresi/kondisi bernilai **TRUE**, pada **while** potongan kode akan **terus dieksekusi** hingga ekspresi/kondisi menghasilkan **FALSE**.

Contoh

```cpp
#include <iostream>
using namespace std;

int main()
{
    int i = 0;
    while (i < 10)
    {
        cout << "Hello World! ke-" <<  i << "\n";
        i++;
    }
    return 0;
}
```

Sehingga pada contoh di atas:

- Pada awalnya, **variabel `i`** bernilai 0. 
- Sequence selanjutnya adalah `while`, dan i bernilai kurang dari 10 (**TRUE**), maka kode didalam `while` akan dijalankan, yakni print Hello world ke-i. 
- Setelah melakukan print hello world, **variabel `i`** akan di increment, dan kembali ke statement `while` untuk memeriksa apakah **`i`** masih kurang dari 10 setelah di-increment
- Karena setelah **`i`** di-increment nilainya masih 1 dan kurang dari 10, maka `while` akan dijalankan lagi hingga **`i`** bernilai 10 yang berarti tidak memenuhi kondisi `while`.

## Perulangan Do-While

Sintaks dari perulangan `do – while` adalah sebagai berikut.
```cpp
do {
    // Potongan kode yang dieksekusi.
    .
    .
    // increment/decrement
} while (<Ekspresi/Kondisi>)
```

Cara kerja dari perulangan `do – while` mirip dengan perulangan `while`. Hanya saja, pada perulangan `do – while`, potongan kode dijamin akan dieksekusi tepat satu kali sebelum mengevaluasi ekspresi/kondisi.

Contoh

```cpp
#include <iostream>
using namespace std;

int main()
{
    int num = 0;
    do
    {
        cout << "Num sekarang adalah " << num << "\n";
        cout << "Masukkan bilangan integer positif (-1 untuk keluar ): ";
        cin >> num;
    } while (num != -1);
    return 0;
}
```

## Perulangan For

Perulangan `for` merupakan perulangan paling rumit diantara perulangan lainnya. Sintaksnya adalah sebagai berikut.

```cpp
for (init_statement; kondisi/ekspresi; end_statement) {
    //  Potongan kode yang dieksekusi
    .
    .
}
```

Cara kerjanya adalah sebagai berikut:
- Bagian `init_statement` digunakan untuk inisialisasi variabel yang akan digunakan dalam perulangan. Bagian ini hanya dijalankan sekali saka pada saat awal perulangan.
- Selanjutnya `kondisi/ekspresi` akan dievaluasi. Jika menghasilkan **TRUE**, maka akan mengeksekusi potongan kode. Jika menghasilkan **FALSE**, maka perulangan berhenti.
- Setelah potongan kode selesai dieksekusi, akan mengeksekusi bagian `end_statement`. Biasanya bagian ini digunakan sebagai **increment/decrement**.
- Lalu akan **mengevaluasi ekspresi/kondisi lagi**, dan begitu seterusnya.

Contoh

```cpp
#include <iostream>
int main()
{
    int i;
    //    init;condition; increment
    for (i = 0; i < 10  ; i++) {
        cout << "Hello World!\n";
    }
}
```
1. Awalnya **`i`** bernilai 0
2. For statement akan memeriksa nilai **`i`** apakah kurang dari 10
3. Apabila **TRUE** maka jalankan kode dalam for block, yakni print hello world
4. Setelah command dalam block for selesai dijalankan, maka variabel **`i`** akan di-increment, dan diperiksa lagi.
5. Apabila **`i`** kurang dari 10, maka command dalam block dieksekusi, apabila tidak maka for loop akan berhenti

## Perulangan/Percabangan Bersarang (Nested)

Percabangan dan perulangan juga dapat dibuat secara bersarang (membuat percabangan/perulangan di dalam percabangan/perulangan), tentu saja menyesuaikan kebutuhan. Contoh berikut adalah perulangan `for` bersarang.
```cpp
int i, j;
for (i = 1; i <= 10; ++i) {
    // Statement yang ingin dijalankan pada level terluar

    for (j = 1; j <= 10; j++) {
        // Statement yang ingin dijalankan pada level terdalam

        // Percabangan di dalam perulangan
        if (i == 10) {
            // Lakukan sesuatu
        }
    }
    // Statement yang ingin dijalankan pada level terluar
}
```

# Break dan Continue
Keyword `break` dan `continue` digunakan untuk mengendalikan (kontrol) alur pada perulangan. Berikut penjelasannya.

## Break
Perintah `break` digunakan untuk **menghentikan** perulangan (secara paksa). Apabila perintah `break` pada suatu perulangan dijalankan, maka perulangan tersebut akan **dihentikan (secara paksa) dari titik dimana perintah break muncul**.

Contoh

```cpp
#include <iostream>
using namespace std;

int main()
{
	int i;
	for (i = 1; i <= 6; i++) {
		cout << i << "\n";
		//   Jika i adalah 4, maka keluar dari perulangan
		if (i == 4) {
			break;
		}
	}
	return 0;
}
```

## Continue

Kebalikan dari perintah break, perintah `continue` digunakan untuk **melanjutkan perulangan**. Pada perulangan, apabila menemui perintah `continue`, maka perintah-perintah dibawah `continue` akan **diabaikan** dan **kembali akan mengevaluasi ekspresi/kondisi**. Sedangkan pada perulangan `for` akan langsung mengekekusi bagian end_statement kemudian mengevaluasi ekspresi/kondisi.

Contoh

```cpp
#include <iostream>
using namespace std;

int main()
{
	int i;
    for (i = 1; i <= 6; i++) {
	    // Jika i adalah 4, maka abaikan perintah printf()
        if (i == 4) {
            continue;
        }
       	cout << i << "\n";
    }
    return 0;
}
```

# Infinite Loop

Infinite loop adalah kasus di mana perulangan tidak akan pernah berhenti. Hal ini terjadi karena perulangan tidak akan pernah menemui kondisi yang membuatnya berhenti. Contoh di bawah akan menghasilkan infinite loop.

```cpp
#include <iostream>
using namespace std;

int main()
{
    int i;
    for (i = 1; i <= 100; i--) {
        // Perulangan tak akan pernah berhenti
    }
}
```

# Array

## Pengenalan Array

Array merupakan jenis struktur data yang menampung elemen betipe data sama secara sekuensial dengan ukuran (kapasitas) yang tetap (_fixed-size_). Bayangkanlah sebuah array sebagai sekumpulan elemen sejenis yang disusun secara berurutan pada satu _identifier_ (nama).

## Deklarasi Array

Array juga sama seperti variabel, perlu dideklarasikan terlebih dahulu sebelum bisa digunakan. Deklarasi array sama seperti variabel, hanya saja saat pendeklarasiannya perlu dituliskan ukurannya.

```
tipe_data identifier_array[size];
```

## Inisialisasi Array

Kita juga bisa menginisialisasi elemen-elemen pada array setelah dideklarasikan. Sintaksnya adalah seperti berikut.

```
tipe_data identifier_array[size] = {elem1, elem2, elem3, ....}
```

## Mengakses Array

Seperti yang telah dijelaskan sebelumnya, array disimpan secara sekuensial (pada blok memori secara berurutan). Lalu bagaimana kita mengakses tiap elemennya? Pengaksesan elemen pada array dilakukan dengan menuliskan _identifier_ array-nya lalu digabung dengan menggunakan operator subscript `[]` dengan menyertakan indeks didalamnya.

![akses_array](https://github.com/Algoritma-dan-Pemrograman-ITS/DasarPemrograman/blob/master/img/Array_access.png?raw=true)

Indeks pada array menggunakan _zero-based index_, yang artinya elemen pertama pada array ditunjukkan oleh indeks ke 0 (bukan ke 1) dan elemen terakhir ditunjukkan oleh indeks ke N-1 (misal N adalah panjang array).
Elemen-elemen pada array dapat diperlakukan sama seperti halnya variabel. Kita dapat melakukan assignment, operasi aritmatika, dan lain-lain.

Contoh:

```cpp
#include <iostream>
using namespace std;

int main () 
{

  int a[10]; //Deklarasi Array
  
  int b[5] = {1, 2, 3, 4, 5}; //Inisialisasi Array
  
  a[0] = 50;
  a[1] = 20;

  cout << a[0] << " " << a[1] << "\n";
  
  return 0;

}
```

Mengapa kita perlu array? Andaikan kita membutuhkan 1000 inputan data, kita tidak perlu membuat deklarasi variabel berjumlah 1000, misalkan variabel a1 hinga a1000. Namun, kita cukup menuliskan 1 identifier array berkapasitas 1000.

Contoh program tanpa array:
```cpp
#include <iostream>
using namespace std;

int main () {

  int a, b, c, d, e; //Deklarasi 5 variabel integer
  
  cin >> a >> b >> c >> d >> e;

  cout << "Bilangan pertama adalah " << a << "\n";
  cout << "Bilangan kedua adalah " << b << "\n";
  cout << "Bilangan ketiga adalah " << c << "\n";
  cout << "Bilangan keempat adalah " << d << "\n";
  cout << "Bilangan kelima adalah " << e << "\n";
  
  return 0;

}
```

Bayangkan kita tidak hanya memasukkan 5 data, melainkan 1000 data, bagaimana kita mendeklarasikan semuanya dalam variabel dan kemudian mencetaknya? Maka dari itulah array digunakan.

Contoh program menggunakan array:
```cpp
#include <iostream>
using namespace std;

int main () 
{
	int a[5], i; 
	for(i = 0; i < 5; i++) {
		cin >> a[i];
	}

	for(i = 0; i < 5; i++) {
		cout << "Bilangan ke-" << i+1 << " adalah " << a[i] << "\n";
	}

	return 0;

}
```
## Dimensi Array

### Array Satu Dimensi

Sebuah array dikatan berdimensi satu apabila tiap elemennya hanya menyimpan satu data/objek. Contoh-contoh pada penjelasan sebelumnya merupakan array satu dimensi.

Contoh array satu dimensi:

```cpp
int main()
{
	int arr[5];
	arr[0] = 4;
	arr[1] = 2;
	arr[2] = 3;
	return 0;
}
```

Jika diilustrasikan, maka array tersebut akan tampak seperti di bawah.

![array-satu-dimens](https://github.com/Algoritma-dan-Pemrograman-ITS/DP_modul-2/blob/master/img/1D_Array.png)

### Array Multidimensi

Sebuah array dikatakan multidimensional apabila tiap elemen array  menampung array lainnya. Apabila array satu dimensi hanya memiliki sebuah index, array multidimensi memiliki dua atau lebih index untuk mengakses elemen dalam array tersebut. 

Cara deklarasinya pun berbeda dari array satu dimensi. Kita memerlukan N buah kurung siku untuk membuat array dengan N-dimensi.

Berikut adalah contoh program dengan array dua dimensi:
```cpp
int main () 
{
	int matriks[5][6];
	matriks[2][3] = 100;
	matriks[1][4] = 200;
	return 0;
}
```

Apabila diilustrasikan, bentuk array dua dimensi layaknya baris dan kolom, seperti gambar di bawah.

![array-dua-dimensi](https://github.com/Algoritma-dan-Pemrograman-ITS/DP_modul-2/blob/master/img/2D_Array.png)

Selain bentuk dua dimensi, kita dapat membuat array hingga N-dimensi, sesuai kebutuhan.

# String

## Pengenalan String

Secara umum, string merupakan kumpulan dari satu atau lebih karakter. Pada bahasa C++, string didefinisikan sebagai kumpulan karakter yang diakhiri oleh karakter null (`'\0'`). Intinya adalah, string merupakan sebuah `array` dari tipe data `char`

Misalkan string `"Dasar"`, pada bahasa C++ direpresentasikan sebagai kumpulan karakter `'D'`, `'a'`, `'s'`, `'a'`, `'r'`, dan `'\0'`.

## Representasi String

Contoh pendeklarasian string:
```cpp
#include <iostream>
using namespace std

int main () 
{  
	char str[] = "Halo"; 
	return 0;
}
```

Contoh di atas akan mendeklarasikan string bernama str dengan kapasitas 5 karakter, di mana `str[0] = 'H'`, `str[1] = 'a'`, `str[2] = 'l'`, `str[3] = 'o'`, dan `str[4] = '\0'`.
Perhatikan bahwa str[4] berisi karakter '\0' (null character), walaupun dalam literal string di atas tidak ada karakter tersebut. 

Dalam bahasa C++, karakter null digunakan untuk menandakan akhir dari sebuah string.

Contoh pendeklarasian string (2):
```cpp
#include <iostream>
using namespace std;

int main () {
  
  char array[10];
  
  return 0;
}
```
Contoh di atas akan mendeklarasikan string bernama array yang dapat menampung maksimal 10 karakter, termasuk null character.

Selain itu, kita dapat mendeklarasikan string sebagai tipe data `string` yang tersedia dalam library `<string>`

Contoh pendeklarasian string (3):
```cpp
#include <iostream>
#include <string>
using namespace std;

int main () {
  
  string arr = "ini adalah string";
  
  return 0;
}
```

Untuk menerima input string dari user, kita dapat menggunakan `cin`

Contoh source code penggunaan `cin` untuk membaca string:
```cpp
#include <iostream>
#include <string>
using namespace std;

int main () {
  
	string arr;
	while(1)
	{
		cin >> arr;
		cout << "-- " << arr << "\n";
	}
	return 0;

}
```

String yang dibaca dengan mengunakan `cin` akan secara otomatis memiliki null character di akhir.

Karena string pada dasarnya hanyalah sebuah array, kita dapat mengakses karakter individual sebuah string layaknya kita mengakses array seperti berikut:
```cpp
#include <iostream>
#include <string>
using namespace std;

int main () {
  
  string arr = "ini adalah string";
  cout << arr[0] << arr[1] << arr[2];

  return 0;
}
```


## Fungsi-Fungsi String

> Dalam bahasa pemrograman C++, terdapat library yang dibuat dengan tujuan memudahkan pengguna dalam mengolah string. Library tersebut tersimpan dalam `<string>`, oleh karena itu, untuk mengakses library ini, diperlukan tambahan preprocessor, yaitu:

```cpp
#include <string>
```
Berikut adalah beberapa fungsi dan penjelasannya.

### Fungsi `copy` 
Fungsi `copy` digunakan untuk melakukan copy dari sebuah string ke string lainnya. 
Contoh penggunaan dalam kode program: Contoh penggunaan dalam kode program:
```cpp
#include <iostream>
#include <string>
using namespace std;

int main () {
	string = "Halo";
	string b;
	
	// Copy string a ke string b
	b = a;

	cout << b << "\n";	
	return 0;
}
```

### Fungsi `Concatenation` 
Fungsi `concat` digunakan untuk melakukan penempelan sebuah string pada **akhir** string yang lain. 
Contoh penggunaan dalam kode program:

```cpp
#include <iostream>
#include <string>
using namespace std;

int main () {
	string a = "Halo";
	string b = " Kawan";
	string c;
	
	// Copy string a ke string b
	c = a;
	
	// Tempelkan string b ke akhir string c
	c += b;
	
	cout << c << "\n";
	
	return 0;

}
```

### Fungsi `comparison`
Fungsi `comparison` digunakan untuk melakukan **pembandingan** sebuah string dengan string yang lain.  

Berikut adalah contoh penggunaan fungsi ini dalam kode progam:
```cpp
#include <iostream>
#include <string>
using namespace std;

int main () {
	string a = "Halo";
	string b = "Hai";
	string c = "Halo";
	
	if(a == b) cout << "String a sama dengan b\n";
	else cout << "String a tidak sama dengan b\n";
	
	if(a == c) cout << "String a sama dengan c\n";
	else cout << "String a tidak sama dengan c\n";
	
	return 0;

}
```

### Fungsi `length`
Fungsi `length` digunakan untuk mengetahui **panjang** dari sebuah string.
```cpp
#include <iostream>
#include <string>
using namespace std;

int main () {
	string a = "Halo";
	
	cout << "Panjang string a adalah " << a.length() << "\n";
	
	return 0;

}
```
