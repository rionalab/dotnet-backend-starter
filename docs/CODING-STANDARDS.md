# Coding Standards

- C# file, class, record dan public member: PascalCase; local/parameter: camelCase; private field: _camelCase.
- Interface: I prefix. Metode asynchronous: Async suffix; UseCase: ExecuteAsync.
- Feature dan operation memakai nama bisnis, bukan folder generik Helpers yang menampung semuanya.
- Gunakan nullable reference types, DI constructor, async/await dan CancellationToken pada semua I/O.
- Hindari .Result, .Wait(), async void, service locator dan static mutable state.
- Komentar memakai /* ... */ ketika membantu menjelaskan alasan. Hindari XML summary dan komentar yang mengulang kode.
- Request/response DTO terpisah dari entity. Jangan mengembalikan DataTable atau entity persistence langsung.
- Centralize pesan melalui AppMessages; pertahankan HTTP status yang sesuai.
- Validasi input di batas aplikasi; invariant bisnis tetap ditegakkan dalam domain/UseCase.
- Tangkap exception hanya bila dapat ditangani; middleware menangani exception tak terduga dan mencatat trace ID.
- Jangan log password, token, cookie, isi dokumen privat, atau connection string.
- Gunakan konfigurasi bertipe dan validasi konfigurasi penting saat startup.
- Jangan gunakan SQL inline, EF Core atau MediatR. Stored procedure wajib tetap aman terhadap injection.
- Jangan menambahkan generic repository atau abstraction tanpa kebutuhan berulang.
- Sertakan path file ketika menjelaskan potongan kode kepada pengguna.
- Pilih test yang memverifikasi perilaku; jangan menambah test yang hanya menyalin implementasi.
