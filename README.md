# Tugas Flutter
Nama  : Fathi Qushoyyi Ahimsa

NPM   : 2206082120

Kelas : PBP C

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
