# Testing Role

Pilih test berdasarkan perilaku dan risiko. Unit test untuk invariant/UseCase; integration test untuk HTTP pipeline, authorization dan SP nyata di database test terisolasi. Periksa sukses, invalid, missing, conflict dan forbidden sesuai operasi. Gunakan fixture deterministik dan cleanup; jangan menyentuh produksi. Catat test skipped beserta alasannya. Jangan mengubah expected output sekadar agar test lulus.

Ikuti AGENTS.md. Panduan ini tidak membuat subagent otomatis.
