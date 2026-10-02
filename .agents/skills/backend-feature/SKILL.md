---
name: backend-feature
description: Implement backend features in .NET APIs using Vertical Slice, direct UseCases and Dapper stored procedures. Use for new business operations or changes spanning validation, domain and persistence.
---

# backend-feature

1. Baca AGENTS.md, architecture, coding standards dan PRODUCT.md bila tersedia.
2. Identifikasi acceptance criteria, permissions, status/transisi serta schema/SP terkait. Tanyakan hanya fakta bisnis yang menghalangi implementasi; lanjutkan inspeksi independen.
3. Baca docs/API-CONTRACT.md dan .agents/backend.md. Tetapkan request/response dan error sebelum kode.
4. Buat atau ubah operation di Features/{Feature}/{Operation}; gunakan validator yang sudah dipilih proyek, UseCase ExecuteAsync dan domain behavior bila dibutuhkan.
5. Tambahkan repository abstraction milik feature serta implementasi Infrastructure. Bila SP berubah, gunakan stored-procedure skill; teruskan token dan transaksi.
6. Tambahkan controller endpoint tipis dan policy authorization; jangan percaya actor/tenant dari client.
7. Update DI, kontrak dan test perilaku yang relevan; jalankan build/test yang tersedia.
8. Laporkan file/perilaku yang berubah, verifikasi, dan batas yang belum dapat diperiksa. Jangan mengklaim test berjalan tanpa output.
