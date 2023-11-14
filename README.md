# Tugas Flutter
Nama  : Fathi Qushoyyi Ahimsa

NPM   : 2206082120

Kelas : PBP C

## Tugas 8

### Pertanyaan Tugas 8
1. Jelaskan perbedaan antara Navigator.push() dan Navigator.pushReplacement(), disertai dengan contoh mengenai penggunaan kedua metode tersebut yang tepat!
Navigator.push() dan Navigator.pushReplacement() adalah dua metode yang digunakan dalam Flutter untuk mengelola navigasi antar halaman (page navigation) dalam aplikasi.
**Navigator.push():** Metode ini digunakan untuk menambahkan halaman baru ke dalam stack navigasi. Saat menggunakan Navigator.push(), halaman baru akan ditempatkan di atas halaman saat ini, dan pengguna dapat kembali ke halaman sebelumnya dengan tombol "back" pada perangkat.

Contoh penggunaan Navigator.push():
```dart
onPressed: () {
  Navigator.push(
    context,
    MaterialPageRoute(builder: (context) => Menu()),
  );
}
```

**Navigator.pushReplacement():** Metode ini juga menambahkan halaman baru ke dalam stack navigasi, tetapi dengan menggantikan halaman saat ini. Ini berarti halaman saat ini akan dihapus dari tumpukan, dan halaman baru akan menjadi halaman terbaru. Pengguna tidak dapat kembali ke halaman sebelumnya, karena halaman tersebut telah digantikan.

Contoh penggunaan Navigator.pushReplacement():
```dart
onPressed: () {
  Navigator.pushReplacement(
    context,
    MaterialPageRoute(builder: (context) => HalamanGantian()),
  );
}
```

2. Jelaskan masing-masing layout widget pada Flutter dan konteks penggunaannya masing-masing!

**Layout Widget pada Flutter:**

1. **Container:** Digunakan untuk mengelilingi widget lain dan memberikan properti seperti padding, margin, dan dekorasi. Cocok untuk mengatur tata letak dan penataan widget di dalamnya.

```dart
Container(
  padding: EdgeInsets.all(16.0),
  margin: EdgeInsets.symmetric(vertical: 8.0),
  decoration: BoxDecoration(
    color: Colors.blue,
    borderRadius: BorderRadius.circular(8.0),
  ),
  child: Text('Isi Container'),
)
```

2. **Row dan Column:** Row digunakan untuk menempatkan widget dalam satu baris secara horizontal, sementara Column digunakan untuk menempatkan widget dalam satu kolom secara vertikal.

```dart
Row(
  children: [
    Icon('Kolom 1'),
    Text('Kolom 2'),
  ],
)

Column(
  children: [
    Text('Baris 1'),
    Text('Baris 2'),
  ],
)
```

3. **ListView:** Digunakan untuk menampilkan daftar item yang dapat di-scroll. Cocok untuk menampilkan data dinamis secara singkat.

```dart
ListView(
  children: [
    ListTile(
      title: Text('Item 1'),
    ),
    ListTile(
      title: Text('Item 2'),
    ),
    // ...
  ],
)
```

4. **Stack:** Digunakan untuk menumpuk widget di atas satu sama lain. Cocok untuk membuat tata letak kompleks.

```dart
Stack(
  children: [
    Image(...),
    Positioned(
      bottom: 10.0,
      right: 10.0,
      child: Text('Posisi Teks'),
    ),
  ],
)
```

5. **Expanded dan Flexible:** Digunakan dalam Row atau Column untuk memberikan fleksibilitas pada ukuran widget child. Expanded membuat widget memenuhi sebanyak mungkin ruang yang tersedia, sementara Flexible memberikan kontrol terhadap seberapa banyak ruang yang diambil oleh child.

```dart
Row(
  children: [
    Expanded(
      child: Container(color: Colors.red),
    ),
    Container(color: Colors.blue),
  ],
)

Row(
  children: [
    Flexible(
      flex: 2,
      child: Container(color: Colors.red),
    ),
    Flexible(
      flex: 1,
      child: Container(color: Colors.blue),
    ),
  ],
)
```

6. **GridView:** Digunakan untuk menampilkan widget dalam tata letak grid (kotak). Cocok untuk menampilkan koleksi item dalam grid.

```dart
GridView.builder(
  gridDelegate: SliverGridDelegateWithFixedCrossAxisCount(
    crossAxisCount: 2,
    crossAxisSpacing: 8.0,
    mainAxisSpacing: 8.0,
  ),
  itemBuilder: (context, index) {
    return Container(
      color: Colors.green,
    );
  },
)
```

3. Sebutkan apa saja elemen input pada form yang kamu pakai pada tugas kali ini dan jelaskan mengapa kamu menggunakan elemen input tersebut!

**Elemen Input pada Form:**
TextFormField adalah widget dalam Flutter yang digunakan untuk membuat kolom input teks yang dapat menerima masukan dari pengguna. Beberapa fitur yang sering digunakan:

- Memproses Input Pengguna: TextFormField memproses input pengguna dengan validasi otomatis.
- Pemberian Label dan Hints: Mendukung label dan teks hint untuk memberikan panduan kepada pengguna.
- Validasi Input: TextFormField memungkinkan penggunaan fungsi validasi untuk memastikan input sesuai dengan kriteria tertentu sebelum diproses lebih lanjut.

```dart
TextFormField(
  decoration: InputDecoration(
    labelText: 'Nama Pengguna',
    hintText: 'Masukkan nama pengguna',
    icon: Icon(Icons.person),
  ),
  validator: (value) {
    if (value.isEmpty) {
      return 'Nama pengguna tidak boleh kosong';
    }
    return null;
  },
  onSaved: (value) {
    print('Nama Pengguna: $value');
  },
)
```
4. Bagaimana penerapan clean architecture pada aplikasi Flutter?
**Penerapan Clean Architecture pada Aplikasi Flutter:**
Penerapan Clean Architecture pada aplikasi Flutter melibatkan struktur proyek yang modular dan mudah diuji. Ini melibatkan pembagian proyek menjadi tiga lapisan utama: Presentasi (Presentation Layer), Bisnis (Business Layer), dan Data (Data Layer).

- **Lapisan Presentasi (Presentation Layer):** Berisi widget, tata letak, dan logika presentasi terkait antarmuka pengguna.

- **Lapisan Bisnis (Business Layer):** Berisi logika bisnis dan aturan aplikasi, termasuk use case atau interactor yang mengimplementasikan fungsionalitas spesifik aplikasi.

- **Lapisan Data (Data Layer):** Menangani akses data ke penyimpanan lokal atau sumber data eksternal, dengan repository sebagai perantara antara lapisan bisnis dan sumber data.

Struktur proyek dapat diorganisir dengan membuat folder untuk file .dart yang berbeda, seperti screens, widgets, dan lainnya.

5. Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step! (bukan hanya sekadar mengikuti tutorial)

Saya membuat sebuah file Dart baru dengan nama shoplist_form.dart. Di dalamnya, saya membuat dua kelas: ShopFormPage untuk menampilkan halaman formulir dan _ShopFormPageState untuk mengelola halaman formulir. Pada method build di _ShopFormPageState, saya menggunakan widget Scaffold sebagai template form. Saya membuat objek form untuk menangani formulir dengan validasi dan mengelompokkan tiga elemen masukan (nama item, jumlah item, dan deskripsi item) menggunakan TextFormField.

Untuk tombol Save, saya menggunakan widget ElevatedButton untuk menyimpan data ke form saat ditekan. Validasi dilakukan melalui atribut key dari Form yang diinisialisasi dengan GlobalKey<FormState();>.

Ketika pengguna menekan tombol Tambah Item pada halaman utama, saya menambahkan logika kondisional pada berkas item_card.dart. Jika tombol yang ditekan memiliki nama "TambahItem", aplikasi akan mengarahkan pengguna ke halaman formulir menggunakan Navigator.push() dan menuju kelas ShopFormPage.

Setelah pengguna mengisi formulir dan menekan tombol Save pada halaman formulir, data akan muncul dalam sebuah pop-up. Di berkas item_form.dart, saya menambahkan tombol "Save" menggunakan ElevatedButton. Saat tombol ini ditekan, validasi dilakukan menggunakan kunci form (key). Jika validasi berhasil, saya menggunakan showDialog untuk menampilkan pop-up dengan informasi item yang akan ditambahkan.

Selanjutnya, saya membuat sebuah file Dart bernama left_drawer.dart untuk menampilkan drawer aplikasi. Di dalamnya, saya membuat kelas LeftDrawer yang bersifat stateless. Dalam widget build, saya menggunakan ListView untuk membangun drawer. Saya menggunakan DrawerHeader untuk membuat bagian header drawer dengan warna indigo, judul, dan sub-judul yang sesuai.

Kemudian, saya membuat isi drawer menggunakan ListTile sebagai item pada ListView. ListTile pertama menampilkan "Halaman Utama," dan ketika ditekan, menggunakan Navigator.pushReplacement() untuk mengarahkan ke kelas MyHomePage(). ListTile berikutnya merupakan item drawer untuk menuju ke form penambahan item, dengan Navigator.pushReplacement() menuju kelas ShopFormPage().



## Tugas 7
### Implementasi Kode
1. Membuat proyek  flutter baru dengan perintah `flutter create dataleakedapps`
2. Memindahkan class `MyHomePage` dan `_MyHomePageState` ke dalam file baru yang bernama `menu.dart`
3. Memperbaiki error yang terjadi di dalam file `main.dart`, yaitu pada baris yang berisi `home: const MyHomePage(title: 'Flutter Demo Home Page'),` dengan melakukan import `package:shopping_list/menu.dart`
4. Mengubah variabel colorScheme agar aplikasi mempunyai warna lain
5. Mengubah sifat widget menjadi stateless dengan mengubah `MyHomePage(title: 'Flutter Demo Home Page')` menjadi `MyHomePage()`
6. Mengubah sifat widget dari stateful menjadi stateless dengan mengubah interface dari MyHomePage menjadi `StatelessWidget`
7. Menambahkan class `ShopItem`seperti berikut ini:
```dart
class ShopItem {
  final String name;
  final IconData icon;
  final Color color;

  ShopItem(this.name, this.icon, this.color);
}
```
8. Menambahkan konfigurasi untuk setiap object dari `ShopItem` seperti berikut ini:
```dart
  final List<ShopItem> items = [
    ShopItem("Lihat produk", Icons.checklist_rounded, Colors.blue),
    ShopItem("Tambah produk", Icons.add_shopping_cart_rounded, Colors.red),
    ShopItem("Logout", Icons.logout_rounded, Colors.grey)
  ];
```
9. Mengubah widget dengan menggunakan `Container` seperti berikut:
```dart
Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('Data Leaked Apps'),
        backgroundColor: Colors.limeAccent,
      ),
      body: Container(
        decoration: const BoxDecoration(
          gradient: LinearGradient(
            colors: [Colors.blue, Colors.indigo],
            begin: Alignment.topCenter,
            end: Alignment.bottomCenter,
          ),
        ),
        child: SingleChildScrollView(
          child: Padding(
            //set padding dari halaman
            padding: const EdgeInsets.all(10.0),
            child: Column(
              children: <Widget>[
                const Padding(
                  padding: EdgeInsets.only(top: 10.0, bottom: 10.0),
                  //Widget text untuk menampilkan tulisan dengan alignmet center dan style yang sesuai
                  child: Text(
                    'Data Leaked Apps',
                    textAlign: TextAlign.center,
                    style: TextStyle(
                      fontSize: 30,
                      fontWeight: FontWeight.bold,
                      fontFamily: 'Roboto',
                    ),
                  ),
                ),

                //Grid Layout
                GridView.count(
                  //Container pada card kita
                  primary: true,
                  padding: const EdgeInsets.all(20),
                  crossAxisSpacing: 10,
                  mainAxisSpacing: 10,
                  crossAxisCount: 3,
                  shrinkWrap: true,
                  children: items.map((ShopItem item) {
                    //Iterasi untuk setiap item
                    return ShopCard(item);
                  }).toList(),
                ),
              ],
            ),
          ),
        ),
      ), // This trailing comma makes auto-formatting nicer for build methods.
    );
  }
```
10. Mengubah konfigurasi `ShopCard` menjadi seperti berikut:
```dart
Widget build(BuildContext context) {
    return Material(
      color: item.color,
      child: ClipRRect(
        borderRadius: BorderRadius.circular(10.0),
        child: InkWell(
          // Area responsive terhadap sentuhan
          onTap: () {
            // Memunculkan SnackBar ketika diklik
            ScaffoldMessenger.of(context)
              ..hideCurrentSnackBar()
              ..showSnackBar(SnackBar(
                  content: Text("Kamu telah menekan tombol ${item.name}!")));
          },
          child: Container(
            // Container untuk menyimpan Icon dan Text
            padding: const EdgeInsets.all(8),
            child: Center(
              child: Column(
                mainAxisAlignment: MainAxisAlignment.center,
                children: [
                  Icon(
                    item.icon,
                    color: Colors.white,
                    size: 30.0,
                  ),
                  const Padding(padding: EdgeInsets.all(3)),
                  Text(
                    item.name,
                    textAlign: TextAlign.center,
                    style: const TextStyle(color: Colors.white),
                  ),
                ],
              ),
            ),
          ),
        ),
      ),
    );
  }
```
### Pertanyaan Tugas 7
1. Apa perbedaan utama antara stateless dan stateful widget dalam konteks pengembangan aplikasi FLutter?
    `Stateless Widget = Widget yang tidak memiliki state internal`
    `Stateful Widget = Memiliki State Internal yang dapat berubah seiring waktu.`
    Stateless widget tidak mengalami perubahan sehingga cocok untuk bagian interface pengguna yang statis, seperti teks, ikon, dan tataletak
    Stateful widget dapat digunakan ketika widget perlu merespons perubahan dari input pengguna/data yang tersedia. Cocok untuk formulir, animasi, dan fitur lainnya yang perlu perubahan yang dinamis

2. Sebutkan seluruh widget yang kamu gunakan untuk menyelesaikan tugas ini dan jelaskan fungsinya masing-masing.
    
    `Scaffold:`

    Fungsi: Scaffold adalah kerangka kerja struktur dasar aplikasi Flutter. Ini menyediakan komponen dasar seperti AppBar, Drawer, BottomNavigationBar, dan Floating Action Button (FAB).
    Penggunaan: Scaffold digunakan sebagai struktur utama aplikasi untuk menyediakan komponen tata letak dasar.
    
    `AppBar:`

    Fungsi: AppBar adalah bilah aplikasi yang menampilkan judul dan opsional tombol aksi.
    Penggunaan: AppBar digunakan untuk menampilkan judul halaman atau aplikasi dan memungkinkan penggunaan tombol aksi seperti tombol kembali atau tombol menu navigasi.

    `Container`

    Fungsi: Container adalah widget umum yang mengizinkan kustomisasi tata letak dan dekorasi.
    Penggunaan: Container digunakan untuk mengatur padding, margin, dan dekorasi, serta memungkinkan penataan widget di dalamnya.
    
    `SingleChildScrollView:`

    Fungsi: SingleChildScrollView adalah widget yang memungkinkan scrolling konten di dalamnya ketika konten melebihi ukuran layar.
    Penggunaan: SingleChildScrollView digunakan ketika konten di dalamnya mungkin memerlukan scrolling, memastikan semua konten tetap dapat diakses oleh pengguna.
    
    `GridView.count:`

    Fungsi: GridView.count adalah widget untuk menampilkan data dalam bentuk grid dengan jumlah kolom tetap.
    Penggunaan: Digunakan untuk menampilkan daftar item (dalam hal ini, tombol-tombol menu) dalam bentuk grid.
    
    `InkWell:`

    Fungsi: InkWell adalah widget yang memberikan respons saat disentuh, dengan memberikan efek "splash" atau "ripple".
    Penggunaan: Digunakan untuk menambahkan respons saat tombol-tombol menu ditekan, misalnya menampilkan pesan Snackbar.
    
    `ClipRRect:`

    Fungsi: ClipRRect adalah widget yang memotong sudut dari child widget dan memberinya bentuk melengkung (rounded corners).
    Penggunaan: Digunakan di sekitar InkWell untuk memberikan bentuk rounded square pada tombol-tombol menu.
    
    `Icon:`
    z
    Fungsi: Icon adalah widget untuk menampilkan ikon material design.
    Penggunaan: Digunakan untuk menampilkan ikon di dalam tombol-tombol menu.
