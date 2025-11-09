# Projek_OS-Galuh2

# Tugas Proyek : Langkah Implementasi
Langkah 2 - Struktur Proyek

# Gambar : https://drive.google.com/file/d/1UA1Ct3fh6N4K-2QTg9rs_lMBChir4-nv/view?usp=sharing

# Penjelasan Perintah

1. pwd
   - Perintah ini digunakan untuk menampilkan direktori kerja saat ini (Print Working Directory).
   - Output:
   ```
   /home/hozz yang menandakan user sedang berada di direktori home bernama "hozz".

2. ls
   - Perintah untuk menampilkan daftar file dan folder di dalam direktori saat ini.
   - Output menampilkan beberapa direktori seperti Desktop, Documents, Downloads, Music, Pictures, Public, snap, Templates, Videos.

3. sudo apt-get update
   - Perintah ini digunakan untuk memperbarui daftar paket dari repository yang sudah dikonfigurasi pada sistem Ubuntu.
   - sudo digunakan agar perintah dijalankan dengan hak akses administrator (root).
   - Setelah memasukkan password, sistem mulai mencari dan mengunduh file daftar paket baru dari server Ubuntu.
   - Proses ini mengambil metadata dan informasi terbaru dari berbagai sumber software repository Ubuntu.
   - Terdapat beberapa output Get, Hit, dan beberapa error seperti "No such file or directory" yang menandakan ada sumber repo dari CD-ROM yang tidak ditemukan.
   - Walaupun ada error, proses tetap berjalan dan berhasil mengakses repository online Ubuntu.

Fungsi Umum Perintah di Atas:

- pwd: Fungsinya yaitu memastikan di direktori mana user berada.
- ls: Fungsinya yaitu melihat isi folder saat ini.
- sudo apt-get update: Fungsinya yaitu mengupdate daftar paket supaya sistem tahu versi terbaru perangkat lunak yang tersedia untuk diinstall/upgrade.

# Gambar : https://drive.google.com/file/d/1HXG-XOPdig9WQ57Bpp5VSKSRCXqA6r2-/view?usp=sharing

# Detail Perintah dan Output

1. Update Repository
   - Perintah:
       ```
     sudo apt-get update
     
   - Fungsi:
     - Memperbarui daftar paket dari repository, memperbaharui metadata paket.
   - Output/Error:
     - Pesan error terkait repository CD-ROM:
       ```
       E: The repository 'file:/cdrom noble Release' no longer has a Release file.
         ```
       Ini menunjukkan repository dari CD-ROM tidak lagi valid atau tidak ditemukan, jadi diabaikan.
     - Pesan notifikasi:
         ```
       N: Updating from such a repository can't be done securely, and is therefore disabled by default.
         ```
       Ini menandakan repository dari CD-ROM tidak digunakan karena tidak aman.
   
2. Install Paket tree
   - Beberapa percobaan install tree dilakukan:
       ```
     sudo apt install tree
     
   - Masalah:
      ``` 
     E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
       ```
     Menandakan adanya proses pengelolaan paket (dpkg) sebelumnya yang terganggu atau tidak selesai, sehingga perlu diperbaiki dulu.
   
3. Alternatif Instalasi tree
   - Ketika menjalankan perintah tree langsung:
     ```
     tree
       ```
     Muncul pesan:
       ```
     Command 'tree' not found, but can be installed with:
       sudo snap install tree
       sudo apt install tree
       ```
     Menunjukkan tree belum terpasang, dan user disarankan menginstall dengan snap atau apt.
   
4. Kesalahan Izin dan Lock File
   - Percobaan install tanpa sudo:
       ```
     apt install tree
     Error:
     E: Could not open lock file /var/lib/dpkg/lock-frontend - open (13: Permission denied)
       ```
     Menyatakan user tidak punya izin (bukan root), harus dengan sudo.
   
5. Saran Perbaikan
   - Sistem memberikan instruksi untuk memperbaiki masalah:
       ```
     sudo dpkg --configure -a
       ```
     Untuk menyelesaikan konfigurasi paket yang tertunda atau rusak.
   
6. Percobaan Update Ulang
   - User mencoba ulang:
       ```
     sudo apt-get update
       ```
     Tampil kembali pesan error repository CD-ROM yang sama.

# Gambar : https://drive.google.com/file/d/1M4QIY2m68PuJ1Z_FoCFObM0h9YM0rtUx/view?usp=sharing

# Penjelasan Isi Terminal

1. Perintah sudo apt-get update dijalankan dua kali
   - Fungsi: Memperbarui daftar paket dari repository yang sudah dikonfigurasi.
   - Sumber repo *file:/cdrom noble* mengalami error:
     ```
     Err:2 file:/cdrom noble Release
     File not found - /cdrom/dists/noble/Release (2: No such file or directory)
      ```
     - Ini berarti file Release untuk repository dari CD-ROM tidak ditemukan.
     - Repository ini sudah tidak valid sehingga mendapat peringatan:
        ```
       E: The repository 'file:/cdrom noble Release' no longer has a Release file.
       N: Updating from such a repository can't be done securely, and is therefore disabled by default.
       
   - Repository online lain (http://id.archive.ubuntu.com/ubuntu dan http://security.ubuntu.com/ubuntu) dapat diakses dan di-"Hit", berarti berhasil mengambil data paket.

2. Perintah sudo apt install tree
   - Mencoba memasang paket tree.
   - Error:
      ```
     E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
      ```
     - Menandakan ada proses pengaturan paket dpkg yang belum selesai dan harus diperbaiki terlebih dahulu.

3. Perintah sudo dpkg --configure -a
   - Menjalankan perintah untuk menyelesaikan konfigurasi paket yang terganggu.
   - Output:
      ```
     Setting up cups (2.4.7-1.2ubuntu7.4) ...
     Updating PPD files for cups ...
     Updating PPD files for cups-filters ...
     
   - Ini menunjukkan sistem sedang menyelesaikan konfigurasi paket CUPS (Common UNIX Printing System).

# Gambar : https://drive.google.com/file/d/1wP67ASF2lOZEggK5AZRsZsmv-6DyREU9/view?usp=sharing

1. Proses Pemutakhiran File PPD Printer
   - Baris awal menampilkan proses update file PPD (PostScript Printer Description) untuk berbagai printer seperti postscript-hp, ptouch, pxljr, sag-gdi, splix.
   - Proses ini merupakan bagian dari konfigurasi sistem printing di Ubuntu.

2. Processing Triggers
   - Setelah update file PPD selesai, ada serangkaian "processing triggers" untuk berbagai paket dan layanan:
     - libc-bin, ufw (firewall), systemd, man-db, dbus, desktop-file-utils, hicolor-icon-theme, dan gnome-menus.
   - "Processing triggers" artinya sistem sedang melakukan tindakan yang diperlukan untuk memperbaharui konfigurasi dan database setelah instalasi atau update paket.

3. Perintah Instalasi tree
   - Perintah:
       ```
     sudo apt install tree
      ```
              
   # Fungsi: Menginstal paket tree pada sistem
   - Output Proses Instalasi:
     - Membaca daftar paket dan membangun dependency tree berhasil tanpa masalah.
     - Paket baru yang akan diinstal: tree.
     - Paket ini berukuran 47.1 kB, setelah instalasi memerlukan 111 kB ruang disk tambahan.
     - Mengunduh paket dari repository Ubuntu (http://id.archive.ubuntu.com/ubuntu).
     - Memilih dan menyiapkan paket tree yang sebelumnya belum terinstal.
     - Mengekstrak dan mengatur instalasi paket.
     - Memproses trigger untuk pembaruan database manual (man-db).

4. Perintah tree
   - Setelah instalasi selesai, user menjalankan perintah:
       ```
     tree
       ```
# Gambar : https://drive.google.com/file/d/1cxkCC1Bu7tB1Ud1wTu__IbyrESl3WuXH/view?usp=sharing

1. Instalasi Paket tree
   - Proses instalasi paket tree berhasil:
     - Sistem membaca database paket yang terpasang.
     - Menyiapkan file instalasi dan mengekstrak paket tree.
     - Mengatur (setting up) paket tree versi 2.1.1-2ubuntu3.
     - Memproses trigger untuk pembaruan manual database (man-db).
   
2. Menjalankan Perintah tree
   - Perintah tree dieksekusi untuk menampilkan struktur direktori dari direktori home user (hozz).
   - Output menunjukkan struktur folder:
     - Folder utama: Desktop, Documents, Downloads, Music, Pictures, Public, snap, Templates, Videos.
     - Di dalam folder snap terdapat subfolder snapd-desktop-integration.
     - Di dalam snapd-desktop-integration, terdapat folder 315 yang berisi direktori standar Desktop, Documents, Downloads, Music, Pictures, Public, Templates, Videos.
     - Ada folder common dan symbolic link current -> 315.
   
3. Membuat Direktori Baru
   - Perintah:
    ```
     mkdir project_sistem_operasi_b
    ```
   - Membuat folder baru bernama project_sistem_operasi_b di direktori kerja saat ini.

4. Berpindah Direktori
   - Perintah:
       ```
     cd project_sistem_operasi_b
     
   - Berpindah masuk ke dalam folder project_sistem_operasi_b yang baru dibuat.

# Gambar : https://drive.google.com/file/d/1gDsStTWgh4GRwmRQ9K__5g1WZCGSLQB4/view?usp=sharing


1. Membuat Direktori Baru project_sistem_operasi_b
   - Perintah:
      ```
     mkdir project_sistem_operasi_b
     
   - Fungsi: Membuat folder baru dengan nama project_sistem_operasi_b.
   
2. Masuk ke Direktori project_sistem_operasi_b
   - Perintah:
      ```
     cd project_sistem_operasi_b
     
   - Fungsi: Berpindah ke folder project_sistem_operasi_b yang baru dibuat.

3. Membuat Subdirektori src, doc, dan data
   - Perintah:
      ```
     mkdir src doc data
     
   - Fungsi: Membuat tiga folder baru di dalam project_sistem_operasi_b yaitu src, doc, dan data sebagai struktur dasar proyek.

4. Membuat File readme.md dan src/main.sh
   - Perintah:
      ```
     touch readme.md src/main.sh
     
   - Fungsi: 
     - Membuat file kosong readme.md di direktori utama proyek.
     - Membuat file kosong main.sh di dalam folder src.

5. *Menampilkan Struktur Direktori Menggunakan tree*
   - Perintah:
    ```
     tree
     
   - Output:
     
     .
     ├── data
     ├── doc
     ├── readme.md
     └── src
         └── main.sh
      ```
   - Fungsi: Menampilkan struktur visual folder dan file di dalam direktori kerja saat ini.
 
6. *Melihat Ukuran Folder (du -h --max-depth=1)*
   - Perintah:
      ```
     du -h --max-depth=1
     
   - Fungsi: Menampilkan ukuran masing-masing subdirektori langsung di dalam folder saat ini (maksimal kedalaman 1).
   - Output:
      ```
     4.0K    ./src
     4.0K    ./doc
     4.0K    ./data
     16K     .
     
   - Interpretasi:
     - Setiap subfolder berukuran sekitar 4KB.
     - Total keseluruhan folder (.) berukuran 16KB.

7. *Melihat Ukuran Total Folder (du -sh)*
   - Perintah:
      ```
     du -sh
     
   - Fungsi: Menampilkan ukuran total dari folder saat ini dengan format ringkas dan mudah dibaca.
   - Output: 16K, sama seperti penjumlahan dari ketiga subfolder dan file yang ada.

