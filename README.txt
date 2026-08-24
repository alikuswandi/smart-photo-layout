SMART PHOTO LAYOUT — Client-side Web App

Cara menjalankan:
1. Upload seluruh folder ke GitHub/Vercel/hosting statis, atau jalankan melalui localhost.
2. Buka index.html melalui HTTPS/localhost untuk kompatibilitas Background Removal AI terbaik.

Arsitektur:
- Editor, auto-layout, print preview dan render PDF berjalan di browser (tanpa backend).
- jsPDF dimuat dari CDN internet ketika aplikasi pertama kali dibuka.
- Background Removal AI memakai @imgly/background-removal yang berjalan langsung di browser. Library/model AI diunduh dari internet saat diperlukan pertama kali dan dapat dicache oleh browser.
- Foto tidak dikirim ke backend aplikasi.
- Project, antrean, pengaturan, edit foto dan hasil potongan AI disimpan melalui localStorage di browser/perangkat yang sama.

Catatan localStorage:
- Kapasitas localStorage berbeda antar browser dan biasanya terbatas. Jika project berisi banyak foto beresolusi besar, aplikasi akan menampilkan peringatan penyimpanan penuh.
- Project tersimpan hanya pada browser/perangkat dan origin/domain yang sama.

Catatan AI:
- Proses AI pertama kali membutuhkan internet untuk mengunduh library/model.
- Hasil terbaik didapat melalui HTTPS atau localhost.
- Library @imgly/background-removal memiliki lisensinya sendiri; periksa lisensi package sebelum penggunaan komersial/redistribusi.


v14 Login Akses Penuh:
- Tanpa login: editor/layout/preview aktif; Print dan Export PDF terkunci.
- Login default: admin / AditPrint2026
- Tombol WhatsApp dan Lynk.id tersedia di form login.
- Status login berlaku selama tab/sesi browser aktif.


v15 - Edit Antrean Independen:
- Setiap baris foto yang ditambahkan ke Antrean Cetak memiliki salinan edit tersendiri.
- Zoom, posisi X/Y, rotasi, preset warna, background warna, dan hasil AI pada satu item antrean tidak mengubah item antrean lain walaupun sumber filenya sama.
- Edit Foto dari Library menjadi dasar saat item baru dimasukkan ke antrean.
- Quantity dalam satu baris antrean tetap memakai edit yang sama untuk semua copy pada baris tersebut.


V17 FIREBASE LOGIN
- Supabase Auth diganti Firebase Authentication (Email/Password).
- Konfigurasi: firebase-config.js
- Panduan: FIREBASE_SETUP.txt
- Print dan Export PDF memerlukan user Firebase yang sedang login.

UPDATE v19 - GARIS POTONG GAP
- Opsi Garis Potong di Gap ON/OFF.
- Posisi garis otomatis tepat di tengah gap antar foto.
- Model: garis penuh, putus-putus, dan crop mark pendek.
- Ketebalan garis 0.1–2 mm (otomatis dibatasi agar tetap berada di area gap dan tidak menimpa foto).
- Warna hitam/abu-abu/abu muda + warna kustom.
- Garis tampil di preview, Print, PDF, PNG, dan JPG.
- Ditambahkan Export PNG dan Export JPG per halaman pada 300 DPI.
