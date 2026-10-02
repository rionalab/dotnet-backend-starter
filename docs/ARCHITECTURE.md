# Architecture

## Default dan batas
Target .NET 10, Controllers, modular monolith awal, feature-based Vertical Slice. Ini standar starter; belum ada kode runtime atau paket terpasang.
Pisahkan microservice hanya jika ada kebutuhan batas domain, ownership, scaling, atau deployment yang nyata. Jangan membuat layanan baru otomatis.

## Struktur kode saat implementasi
- src/Backend.Api/Features/{Feature}/{Operation}/: request, response, validator bila dipakai, UseCase.
- src/Backend.Api/Features/{Feature}/: controller, domain entities/value objects dan repository abstraction milik feature.
- src/Backend.Api/Infrastructure/: implementasi repository Dapper, connection factory, integrasi eksternal.
- src/Backend.Api/Common/: ApiResponse, AppMessages, exception middleware dan utilitas lintas feature yang benar-benar diperlukan.
- database/: schema dan stored procedure berversi.
- tests/Backend.UnitTests/ dan tests/Backend.IntegrationTests/.

Mulai satu proyek API; folder tidak harus menjadi assembly. Domain tidak bergantung pada ASP.NET, Dapper, atau SQL client. UseCase bergantung pada abstraction repository; Infrastructure mengimplementasikannya. Controller memanggil UseCase; Program.cs menjadi composition root. Jangan memanggil satu controller dari controller lain.

## Alur
Controller → validation → UseCase → domain bila diperlukan → repository abstraction → Dapper/SP.
Gunakan domain behavior untuk invariant bisnis yang nyata; jangan membuat aggregate kosong untuk CRUD sederhana.
Gunakan ExecuteAsync pada UseCase. Tanpa MediatR dan EF Core. Dapper memakai parameter dan CommandType.StoredProcedure; token diteruskan melalui CommandDefinition.

## Keputusan terbuka
- Validator: pilih validasi eksplisit atau FluentValidation ketika bootstrap runtime; jangan memasang library diam-diam.
- Authentication: tentukan identity provider serta bearer/cookie melalui ADR; jangan menyediakan token palsu atau bypass.
- API versioning: konvensi /api/v1 siap; library dan kebijakan migrasi dipilih saat dibutuhkan.
- Logging, audit table, SignalR, caching, OpenAPI client generation: implementasikan berdasarkan kebutuhan proyek, belum tersedia dalam starter.
- Paket dan SDK: verifikasi kompatibilitas serta pin versi saat implementasi runtime.

## Transaksi dan performa
Tentukan batas transaksi per UseCase, gunakan connection/transaction yang sama untuk operasi atomik. Simpan audit perubahan atomik bila dibutuhkan. Hindari repository yang membuka transaksi terpisah untuk tiap langkah.
Pagination server-side dengan batas ukuran; hindari mengambil BLOB pada list. Pilih kolom eksplisit. Jangan cache data privat tanpa scope dan invalidation yang jelas.
