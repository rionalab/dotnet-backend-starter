# Security

Dokumen ini adalah persyaratan review, bukan klaim keamanan yang sudah diimplementasikan.

- Authentication: validasi issuer, audience, signature dan expiry untuk bearer; konfigurasi cookie Secure, HttpOnly, SameSite sesuai alur bila cookie dipilih.
- Authorization: deny by default, policy-based melalui [Authorize(Policy = "...")]; [AllowAnonymous] hanya eksplisit. Periksa ownership/tenant setiap akses objek; UI tidak menjadi batas keamanan.
- Input: batas panjang, payload/file, paging dan format; validasi bisnis di server.
- SQL: parameter SP melalui Dapper; dynamic SQL di dalam SP tetap wajib parameterized. Allowlist sort identifiers. Gunakan akun database least privilege.
- Rate limit: partition sesuai user/IP yang dipercaya, khususnya login dan operasi mahal; tentukan kebijakan serta respons 429.
- CORS: allowlist origin; jangan wildcard origin dengan credentials.
- CSRF: gunakan perlindungan untuk credential yang dikirim browser otomatis seperti cookie. CORS bukan perlindungan CSRF. Tentukan token/antiforgery sesuai alur.
- Secrets: environment/secret manager; tidak di repo, sample atau log. Konfigurasi contoh memakai placeholder.
- Errors/logs: tidak membocorkan stack trace ke client; trace ID untuk diagnosis; redaksi data sensitif.
- Audit: actor dari identitas server, UTC timestamp, action, target ID, outcome dan trace ID; jangan mempercayai actor dari request.
- Transport/firewall: HTTPS, pembatasan akses DB, trusted reverse proxy. Firewall adalah konfigurasi infrastruktur, bukan atribut controller.
- File: batas ukuran, tipe yang tervalidasi, storage access policy dan nama aman; jangan mengeksekusi konten upload.
- Integrasi: timeout/cancellation, validasi URL tujuan, hindari SSRF dan retry mutasi yang tidak idempotent.
- Dependency: verifikasi versi, patch dan lisensi saat install; jangan menganggap daftar ini membuktikan produksi aman.

Review harus menyebut lokasi bukti, temuan, dampak dan perbaikan. Jika belum ada implementasi, tandai belum tersedia.
