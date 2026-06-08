# Backend Documentation

Folder ini akan berisi dokumentasi khusus terkait area backend, mencakup desain API, arsitektur server, integrasi layanan pihak ketiga, dan keamanan.

## Fungsi Dokumentasi Backend
Sebagai panduan utama untuk struktur endpoint, autentikasi, serta aturan bisnis logic dan perizinan.

## Apa Saja yang Harus Dicatat?
Saat project mulai mengimplementasikan backend/API, dokumentasi wajib mencatat daftar endpoint, metode HTTP, skema payload/response, serta mekanisme pengamanan data.

## Aturan Pencatatan: Single Role Project
- **Endpoint Utama**: Daftar endpoint penting (misal `/api/users`, `/api/products`).
- **Public vs Protected Endpoint**: Endpoint mana yang terbuka dan mana yang butuh token/sesi.
- **Middleware/Auth**: Mekanisme autentikasi yang digunakan (misal JWT, Session).
- **Request/Response Penting**: Struktur data yang dikirim dan diterima.
- **Business Logic Utama**: Aturan khusus yang diproses di server (misal: kalkulasi diskon).

## Aturan Pencatatan: Multi Role Project
- **Endpoint Berdasarkan Role**: Pengelompokan endpoint sesuai role yang diizinkan.
- **Permission Matrix Endpoint**: Tabel detail endpoint, aksi (GET/POST), dan role yang memiliki akses.
- **Middleware Role Checking**: Penjelasan cara backend memblokir akses dari role yang tidak berhak.
- **Batasan Akses Data**: Aturan agar user hanya bisa mengakses datanya sendiri meskipun punya role yang sama.
- **Risiko Keamanan Backend**: Peringatan bahwa backend adalah gerbang pertahanan terakhir yang harus memvalidasi setiap payload.

## Template Ringkas
```markdown
### API Endpoints
- `POST /api/auth/login` (Public)
- `GET /api/users/me` (Protected - All Roles)
- `DELETE /api/products/:id` (Protected - Admin Only)

### Auth & Middleware
- Strategy: ...
- Role Checking Middleware: ...
```
