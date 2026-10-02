# Backend AI Instructions

## Mulai bekerja
Baca docs/PRODUCT.md jika sudah dibuat; jika belum, gunakan docs/PRODUCT.template.md hanya sebagai daftar pertanyaan, bukan fakta bisnis. Baca docs/ARCHITECTURE.md dan docs/CODING-STANDARDS.md. Muat dokumen lain sesuai tugas.
Instruksi pengguna yang eksplisit mengungguli default starter. Catat perubahan keputusan yang berdampak di ADR. Jangan mengarang domain, schema, permissions, integrasi, atau hasil pengujian.

## Default teknik
.NET 10 Web API dengan Controllers, Vertical Slice, pragmatic Clean dan DDD ringan. SQL Server melalui Dapper dan stored procedure saja. UseCase langsung tanpa MediatR; jangan tambahkan EF Core.
CancellationToken untuk I/O. Endpoint lowercase dan plural. ApiResponse<T> konsisten. Komentar C# memakai /* ... */, bukan XML summary.
Pilihan validator belum dikunci: ikuti docs/ARCHITECTURE.md dan keputusan proyek.

## Routing tugas
- Feature backend: .agents/backend.md dan .agents/skills/backend-feature/SKILL.md.
- Endpoint atau kontrak: docs/API-CONTRACT.md dan .agents/skills/api-endpoint/SKILL.md.
- Database: .agents/database.md dan .agents/skills/stored-procedure/SKILL.md.
- Pengujian: .agents/testing.md dan .agents/skills/integration-test/SKILL.md.
- Authentication, authorization, atau review keamanan: .agents/security.md dan docs/SECURITY.md.

File peran .agents/*.md adalah panduan yang dibaca atas arahan ini, bukan konfigurasi otomatis subagent. Jangan menjalankan delegasi hanya karena file peran tersedia.

## Workflow
Inspeksi pola dan perubahan lokal sebelum mengedit. Selesaikan perubahan yang diminta secara vertikal. Batasi refactor pada yang diperlukan. Update kontrak bila perilaku berubah.
Jalankan pemeriksaan yang sesuai dan laporkan yang lulus, gagal, atau tidak dapat dijalankan beserta alasannya. Jangan mengklaim starter ini sebagai API siap produksi.
Jangan commit secrets, data pelanggan, atau kredensial. Jangan mengubah database produksi atau deploy tanpa otorisasi pengguna.
