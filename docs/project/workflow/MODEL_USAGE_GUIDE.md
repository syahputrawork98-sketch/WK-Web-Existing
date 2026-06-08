# Model Usage Guide

Panduan penggunaan model AI dalam eksekusi di Anti-Gravity IDE.

- **Gemini 3.1 Pro Low**: Gunakan untuk small batch, perubahan teks/dokumentasi sederhana, atau refactoring minor.
- **Gemini 3.1 Pro High**: Gunakan untuk medium/high-risk batch, pembuatan fitur baru, setup arsitektur, atau integrasi kompleks.
- **Large Batch**: Jika tugas termasuk large batch, model apa pun wajib menolak atau meminta user memecah tugas tersebut.
- **Alternative Acceleration Model**: Gunakan hanya jika user secara eksplisit meminta percepatan atau model alternatif (misal untuk tugas repetitif spesifik).
- **Pengambilan Keputusan**: Model **tidak boleh** menggantikan keputusan User. Jika ada ambiguitas, model harus bertanya atau memberikan opsi.
- **Larangan Git**: Gemini (model apa pun) dilarang melakukan `git commit` dan `git push`.
