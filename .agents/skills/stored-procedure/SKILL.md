---
name: stored-procedure
description: Create, repair or optimize SQL Server stored procedures used by Dapper repositories, including paging and atomic writes. Use for SP, schema/query or repository-to-SP mapping tasks.
---

# stored-procedure

1. Baca AGENTS.md, .agents/database.md, docs/SECURITY.md dan schema/SP/repository terkait.
2. Tetapkan parameter tipe/ukuran, nullability, output/result set, affected rows dan error semantics. Jangan menebak schema.
3. Buat script berversi di database/ sesuai pola proyek; gunakan CREATE OR ALTER bila target mendukungnya, SET NOCOUNT ON dan kolom eksplisit.
4. Parameterize nilai; allowlist identifier untuk sort. Periksa dynamic SQL di dalam SP.
5. Tentukan batas transaksi dan audit. Untuk transaksi di SP, gunakan TRY/CATCH, XACT_ABORT dan rollback sesuai ownership transaksi. Hindari merusak transaksi milik caller.
6. Sesuaikan Dapper mapping memakai CommandType.StoredProcedure dan CommandDefinition dengan token; jangan gunakan SQL inline.
7. Verifikasi pada database test terisolasi: sukses, konflik, paging dan atomicity sesuai perubahan. Gunakan data deterministik, cleanup serta parameter/result metadata.
8. Laporkan script, kebutuhan deploy, risiko kompatibilitas dan verifikasi yang tidak tersedia; jangan menjalankan perubahan live tanpa otorisasi.
