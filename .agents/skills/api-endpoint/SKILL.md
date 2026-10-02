---
name: api-endpoint
description: Create or change ASP.NET controller endpoints, HTTP contracts, DTOs and API version compatibility. Use for endpoint-focused tasks; use backend-feature for complete business operations.
---

# api-endpoint

1. Baca AGENTS.md, docs/API-CONTRACT.md, docs/SECURITY.md dan controller terkait.
2. Tentukan method, resource lowercase/plural, version, request/response DTO dan nullability.
3. Tentukan authentication/policy, ownership, validation dan HTTP status untuk semua outcome.
4. Implementasikan controller tipis yang memanggil UseCase dan meneruskan CancellationToken.
5. Pertahankan ApiResponse<T> dan mapping validation/exception yang konsisten termasuk framework errors; 204 tidak memiliki body.
6. Dokumentasikan OpenAPI dan breaking changes; regenerate client hanya jika toolchain tersedia.
7. Verifikasi binding, status, response dan forbidden lewat test yang relevan. Laporkan perubahan kontrak.
