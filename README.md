# Flutter Row, Column, dan Counter Example

## Gambaran Umum

Project ini merupakan aplikasi Flutter sederhana yang mendemonstrasikan beberapa konsep dasar Flutter, seperti:

* **StatelessWidget**
* **StatefulWidget**
* **Layout menggunakan Row dan Column**
* **Styling menggunakan Container**
* **Menampilkan gambar dari internet**
* **Responsive layout menggunakan MediaQuery**
* **Manajemen state menggunakan setState()**

Aplikasi ini menampilkan:

* Sebuah gambar dari internet
* Teks deskripsi
* Kategori ikon
* Counter sederhana yang bisa ditambah dengan tombol

---

# Struktur Konsep Aplikasi

Aplikasi ini terdiri dari tiga komponen utama:

1. **MyApp** → Root widget dari aplikasi
2. **RowColumnPage** → Layout utama aplikasi
3. **CounterCard** → Komponen counter yang interaktif

---

# 1. Import Library Material Flutter

```dart
import 'package:flutter/material.dart';
```

Baris ini digunakan untuk mengimpor **library Material Design** milik Flutter.

Library ini menyediakan berbagai widget UI seperti:

* Scaffold
* AppBar
* Text
* Row
* Column
* Container
* Icon

Semua widget tersebut mengikuti standar desain **Material Design dari Google**.

---

# 2. Fungsi Main (Entry Point Aplikasi)

```dart
void main() {
  runApp(const MyApp());
}
```

Fungsi `main()` adalah **titik awal eksekusi program Flutter**.

Penjelasan:

* `runApp()` digunakan untuk menjalankan aplikasi Flutter
* `MyApp` adalah widget utama yang akan ditampilkan pertama kali

---

# 3. Class MyApp (Root Widget)

```dart
class MyApp extends StatelessWidget {
  const MyApp({super.key});
```

Class ini merupakan **widget utama dari aplikasi**.

Class ini menggunakan **StatelessWidget**, yang berarti:

* Widget ini **tidak memiliki state yang berubah selama aplikasi berjalan**

---

## Method build()

```dart
@override
Widget build(BuildContext context)
```

Method `build()` berfungsi untuk **mendefinisikan tampilan UI** dari widget.

Flutter akan memanggil method ini setiap kali UI perlu diperbarui.

---

## MaterialApp

```dart
return MaterialApp(
  title: 'Flutter Demo',
```

`MaterialApp` adalah widget utama yang menyediakan fitur seperti:

* Navigasi aplikasi
* Pengaturan tema
* Routing halaman
* Judul aplikasi

---

## Konfigurasi Tema

```dart
theme: ThemeData(
  colorScheme: ColorScheme.fromSeed(seedColor: Colors.deepPurple),
  useMaterial3: true,
),
```

Bagian ini mengatur **tema visual aplikasi**.

Penjelasan:

* `ColorScheme.fromSeed()` menghasilkan palet warna otomatis
* `seedColor` menentukan warna utama
* `useMaterial3: true` menggunakan **Material Design versi terbaru**

---

## Halaman Utama

```dart
home: const RowColumnPage(),
```

Baris ini menentukan **halaman pertama yang ditampilkan ketika aplikasi dijalankan**.

Widget yang digunakan adalah **RowColumnPage**.

---

# 4. Widget RowColumnPage

```dart
class RowColumnPage extends StatelessWidget
```

Widget ini merupakan **layout utama aplikasi**.

Widget ini menggunakan **StatelessWidget** karena tampilannya tidak berubah secara dinamis.

---

# 5. MediaQuery (Mendapatkan Ukuran Layar)

```dart
MediaQueryData mediaQueryData = MediaQuery.of(context);
double screenWidth = mediaQueryData.size.width;
double screenHeight = mediaQueryData.size.height;
```

`MediaQuery` digunakan untuk mendapatkan informasi tentang layar perangkat, seperti:

* lebar layar
* tinggi layar
* orientasi perangkat

Hal ini berguna untuk membuat **layout yang responsif**.

---

# 6. Scaffold (Struktur Halaman)

```dart
return Scaffold(
```

`Scaffold` menyediakan struktur dasar halaman pada aplikasi Flutter.

Biasanya terdiri dari:

* AppBar
* Body
* FloatingActionButton
* Drawer

---

# 7. AppBar

```dart
appBar: AppBar(
  title: const Text(
    'My First App',
    style: TextStyle(color: Colors.black),
  ),
  backgroundColor: Colors.orange[200],
  centerTitle: true,
),
```

AppBar adalah **bar navigasi di bagian atas aplikasi**.

Fitur yang digunakan:

* Judul aplikasi
* Warna background
* Judul berada di tengah

---

# 8. Layout Utama Menggunakan Column

```dart
body: Column(
```

`Column` digunakan untuk menyusun widget **secara vertikal dari atas ke bawah**.

Konfigurasi:

```dart
crossAxisAlignment: CrossAxisAlignment.center,
mainAxisAlignment: MainAxisAlignment.center,
```

Penjelasan:

| Properti           | Fungsi                     |
| ------------------ | -------------------------- |
| mainAxisAlignment  | mengatur posisi vertikal   |
| crossAxisAlignment | mengatur posisi horizontal |

---

# 9. Bagian Gambar

```dart
Image.network(
  'https://picsum.photos/200',
  fit: BoxFit.cover,
  width: 500,
)
```

Widget ini digunakan untuk **menampilkan gambar dari internet**.

Penjelasan:

* `Image.network()` mengambil gambar dari URL
* `fit: BoxFit.cover` membuat gambar menyesuaikan ukuran container
* `width: 500` mengatur lebar gambar

Gambar dibungkus dengan widget:

* `Container`
* `AspectRatio`

`AspectRatio` memastikan gambar memiliki **rasio persegi (1:1)**.

---

# 10. Bagian Teks

```dart
Text(
  'What image is that',
  style: TextStyle(fontSize: 16)
)
```

Widget ini menampilkan teks deskripsi di bawah gambar.

Container di sekitarnya memberikan:

* margin
* padding
* warna background

---

# 11. Bagian Kategori Ikon

```dart
Row(
  mainAxisAlignment: MainAxisAlignment.spaceEvenly,
```

`Row` digunakan untuk menyusun widget **secara horizontal**.

Di dalam Row terdapat **3 Column**.

Setiap Column berisi:

```
Icon
Text
```

Contoh:

```
Column(
  children: [
    Icon(Icons.food_bank),
    Text("Food")
  ]
)
```

Kategori yang ditampilkan:

| Ikon | Kategori |
| ---- | -------- |
| 🍔   | Food     |
| 🏞️  | Scenery  |
| 👥   | People   |

---

# 12. Widget CounterCard

```dart
CounterCard()
```

Widget ini adalah komponen **counter interaktif**.

Widget ini menggunakan **StatefulWidget** karena datanya dapat berubah.

---

# 13. StatefulWidget

```dart
class CounterCard extends StatefulWidget
```

`StatefulWidget` digunakan ketika UI **memiliki data yang bisa berubah**.

Contoh penggunaan:

* counter
* animasi
* input pengguna
* data dari API

---

# 14. Variabel Counter

```dart
int _counter = 0;
```

Variabel ini menyimpan **nilai counter saat ini**.

Tanda `_` menunjukkan bahwa variabel bersifat **private**.

---

# 15. Fungsi Increment Counter

```dart
void _incrementCounter() {
  setState(() {
    _counter++;
  });
}
```

Penjelasan:

* `_counter++` menambah nilai counter
* `setState()` memberi tahu Flutter bahwa UI harus diperbarui

Tanpa `setState()`, perubahan nilai tidak akan terlihat di layar.

---

# 16. Tampilan Counter

```dart
Text("Counter here: $_counter")
```

Widget ini menampilkan nilai counter.

Contoh output:

```
Counter here: 3
```

---

# 17. Tombol Penambah Counter

```dart
IconButton(
  onPressed: _incrementCounter,
  icon: Icon(Icons.add),
)
```

Ketika tombol ditekan:

1. Fungsi `_incrementCounter()` dipanggil
2. Nilai `_counter` bertambah
3. `setState()` dijalankan
4. UI diperbarui dengan nilai counter terbaru

---

# Struktur Tampilan Akhir

Urutan tampilan aplikasi:

```
AppBar
   ↓
Gambar
   ↓
Teks deskripsi
   ↓
Kategori ikon (Row)
   ↓
Counter
```

---

# Konsep Flutter yang Dipelajari

Project ini mendemonstrasikan beberapa konsep dasar Flutter, yaitu:

* Arsitektur UI berbasis widget
* Perbedaan StatelessWidget dan StatefulWidget
* Layout menggunakan Row dan Column
* Styling menggunakan Container
* Layout responsif dengan MediaQuery
* Manajemen state menggunakan setState
* Event handling pada tombol
* Menampilkan gambar dari internet

---

# Cara Menjalankan Project

1. Install Flutter SDK
2. Buka folder project
3. Jalankan perintah berikut:

```
flutter pub get
flutter run
```

---

