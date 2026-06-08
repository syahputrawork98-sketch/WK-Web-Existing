# Existing Mode — WK

Dokumen ini menjelaskan logika kerja WK untuk project yang sudah memiliki aplikasi atau *codebase* berjalan. Inti dari mode ini adalah **Feature-First Existing Documentation**.

*(Catatan: Saat template ini diterapkan ke project asli, nama "WK-Web-Existing" pada repositori harus disesuaikan menjadi nama project asli Anda).*

## 1. Feature-First Existing Documentation

Pada project existing, AI **dilarang keras** langsung membuat aplikasi, melakukan *refactor*, atau mengubah frontend/backend/database. AI harus membaca aplikasi yang sudah ada, menemukan fitur-fiturnya, mencatat fitur tersebut, lalu baru menghubungkan setiap fitur ke frontend, backend, database, dan *development notes*.

Alur kerjanya adalah sebagai berikut:
`Existing App` → `Read-only scan` → `F00 — Existing Project Setup` → `Feature Discovery` → `FEATURE_HISTORY.md` → `docs/history/features/F01-FXX` → `Frontend / Backend / Database Relation Audit` → `Update CURRENT_STATUS.md` → `Baru masuk technical fix/development`

**PENTING**: Fitur adalah pusat dokumentasi. Frontend/backend/database hanyalah relasi teknis dari fitur tersebut.

## 2. Peran `CURRENT_STATUS.md`

`CURRENT_STATUS.md` berfungsi sebagai:
- Dashboard progress terakhir.
- Catatan *checkpoint*.
- Catatan AI terakhir mengerjakan sampai mana.
- Catatan phase aktif.
- Catatan fitur terakhir yang sedang dicek.
- Catatan *next step* agar AI tidak bingung saat pekerjaan dilanjutkan.

**Isi wajib `CURRENT_STATUS.md`**:
- Current Phase
- Last Checkpoint
- Last Worked Feature
- Current Progress
- Known Blockers
- Next Step

Dokumen ini **tidak boleh** menjadi tempat detail panjang semua fitur. Detail fitur harus diletakkan di file masing-masing di dalam folder `docs/history/features/`.

## 3. Peran `FEATURE_HISTORY.md`

`FEATURE_HISTORY.md` adalah *index* (daftar isi) dari semua fitur yang ada di project.
Dokumen ini harus mencatat matriks berikut:
- Feature ID
- Feature Name
- Type
- Status (Contoh: `Existing / Stable`, `Existing / Needs Review`, `Partial`, `Unknown`, `HOLD`, `Deprecated`)
- Frontend Relation Status
- Backend Relation Status
- Database Relation Status
- Detail File

**Aturan**: Jangan pernah menggunakan status `Completed` untuk fitur existing sebelum fitur tersebut benar-benar divalidasi.

## 4. Peran `docs/history/features/`

Setiap fitur yang ditemukan harus memiliki file detailnya sendiri di dalam folder ini (contoh: `F01_LANDING_PAGE.md`, `F02_AUTHENTICATION.md`).
Setiap file fitur harus menjadi pusat rangkuman fitur tersebut dengan struktur wajib sebagai berikut:

```markdown
# FXX — Feature Name

## Feature Summary
Penjelasan singkat fitur.

## Current Status
Status fitur.

## Feature Evidence
Bukti fitur ini ditemukan dari mana.

## Frontend Relation
File/folder frontend yang berhubungan dengan fitur ini.

## Backend Relation
File/folder backend/API yang berhubungan dengan fitur ini.

## Database Relation
Table/model/schema/database file yang berhubungan dengan fitur ini.

## Development Notes
Catatan install, script, env, dependency, atau local run jika relevan.

## Known Gaps
Bagian yang belum jelas, belum dicek, atau masih bermasalah.

## Checkpoint Notes
Catatan checkpoint untuk fitur ini.

## Next Step
Langkah berikutnya untuk fitur ini.
```

## 5. Peran F00 — Existing Project Setup

F00 bukanlah fitur aplikasi untuk user. F00 adalah *setup/adoption feature* untuk project existing.
Nama file yang direkomendasikan adalah `F00_EXISTING_PROJECT_SETUP.md`.

F00 harus menjawab pertanyaan: *“Aplikasi existing ini siap dibaca, dijalankan, dan diaudit atau belum?”*
Hal-hal yang dicatat dalam F00:
- Apakah project bisa diinstall atau belum?
- Package manager apa yang digunakan?
- Apakah script dev/build/lint/test tersedia?
- Apakah ada env example?
- Framework apa yang dipakai?
- Bagaimana struktur folder utamanya?
- Apakah cara run local sudah jelas?
- Apakah status awal project siap diaudit?

## 6. Urutan Kerja Setelah F00

Setelah F00 selesai, AI harus melakukan **Feature Discovery**.
Tujuannya adalah mencari fitur yang sudah ada dari:
- route/page, menu, form, dashboard, auth, admin area
- API endpoint, model/schema, database relation
- deployment/config jika relevan.

Setelah fitur ditemukan:
1. Masukkan ke `FEATURE_HISTORY.md`.
2. Buat detail file di `docs/history/features/`.
3. Isi status awalnya sebagai `Existing / Needs Review`, `Partial`, `Unknown`, `HOLD`, atau `Deprecated` (jangan langsung tulis `Completed`).

## 7. Relasi Fitur ke Frontend/Backend/Database

Setiap file fitur (F01, F02, dst.) harus menyambungkan fitur konseptual ke wujud teknisnya.
Contoh:

**F01 — Landing Page**
- Frontend Relation: `app/page.tsx`, `components/HeroSection.tsx`
- Backend Relation: Not Required / Unknown
- Database Relation: Not Required / Unknown

**F02 — Authentication**
- Frontend Relation: login page, auth form
- Backend Relation: auth route/API/middleware
- Database Relation: user table/model/session/token

## 8. Syarat Development Baru

*Technical fix* atau *development* baru baru boleh dilakukan SETELAH:
- F00 sudah ada.
- `FEATURE_HISTORY.md` sudah berisi daftar fitur.
- File detail fitur sudah dibuat untuk fitur utama.
- Relasi frontend/backend/database sudah mulai dipetakan.
- `CURRENT_STATUS.md` menunjukkan checkpoint terakhir.
- User menyetujui batch perbaikan.

**Larangan Eksekusi**:
- Jangan langsung *refactor* project existing.
- Jangan langsung membuat ulang frontend/backend/database.
- Jangan membuat folder `client/` atau `server/` baru jika project existing sudah memakai struktur lain (seperti `apps/web`, `src`, `frontend`, dll).
- Jangan menyebut fitur existing `Completed` sebelum validasi.
- Jangan membuat banyak file feature sebelum *feature inventory* jelas.
- Jangan menghapus README/docs lama tanpa *mapping*.
- Jangan meng-install dependensi.
- Jangan melakukan *commit/push*.

## 9. Model Execution Policy

Default model untuk eksekusi AI (Gemini) di lingkungan ini adalah:
- **Gemini 3.1 Pro low**
- **Gemini 3.1 Pro high**

**Aturan Pemakaian**:
- **Gemini 3.1 Pro low**: Digunakan untuk batch ringan, dokumentasi kecil, review sederhana, update status, dan perubahan *low-risk*.
- **Gemini 3.1 Pro high**: Digunakan untuk audit lebih dalam, analisis fitur, mapping frontend/backend/database, *refactor planning*, atau batch yang membutuhkan reasoning lebih kuat.

Roomchat 00 harus memahami kapan menggunakan model yang tepat dan merekomendasikannya kepada User. Namun, keputusan akhir model tetap mengikuti User.

*(Model alternatif opsional jika User meminta percepatan: Claude Sonnet 4.6 thinking, Claude Opus 4.6 thinking, GPTOS 120B medium, Gemini 3.5 Flash low/medium/high).*
