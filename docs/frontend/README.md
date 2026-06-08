# Frontend Documentation

Folder ini akan berisi dokumentasi khusus terkait area frontend, mencakup arsitektur UI, state management, panduan gaya, dan komponen.

## Fungsi Dokumentasi Frontend
Dokumentasi ini berfungsi sebagai panduan arsitektur antarmuka dan batasan akses pengguna di sisi klien.

## Apa Saja yang Harus Dicatat?
Saat project mulai mengimplementasikan frontend, dokumentasi ini wajib memuat arsitektur routing, pembagian komponen utama, state management yang dipilih, serta daftar halaman berdasarkan hak akses.

## Aturan Pencatatan: Single Role Project
Jika project hanya memiliki satu jenis pengguna (misalnya: admin saja atau user publik saja), catat hal berikut:
- **Role utama**: Siapa pengguna sistem ini.
- **Public vs Protected Pages**: Halaman mana yang bisa diakses tanpa login dan mana yang wajib login.
- **Route/Page Utama**: Daftar halaman utama beserta path-nya (misal `/dashboard`).
- **Komponen Penting**: Komponen UI yang sering digunakan berulang.
- **State/Data yang Digunakan**: Data utama yang disimpan di sisi klien (misal: data user yang sedang login, keranjang belanja).

## Aturan Pencatatan: Multi Role Project
Jika project memiliki beberapa tingkat hak akses (misal: admin, manajer, kasir, pelanggan), catat:
- **Daftar Role**: Definisi peran yang ada.
- **Matrix Akses Halaman**: Tabel yang menunjukkan role mana yang bisa mengakses halaman tertentu.
- **Route Berdasarkan Role**: Struktur routing yang dilindungi oleh pengecekan hak akses.
- **Perbedaan UI Per Role**: Penjelasan jika ada tombol, menu, atau fitur yang disembunyikan/dimunculkan untuk role tertentu.
- **Halaman Protected**: Daftar rute yang diblokir bagi role yang tidak memiliki izin.
- **Risiko Akses Frontend**: Peringatan bahwa perlindungan di frontend hanya untuk UX, dan validasi sejati tetap harus dilakukan di backend.

## Template Ringkas
```markdown
### Arsitektur UI
- Framework: ...
- State Management: ...

### Routing & Akses (Single/Multi Role)
- `/login` (Public)
- `/dashboard` (Protected - Admin)
- `/profile` (Protected - User, Admin)
```
