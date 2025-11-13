# Praktikum 10

Project Modul 10 - Integrasi GUI, Navigasi, & API (JSON Serialization)

📖 Deskripsi

Project ini adalah modul integrasi yang menggabungkan hampir semua materi yang telah dipelajari. Anda akan membangun sebuah aplikasi lengkap yang:

Mendesain GUI: Menggunakan Card dan ListView (Modul 5 & 6).

Mengambil Data API: Menggunakan package http (Modul 6).

Mengelola Navigasi: Menggunakan Named Routes (Modul 7 & 8).

Mengirim Data: Mengirim arguments saat navigasi (Modul 8).

Perbedaan utama dari Modul 6 adalah, Anda sekarang akan menggunakan Model Class dan JSON Serialization (fromJson) untuk mengubah data JSON dari API menjadi objek Dart yang rapi. Ini adalah praktik standar industri.

🎯 Tujuan Utama Project

Desain GUI: Mendesain antarmuka yang responsif menggunakan ListView.builder dan Card.

Model Data (JSON Serialization): Mampu membuat class model (misal: GameModel) yang memiliki factory constructor fromJson() untuk mem-parsing data JSON secara aman dan terstruktur.

Integrasi API: Mengambil data dari API eksternal menggunakan http.get dan mengubah response JSON menjadi List berisi objek Model Anda.

Navigasi Terstruktur: Menerapkan Named Routes untuk mengelola perpindahan antar halaman (misal: dari halaman List ke halaman Detail).

Passing Data: Mengirim data (objek Model) sebagai arguments ke halaman detail saat item di-klik.

✅ Daftar Tugas (To-Do List)

Berikut adalah langkah-langkah untuk membangun aplikasi integrasi ini:

Buat Project Baru:

[ ] Buat "New Flutter Project" (misal: game_app_integration).

Tambahkan Dependency:

[ ] Buka pubspec.yaml dan tambahkan package: http.

[ ] Jalankan flutter pub get.

Buat Struktur File:

[ ] Buat file untuk main.dart (konfigurasi rute).

[ ] Buat file untuk home_page.dart (menampilkan ListView).

[ ] Buat file untuk detail_page.dart (menampilkan detail item).

[ ] Buat file untuk game_model.dart (definisi class model).

Buat Model Data (game_model.dart):

[ ] Buat class (misal: GameModel).

[ ] Tambahkan properti (final String title, final String genre, dll.).

[ ] Buat factory constructor GameModel.fromJson(Map<String, dynamic> json) untuk mem-parsing JSON.

Buat Fungsi API Service:

[ ] Buat fungsi async fetchGames() yang memanggil API (misal: FreeToGame).

[ ] Saat data JSON diterima, looping data tersebut dan ubah setiap item JSON menjadi objek GameModel menggunakan GameModel.fromJson().

[ ] Kembalikan Future<List<GameModel>>.

Konfigurasi main.dart:

[ ] Atur initialRoute: '/'.

[ ] Definisikan routes:

routes: {
  '/': (context) => HomePage(),
  '/detail': (context) => DetailPage(),
},


Kode Halaman Utama (home_page.dart):

[ ] Jadikan StatefulWidget.

[ ] Panggil fetchGames() di initState() atau gunakan FutureBuilder.

[ ] Tampilkan ListView.builder yang datanya berasal dari List<GameModel>.

[ ] Bungkus item list (misal: Card) dengan InkWell atau GestureDetector.

[ ] Di dalam onTap, panggil navigasi ke halaman detail sambil mengirim data game:
Navigator.pushNamed(context, '/detail', arguments: game);

Kode Halaman Detail (detail_page.dart):

[ ] Ambil data argumen: final game = ModalRoute.of(context)!.settings.arguments as GameModel;

[ ] Tampilkan data (game.title, game.genre, dll.) di body.

[ ] Tambahkan tombol "Kembali" (Navigator.pop(context)).
