# Greenfield Mode — WPWK

## Fungsi Dokumen
Dokumen ini digunakan saat WPWK diterapkan untuk membuat project yang benar-benar baru dari nol (tidak ada codebase sebelumnya).

## Karakteristik Greenfield Mode
- **Codebase**: Kosong. Akan diinisiasi di dalam folder `WK-Web-Greenfield/client/` dan `WK-Web-Greenfield/server/`.
- **README & FEATURES**: Dapat dibuat dari nol atau mengikuti template bebas yang telah disediakan.
- **Batch Awal**: Langsung masuk ke inisialisasi framework, instalasi dependensi, atau penyiapan arsitektur.
- **Risiko**: Relatif lebih rendah pada awal project, karena tidak ada sistem berjalan yang berpotensi rusak.

## Tahapan Greenfield Mode
1. **Pilih Template & Stack**: Diskusikan dengan Roomchat 00 terkait stack yang akan dipakai (misalnya Next.js untuk frontend, Express/NestJS untuk backend).
2. **Feature Batch Pertama (Project Foundation)**:
   - Menjalankan perintah inisiasi (misal `npx create-next-app`).
   - Setup Environment Variables (`.env.example`).
   - Menyiapkan arsitektur folder.
3. **Penyusunan Dokumentasi Dasar**:
   - Update `README.md` utama project.
   - Setup `CURRENT_STATUS.md` dan struktur dokumentasi awal di `docs/history/`.
4. **Development Reguler**:
   - Terus ikuti iterasi `FXX` untuk setiap fitur baru sesuai standar `WORKING_SYSTEM.md`.

## Aturan Keselamatan
Meskipun project dibangun dari awal:
- Tetap patuhi aturan Batch Gate System (validasi rencana di Roomchat sebelum eksekusi).
- Jangan menyimpan rahasia/credentials ke repository.
- Selalu pisahkan implementasi menjadi batch-batch kecil (Small/Medium Batch) untuk mempermudah review.
