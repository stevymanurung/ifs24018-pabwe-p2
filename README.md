# {username-kamu}-pabwe-p2 — Aksara AI

Studi kasus Praktikum 2 (PABWE): landing page, blog, dan CV untuk perusahaan
fiktif jasa AI bernama **Aksara AI**.

## Struktur proyek

```
├── index.html              # Landing page (HTML + CSS murni)
├── blog.html                # Daftar blog (Bootstrap 5 + Bootstrap Icons)
├── blog-detail.html         # Detail blog (Bootstrap 5 + Bootstrap Icons)
├── cv.html                   # CV digital (Tailwind CSS 4)
├── assets/
│   ├── css/
│   │   ├── style.css         # External CSS untuk index.html
│   │   └── fonts.css         # Google Fonts (Fraunces & Plus Jakarta Sans), self-hosted
│   ├── fonts/                 # File .woff2 font, subset Latin saja
│   └── img/                    # (opsional, belum dipakai)
├── vendor/                     # Bootstrap, Bootstrap Icons, Tabler Icons, Tailwind — SEMUA SELF-HOSTED
├── _redirects                  # Aturan Netlify: /index di-rewrite (200) ke index.html, bukan redirect
└── README.md
```

**Penting:** semua library (Bootstrap, Bootstrap Icons, Tabler Icons, Tailwind
CSS 4 Play CDN, Google Fonts) sudah di-*self-host* jadi file lokal di folder
`vendor/` dan `assets/`. Tidak ada satupun `<link>`/`<script>` yang menunjuk ke
CDN eksternal lagi. Ini dilakukan karena banyak sandbox/runner audit otomatis
(termasuk yang dipakai tool penilaian kampus) memblokir domain CDN pihak
ketiga, yang bisa membuat Lighthouse gagal total memuat halaman dan
melaporkan skor 0 di semua kategori — padahal halamannya sendiri sebenarnya
baik-baik saja.

## ⚠️ Kalau skor audit masih 0 — cek cara deploy-nya

Skor Lighthouse 0 di **semua** kategori sekaligus (Performance, Accessibility,
Best Practices, SEO) biasanya bukan berarti halamannya jelek — itu tanda
Lighthouse **gagal memuat halaman sama sekali**. Dua penyebab paling umum:

1. **Folder ter-upload sebagai subfolder di Netlify.** Kalau kamu drag folder
   bernama `project` (atau nama lain) ke Netlify Drop, isinya bisa berakhir di
   `/project/index.html`, bukan di root (`/index.html`). Root domain jadi 404.
   **Solusi:** buka/extract folder ini dulu, lalu drag-drop **isi filenya**
   (`index.html`, `blog.html`, dst. beserta folder `assets/` dan `vendor/`
   langsung terlihat), bukan foldernya sendiri.
2. **Cek langsung di browser** apakah `https://ifs24018-p2.netlify.app`
   benar-benar menampilkan landing page-nya, bukan halaman "Page not found"
   bawaan Netlify. Kalau masih 404, redeploy dengan cara di atas.

Setelah redeploy, tunggu 1–2 menit lalu jalankan ulang audit-nya.

## Yang perlu kamu sesuaikan sebelum dikumpulkan

- **Ganti nama folder** menjadi `{username-kamu}-pabwe-p2`, misalnya `ifs24018-pabwe-p2`.
- **cv.html**: ganti "Nama Mahasiswa", email, nomor telepon, riwayat pendidikan,
  pengalaman, dan link GitHub/LinkedIn dengan data kamu sendiri.
- **Nama & tema perusahaan** ("Aksara AI") boleh diganti bebas sesuai selera,
  asal konsisten di semua halaman (index.html, blog.html, blog-detail.html).
- Foto profil CV memakai avatar generator (dicebear.com, via URL eksternal)
  sebagai placeholder — boleh diganti foto asli, taruh di `assets/img/`.
- Gambar cover blog memakai Unsplash (URL eksternal) — boleh diganti gambar
  lain yang relevan, lokal atau URL publik.

## Cara menjalankan / deploy

- **Lokal:** buka `index.html` langsung di browser, atau gunakan ekstensi
  **Live Server** di VSCode agar navigasi antar halaman berjalan mulus.
- **Netlify:** drag-drop **isi folder ini** (bukan foldernya) ke
  Netlify Drop (app.netlify.com/drop), atau hubungkan lewat Git.

## Checklist pengumpulan

- [x] Landing page AI dengan external CSS berjalan, tanpa framework
- [x] Blog list + detail memakai Bootstrap 5 & Bootstrap Icons
- [x] Konten blog terkait AI (6 artikel)
- [x] CV memakai Tailwind CSS 4
- [x] Semua halaman saling terhubung lewat navigasi
- [x] Semua CDN eksternal sudah di-self-host (vendor/, assets/fonts/)
- [x] Audit aksesibilitas otomatis (axe-core) lokal: 0 pelanggaran di 4 halaman
- [x] Kontras warna teks disesuaikan agar lolos WCAG AA (>=4.5:1)
- [x] Heading order rapi (h1->h2->h3, tidak ada yang loncat level)
- [ ] Sudah dicek di browser sungguhan (bukan cuma dari kode) — cek tampilan
      & console error sendiri sebelum submit final
- [ ] Sudah dikonfirmasi URL Netlify menampilkan halaman yang benar (bukan 404)
