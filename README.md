# Defect Tracker UT — CLS NDP Batam

Tracker defect hasil Uji Terima (UT) Gedung CLS NDP Batam, PT. Karsa Prabala.
Halaman statis di GitHub Pages, data tersimpan di Firebase Firestore sehingga semua anggota tim melihat dan mengisi data yang sama.

## Fitur
- Status per item: Open / In Progress / Closed, dengan tanggal mulai dan tanggal selesai
- Ringkasan outstanding dan rekap per PIC
- Ubah PIC, keterangan, dan tambah/hapus item langsung dari halaman
- Kolom PIC Karsa (penanggung jawab dari PT. Karsa Prabala)
- Dokumentasi foto Open dan Closed (maks. 4 foto per tahap, bisa langsung dari kamera HP); foto dikompres otomatis dan disimpan di Firestore, tanpa perlu paket Blaze
- Catatan siapa yang terakhir mengubah tiap item ("Nama pengisi" di kanan atas)
- Export PDF A4 landscape, lengkap dengan foto kecil dokumentasi (mengikuti saringan yang sedang aktif)
- Blok merah = Raised Floor (lingkup GSD), blok oranye = By Other

## Setup Firebase (sekali saja)
1. Buka https://console.firebase.google.com → **Add project** → beri nama, misalnya `defect-tracker-cls-ndp` (Google Analytics boleh dimatikan).
2. **Build → Firestore Database → Create database** → pilih lokasi `asia-southeast2 (Jakarta)` → **Start in production mode**.
3. Tab **Rules** di Firestore → hapus isinya, tempel isi file `firestore.rules` → **Publish**.
4. **Build → Authentication → Get started → Sign-in method → Anonymous → Enable → Save**.
5. **Project settings (ikon gerigi) → General → Your apps → ikon `</>` (Web)** → beri nama → **Register app**. Salin objek `firebaseConfig` yang muncul.
6. Tempel nilai-nilai tersebut ke file `config.js`.
7. **Authentication → Settings → Authorized domains → Add domain** → `dwikikrisnadi-coder.github.io`.

## Setup GitHub Pages
1. Repository → **Settings → Pages**.
2. Source: **Deploy from a branch**, Branch: `main`, folder `/ (root)` → **Save**.
3. Setelah 1–2 menit halaman aktif di `https://dwikikrisnadi-coder.github.io/defect-tracker-cls-ndp/`.

## Pertama kali dibuka
Database masih kosong, klik **Muat data defect terbaru** satu kali.

## Catatan keamanan
Siapa pun yang memegang link bisa membaca dan mengubah data. Bagikan link hanya ke tim proyek.
Nilai di `config.js` memang aman berada di repository publik; yang menjaga data adalah aturan di `firestore.rules`.
