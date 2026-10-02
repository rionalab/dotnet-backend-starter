# Menggunakan Starter

Starter ini berisi setup AI, belum merupakan aplikasi .NET yang bisa dijalankan.

1. Gunakan repository ini sebagai sumber template untuk repo proyek baru; jangan membawa history atau domain proyek lama jika tidak diperlukan.
2. Salin docs/PRODUCT.template.md menjadi docs/PRODUCT.md dan isi kebutuhan produk.
3. Sesuaikan docs/ARCHITECTURE.md, terutama validator dan authentication. Catat keputusan besar di docs/adr/.
4. Jalankan Codex dari root repository. AGENTS.md mengarahkan pembacaan aturan dan panduan peran.
5. Skill repository berada di .agents/skills/{name}/SKILL.md. Ini mengikuti lokasi discovery repository pada dokumentasi resmi: https://learn.chatgpt.com/docs/build-skills. Struktur .codex/skills pada diskusi awal diganti agar mengikuti lokasi tersebut.
6. File .agents/backend.md, database.md, security.md, testing.md adalah panduan peran, tidak otomatis membuat agent terpisah.
7. Minta bootstrap runtime .NET 10 sesuai architecture, lalu implementasikan feature pertama setelah acceptance criteria dan kontrak jelas.

## Contoh permintaan
- Baca AGENTS.md, bootstrap API .NET 10 berdasarkan docs/ARCHITECTURE.md; verifikasi package, SDK dan build.
- Gunakan $backend-feature untuk implementasi feature sesuai PRODUCT.md dan acceptance criteria berikut ...
- Gunakan $stored-procedure untuk membuat SP paging sesuai schema berikut ...
- Gunakan $integration-test untuk memverifikasi endpoint ... termasuk forbidden dan konflik.

Dalam lingkungan yang tidak menampilkan skills repository, minta AI membaca path SKILL.md secara eksplisit. Repo-scoped skills ini tidak otomatis menjadi personal skills di semua percakapan ChatGPT.

## Update standar
Copy template menghasilkan snapshot. Update starter tidak otomatis memperbarui repo turunan; review diff dan terapkan perubahan yang relevan.
