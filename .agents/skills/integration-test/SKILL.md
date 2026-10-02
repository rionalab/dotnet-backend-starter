---
name: integration-test
description: Add or run integration tests for ASP.NET APIs and SQL Server stored procedures. Use when testing HTTP binding, middleware, authorization, repository mapping or database behavior; do not substitute mocks for real database verification.
---

# integration-test

1. Baca AGENTS.md, .agents/testing.md, kontrak serta implementasi yang ditargetkan.
2. Inspeksi framework/fixture test yang sudah dipakai; jangan install framework baru diam-diam.
3. Tetapkan acceptance scenarios dan boundary nyata: WebApplicationFactory atau host test untuk HTTP; SQL Server test terisolasi untuk SP.
4. Gunakan identity test yang jelas dan uji unauthorized/forbidden/ownership; jangan menonaktifkan authorization global agar test lulus.
5. Siapkan schema/SP dan data fixture deterministik; cleanup per test. Jangan gunakan kredensial atau database produksi.
6. Assert status, envelope/DTO, persistensi dan rollback sesuai kasus; bedakan test mock UseCase dari integration DB nyata.
7. Jalankan suite terarah, lalu checks wajib proyek. Jika runtime/DB tidak tersedia, tandai belum dijalankan beserta prerequisite; jangan menganggap skipped sebagai passed.
8. Laporkan hasil dan failure yang belum terselesaikan.
