# Database Documentation

Folder ini akan berisi dokumentasi khusus terkait database, mencakup skema (schema), strategi migrasi, ERD, dan query penting.

## Fungsi Dokumentasi Database
Sebagai panduan struktur penyimpanan data, relasi antar entitas, dan kepemilikan data.

## Apa Saja yang Harus Dicatat?
Saat project mulai mendesain database, dokumentasi wajib memuat daftar tabel utama, relasinya, dan field yang mengontrol kepemilikan atau izin akses.

## Aturan Pencatatan: Single Role Project
- **Tabel Utama**: Tabel-tabel esensial untuk bisnis logic.
- **Field Penting**: Kolom krusial yang perlu diperhatikan tipe datanya.
- **Relasi Dasar**: Bagaimana tabel-tabel utama saling terhubung (1-N, M-N).
- **Ownership Data**: (Jika ada) bagaimana data dikaitkan dengan user tertentu.

## Aturan Pencatatan: Multi Role Project
- **Users Table**: Struktur tabel yang menyimpan informasi dasar akun.
- **Roles Table**: Struktur tabel jenis peran (jika terpisah dari tabel user).
- **Permissions Table**: (Jika diperlukan) skema RBAC detail untuk izin spesifik.
- **Relasi User-Role**: Bagaimana user dihubungkan ke rolenya.
- **Ownership Field**: Kolom penting seperti `user_id`, `owner_id`, `created_by`, `updated_by` untuk membatasi akses edit/hapus.
- **Data Access Rule Per Role**: Penjelasan tabel mana saja yang bisa diakses secara global vs terbatas sesuai kepemilikan.
- **RBAC Sederhana vs Permission Detail**: Penjelasan sistem perizinan yang dipilih.

## Template Ringkas
```markdown
### Tabel Utama
- `users`: Data autentikasi
- `products`: Data produk utama (`created_by` mengarah ke `users.id`)

### Relasi Multi Role
- `users.role` ENUM('admin', 'user')
- Data akses: User hanya boleh melihat `products` milik mereka sendiri, Admin bisa melihat semua.
```
