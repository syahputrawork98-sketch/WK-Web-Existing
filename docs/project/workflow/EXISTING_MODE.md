# Existing Mode — WPWK

## Fungsi Dokumen
Dokumen ini digunakan saat WPWK diterapkan ke project yang sudah memiliki client/server atau codebase berjalan, tetapi dokumentasi, history, dan workflow kontrolnya belum rapi.

- WPWK tidak dipakai untuk menimpa project lama.
- WPWK dipakai sebagai documentation/control layer.
- Fokus awal adalah audit, mapping, dan dokumentasi.
- Client/server tidak boleh disentuh sebelum audit dan batch gate jelas.

## Kapan Digunakan
Gunakan panduan ini jika:
- project sudah memiliki client/
- project sudah memiliki server/
- project sudah memiliki package.json atau framework berjalan
- project sudah pernah deploy
- fitur utama sudah ada
- README/FEATURES/docs belum rapi
- project belum punya feature tracker
- project belum punya batch history
- user ingin mulai mengontrol project lama memakai cara kerja WPWK

## Greenfield vs Existing Project

| Aspek | Greenfield Project | Existing Project |
|---|---|---|
| Codebase | Belum ada / masih kosong | Sudah ada client/server |
| README | Dibuat dari awal | Diaudit dan diadaptasi |
| FEATURES | Dirancang dari awal | Direkonstruksi dari fitur nyata |
| client/server | Bisa dibuat dari template | Tidak boleh disentuh dulu |
| Batch awal | Project starter | Existing project audit |
| Risiko | Lebih rendah | Lebih tinggi karena ada sistem berjalan |

## Prinsip Utama Existing Adoption
- Jangan menyentuh client/server di batch awal.
- Jangan refactor hanya demi menyesuaikan WPWK.
- Jangan menghapus dokumentasi lama tanpa mapping.
- Jangan menimpa README/FEATURES sebelum isi lama dipahami.
- Jangan menganggap fitur existing otomatis Completed.
- Gunakan status Existing / Needs Review jika fitur sudah ada tapi belum divalidasi.
- Tambahkan `docs/project/` sebagai control layer.
- Build up dokumentasi pelan-pelan berdasarkan kondisi nyata project.

## Existing Project Adoption Flow
1. Adoption Pre-Scan
2. Existing Project Audit
3. Documentation Mapping
4. Feature Inventory
5. Risk Classification
6. WPWK Docs Injection
7. Feature Tracker Reconstruction
8. First Controlled Batch

## 1. Adoption Pre-Scan
Tahap ini hanya membaca struktur project.

Yang dicek:
- root files
- README lama
- FEATURES lama jika ada
- docs lama jika ada
- client location
- server location
- package.json
- framework
- env example
- deployment config
- database config
- scripts
- folder penting lain

Output:
Existing Project Pre-Scan Summary

## 2. Existing Project Audit
Audit menilai kondisi project tanpa mengubah file kode.

Existing Project Audit Summary

Project Name:
Repository:
Current Framework:
Frontend Location:
Backend Location:
Database:
Deployment:
Auth:
Existing Docs:
Main Features:
Known Risks:
Unknown Areas:
Recommended Adoption Mode:
Recommended First Batch:

## 3. Documentation Mapping
- README lama dipertahankan jika masih relevan.
- README boleh diadaptasi, bukan ditimpa total tanpa alasan.
- FEATURES lama dipetakan menjadi feature tracker.
- Docs lama bisa dipindahkan, dirangkum, atau direferensikan.
- Jika dokumen lama berantakan, buat mapping dulu sebelum rewrite.

## 4. Feature Inventory
Fitur existing harus didata berdasarkan kondisi nyata.

Existing Feature Inventory

| Feature ID | Feature Name | Area | Current Evidence | Suggested Status | Notes |
|---|---|---|---|---|---|

Contoh status:
- Existing / Stable
- Existing / Needs Review
- Partial
- Unknown
- HOLD
- Deprecated

- Jangan pakai Completed jika belum divalidasi.
- Completed hanya boleh dipakai jika sudah lolos validasi sesuai DoD.

## 5. Risk Classification
Low Risk:
- tambah docs/project/
- membuat CURRENT_STATUS.md
- membuat FEATURE_HISTORY.md
- membuat feature files
- merapikan docs tanpa menyentuh kode

Medium Risk:
- rewrite README
- rewrite FEATURES
- reorganisasi docs lama
- update env example
- mapping script/deployment docs

High Risk:
- mengubah client code
- mengubah server code
- mengubah database schema
- mengubah auth/security
- mengubah deployment/env
- delete/rename file/folder
- refactor besar

Aturan:
- Batch adoption awal harus Low Risk.
- High Risk wajib user confirmation dan review.

## 6. WPWK Docs Injection
Menambahkan struktur kontrol WPWK ke project existing.

Umumnya boleh dibuat:
- docs/project/
- docs/project/workflow/
- docs/history/
- docs/history/features/
- docs/project/onboarding/

Tetapi:
- Jangan mengubah client/server.
- Jangan install dependency.
- Jangan membuat config baru.
- Jangan menghapus docs lama.
- Jangan membuat fitur aplikasi baru.

## 7. Feature Tracker Reconstruction
Setelah audit, feature tracker dibuat berdasarkan fitur nyata.

Contoh:
| Feature Batch | Feature Name | Area | Status | Reason / HOLD Notes | Next Step | Detail File |
|---|---|---|---|---|---|---|
| F01 | Existing Client System | frontend/client | Existing / Needs Review | Client sudah ada tapi belum diaudit penuh | F01A — Client Structure Audit | features/F01_EXISTING_CLIENT_SYSTEM.md |
| F02 | Existing Server System | backend/server | Existing / Needs Review | Server sudah ada tapi belum diaudit penuh | F02A — Server Structure Audit | features/F02_EXISTING_SERVER_SYSTEM.md |

## 8. First Controlled Batch
Setelah adoption docs masuk, batch berikutnya harus audit terarah, bukan langsung refactor.

Contoh:
- F01A — Client Structure Audit
- F02A — Server Structure Audit
- F03A — Database Presence Audit
- F04A — Deployment Readiness Audit
- FXX-CP — Documentation Checkpoint

## Hal yang Tidak Boleh Dilakukan
- Jangan menimpa project existing dengan struktur WPWK secara paksa.
- Jangan menghapus README lama tanpa backup/mapping.
- Jangan mengubah client/server di batch dokumentasi adoption.
- Jangan install dependency.
- Jangan rename folder besar.
- Jangan mengubah database/auth/deployment tanpa batch khusus.
- Jangan menyebut fitur existing Completed tanpa validasi.
- Jangan menjadikan F00 sebagai fitur aplikasi.

## Existing Adoption Decision Template

Adoption Decision

Project Type:
Existing Project Condition:
Client Status:
Server Status:
Docs Status:
Recommended Adoption Mode:
Risk Level:
Need Roomchat 01 Review:
Need User Confirmation:
First Adoption Batch:
Notes:

## Existing Adoption Guardrails

Existing adoption harus dilakukan secara bertahap. WPWK tidak boleh dimasukkan ke project existing dengan cara full injection atau membuat banyak file sekaligus.

Prinsip:

* Existing project adoption harus progressive, bukan full injection.
* Batch pertama sebaiknya read-only audit.
* Jangan membuat banyak file WPWK sekaligus.
* Jangan menimpa README lama tanpa mapping.
* Jangan membuat folder `client/` atau `server/` jika project existing sudah memakai struktur lain seperti `apps/web`, `apps/api`, `frontend`, `backend`, atau struktur custom.
* Jangan membuat banyak feature files sebelum feature inventory disetujui Roomchat 00.
* Jangan mengubah kode, config, dependency, env, database, deployment, atau struktur folder pada adoption batch awal.
* Gunakan minimal control layer dulu.
* Jika user bilang “rapikan semua”, Roomchat 00 harus memecahnya menjadi audit → mapping → minimal docs → feature inventory → controlled expansion.
* Map first, move later.

## Progressive Adoption Levels

### Level 0 — Read-only Pre-Scan

Tujuan:

* Membaca struktur project existing.
* Tidak membuat file.
* Tidak mengubah file.
* Menghasilkan audit summary di chat atau laporan eksekutor.

Boleh:

* membaca root files
* membaca README
* membaca package.json
* membaca struktur client/server
* membaca docs lama

Tidak boleh:

* membuat file
* mengubah file
* install dependency
* rename/delete

### Level 1 — Minimal Control Layer

Tujuan:
Menambahkan lapisan kontrol paling kecil agar project mulai bisa dikendalikan dengan WPWK.

Boleh membuat maksimal 1 sampai 3 file, misalnya:

* docs/history/CURRENT_STATUS.md
* docs/history/FEATURE_HISTORY.md
* docs/history/features/F00_EXISTING_PROJECT_ADOPTION.md

Tidak boleh:

* membuat semua workflow template lengkap sekaligus
* membuat semua docs frontend/backend/database
* membuat banyak feature files
* mengubah client/server

### Level 2 — Documentation Mapping

Tujuan:
Memetakan dokumentasi lama sebelum dipindah, dirapikan, atau ditulis ulang.

Boleh:

* membuat mapping README lama
* membuat mapping docs lama
* membuat catatan keep/move/rewrite/archive

Tidak boleh:

* menghapus dokumentasi lama tanpa mapping
* rewrite README besar-besaran tanpa persetujuan
* memindahkan banyak file sekaligus

| Existing File | Current Purpose  | Action       | Notes                                |
| ------------- | ---------------- | ------------ | ------------------------------------ |
| README.md     | Cara run project | Keep / Adapt | Jangan timpa sebelum mapping         |
| docs/api.md   | Catatan API lama | Map          | Bisa dipetakan ke backend docs nanti |

### Level 3 — Feature Inventory

Tujuan:
Membuat daftar fitur existing berdasarkan kondisi nyata.

Boleh:

* membuat satu feature inventory
* memakai status Existing / Needs Review, Unknown, Partial, HOLD, Deprecated

Tidak boleh:

* membuat banyak feature files sebelum inventory disetujui
* menyebut fitur existing sebagai Completed tanpa validasi

Aturan:
Feature files detail baru boleh dibuat setelah feature inventory diterima oleh Roomchat 00.

### Level 4 — Controlled WPWK Expansion

Tujuan:
Mulai menambahkan dokumentasi teknis WPWK secara bertahap sesuai kebutuhan.

Boleh:

* docs/frontend jika frontend sudah dipetakan
* docs/backend jika backend sudah dipetakan
* docs/database jika database sudah dipetakan
* docs/deployment jika deployment sudah dipetakan

Tidak boleh:

* membuat semua area docs sekaligus tanpa alasan
* membuat file yang tidak dipakai project
* memaksa struktur WPWK ke struktur project existing

### Level 5 — Technical Batch

Tujuan:
Baru mulai menyentuh client/server/database/deployment.

Syarat:

* audit selesai
* feature inventory ada
* risiko diklasifikasikan
* batch gate jelas
* user confirmation jika menyentuh area sensitif
* Roomchat 01 review jika perlu

## Existing Adoption Batch Limit

Aturan:

* Adoption batch awal harus Small Batch.
* Level 0 tidak mengubah file.
* Level 1 maksimal 1 sampai 3 file.
* Jangan membuat lebih dari 3 file pada adoption batch awal tanpa alasan kuat dan persetujuan user.
* Jika Roomchat 00 merasa perlu membuat banyak file, pecah menjadi beberapa batch kecil.
* Untuk project existing, “rapikan semua docs” tidak boleh diterjemahkan sebagai satu batch besar.
* Satu batch adoption idealnya hanya punya satu tujuan: audit, mapping, minimal control layer, inventory, atau expansion.

## Anti-Blunder Rules for Existing Project

* Jangan full injection.
* Jangan langsung menyalin seluruh struktur WPWK ke project existing.
* Jangan menganggap project existing sebagai repo kosong.
* Jangan membuat `client/` dan `server/` baru jika project sudah punya struktur frontend/backend lain.
* Jangan menimpa README lama sebelum mapping.
* Jangan rewrite FEATURES lama sebelum feature inventory.
* Jangan membuat banyak feature files sebelum inventory disetujui.
* Jangan menyentuh kode sebelum adoption docs minimal selesai.
* Jangan menyebut fitur existing Completed tanpa validasi.
* Jangan refactor hanya demi menyesuaikan WPWK.
* Jangan membuat project lama terasa seperti harus diulang dari nol.

## Correct First Response Pattern for Roomchat 00

Jika user berkata:
“Project ini sudah jadi, tolong masukkan ke workflow WPWK.”

Roomchat 00 sebaiknya menjawab dengan pola:
“Karena ini existing project, saya tidak akan langsung membuat semua struktur WPWK. Saya akan mulai dari Level 0 — Read-only Pre-Scan untuk memahami struktur project dulu. Batch pertama tidak akan membuat atau mengubah file. Setelah audit, baru kita tentukan apakah masuk Level 1 Minimal Control Layer atau perlu mapping dokumentasi dulu.”

## Existing Project Adoption Decision Gate

Sebelum membuat instruksi ke Gemini, Roomchat 00 wajib menjawab:

* Ini Greenfield atau Existing Project?
* Apakah client/server sudah ada?
* Apakah struktur frontend/backend sudah berbeda dari `client/` dan `server/`?
* Apakah README lama masih penting?
* Apakah docs lama ada?
* Apakah fitur existing sudah jelas?
* Level adoption yang dipilih: 0 / 1 / 2 / 3 / 4 / 5
* Jumlah file yang boleh dibuat/diubah
* Apakah batch ini read-only?
* Apakah user confirmation diperlukan?

## Penutup
Existing project adoption bertujuan membuat project lama lebih mudah dikontrol, bukan mengulang project dari nol.
