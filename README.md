# 🎬 OBS Remote Control Web Interface

Sebuah antarmuka web (Web Interface) ringan untuk mengontrol OBS Studio dari jarak jauh melalui browser. Aplikasi ini dibuat menggunakan HTML, CSS, JavaScript (Vanilla), dan PHP (untuk menyimpan data To-Do List), yang dikomunikasikan ke OBS menggunakan **OBS WebSocket v5**.

Sangat cocok digunakan di tablet, smartphone, atau monitor kedua saat sedang melakukan live streaming, podcast, maupun recording.

## ✨ Fitur Utama

- **🚀 Koneksi Web-Socket Dinamis**: Menggunakan sistem Promise yang canggih untuk memastikan tidak ada delay antara web dan OBS.
- **🔄 Auto-Sync Status**: Saat berhasil terkoneksi, web akan otomatis membaca status asli dari OBS secara real-time (Volume, Mic Mute, Status Streaming & Recording, dan Scene yang aktif).
- **🎛️ Scene Switcher (Realtime Highlight)**: Menampilkan seluruh scene yang kamu miliki di OBS dan memberikan *highlight* (warna hijau menyala) pada scene yang saat ini sedang tayang (*Live*). Jika scene diganti dari OBS langsung, highlight di web juga otomatis ikut berpindah.
- **🎙️ Audio & Volume Control**:
  - Tombol untuk me-Mute/Unmute Mic/Aux.
  - Slider volume realtime untuk mengatur besaran volume **Desktop Audio** dan **Mic/Aux**.
- **📡 Kontrol Output**:
  - Tombol *Start / Stop Streaming*.
  - Tombol *Start / Stop Recording*.
  - Tombol *Save Replay Buffer*.
- **📷 Sembunyi/Tampil Kamera**: Matikan atau nyalakan kamera tertentu di dalam scene yang sedang aktif hanya dengan satu tombol (Nama source kamera dapat diubah sesuka hati).
- **📝 Ganti Teks (Text Overlay)**: Mengganti teks di OBS (cocok untuk ganti nama game, topik diskusi, atau nama Host) secara instan.
- **✅ To-Do List Interaktif**:
  - Catat tugas atau daftar rundown acara (tersimpan secara otomatis di server).
  - Terdapat tombol coret dan hapus.
  - Data tersimpan di `todo-data.json` melalui `save-todo.php`.

## ⚙️ Persyaratan (Prerequisites)

1. **OBS Studio** versi 28.0 ke atas (OBS WebSocket v5 sudah terintegrasi secara bawaan).
2. Web server lokal (misalnya **XAMPP, Laragon, MAMP**, atau **Nginx/Apache**) karena fitur penyimpanan *To-Do List* membutuhkan eksekusi file PHP (`save-todo.php`).

## 🛠️ Cara Pemasangan (Setup)

1. Ekstrak (atau *clone*) folder project ini ke dalam direktori web server kamu:
   - Jika menggunakan XAMPP: Masukkan ke folder `htdocs`.
   - Jika di Linux/Nginx/Apache: Masukkan ke `/var/www/html/obs` (seperti struktur folder ini).
2. Buka **OBS Studio**:
   - Pergi ke menu `Tools` -> `WebSocket Server Settings`.
   - Centang **Enable WebSocket server**.
   - Ingat atau ubah **Server Port** (Default: `4455`).
   - (Opsional) Centang **Enable Authentication** dan atur passwordnya untuk keamanan tambahan.
3. Pastikan OBS memiliki *Audio Mixer* dengan nama sumber `Desktop Audio` dan `Mic/Aux`. (Atau ubah nama inputnya di file `index.html` jika berbeda).
4. Untuk fitur **Ganti Teks**, pastikan kamu memiliki source teks di OBS bernama `TeksOverlay`.

## 📱 Cara Penggunaan

1. Buka browser di perangkat pengontrol (HP, tablet, dll). Pastikan perangkat tersebut terhubung di jaringan WiFi/LAN yang sama dengan komputer OBS.
2. Akses alamat lokal web server, contoh: `http://192.168.0.8/obs`
3. Masukkan **IP lokal** komputer yang menjalankan OBS (contoh: `192.168.0.8`).
4. Masukkan **Port** (bawaan: `4455`).
5. Masukkan **Password** (Kosongkan jika kamu menonaktifkan autentikasi di setting WebSocket OBS).
6. Sesuaikan **Nama Source Kamera** sesuai nama kameramu di OBS (contoh: `Video Capture Device` atau `Webcam`).
7. Klik **Konek**.

## 📁 Struktur File

- `index.html` — Antarmuka utama aplikasi dan seluruh logika WebSocket (JavaScript).
- `save-todo.php` — Script backend PHP untuk menangani penyimpanan *To-Do List*.
- `todo-data.json` — File database simpel berformat JSON (Otomatis dibuat/diperbarui oleh PHP).

---
*Dibuat untuk mempermudah operasional streaming/recording tanpa repot alt-tab ke OBS Studio.*
