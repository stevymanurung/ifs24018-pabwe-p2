# 11S24018-pabwe-p2 — Aksara AI

Studi Kasus Praktikum 2 PABWE 2026 (CSS, Bootstrap 5 & Tailwind CSS 4).
Website multi-halaman untuk perusahaan jasa AI fiktif bernama **Aksara AI**.

Semua halaman saling terhubung, identitas brand konsisten, dan setiap halaman
memakai **satu** pendekatan styling sesuai ketentuan soal.

## Struktur proyek

```
11S24018-pabwe-p2/
├── index.html               # Landing page — HTML + CSS murni (tanpa framework)
├── blog.html                # Daftar blog — Bootstrap 5 + Bootstrap Icons
├── blog-detail.html         # Detail artikel — Bootstrap 5 + Bootstrap Icons
├── cv.html                  # Curriculum Vitae — Tailwind CSS 4
├── assets/
│   ├── css/
│   │   ├── style.css        # External CSS, khusus untuk index.html
│   │   └── fonts.css        # @font-face Fraunces & Plus Jakarta Sans
│   ├── fonts/               # File .woff2 (subset latin)
│   └── img/                 # Cover artikel, avatar CV, favicon (SVG lokal)
├── vendor/                  # Bootstrap 5, Bootstrap Icons, Tabler Icons, Tailwind 4
└── README.md
```

## Pembagian teknologi per halaman

| Halaman | Teknologi styling | Catatan |
|---|---|---|
| `index.html` | HTML + CSS murni | Wajib `assets/css/style.css`, tanpa Bootstrap/Tailwind |
| `blog.html` | Bootstrap 5 + Bootstrap Icons | CSS custom tipis di `<style>` untuk warna brand |
| `blog-detail.html` | Bootstrap 5 + Bootstrap Icons | Sama seperti `blog.html` |
| `cv.html` | Tailwind CSS 4 | Token warna brand lewat `@theme`, ikon Tabler |

Library tidak diambil dari CDN melainkan **di-self-host** di folder `vendor/`
dan `assets/fonts/`. Isinya identik dengan versi CDN (Bootstrap 5.3, Tailwind
Play CDN `@tailwindcss/browser@4`), hanya lokasinya lokal — sehingga halaman
tetap tampil benar walau dibuka offline atau lewat `file://`.

## Yang dipenuhi dari ketentuan soal

**index.html** — navbar dengan link in-page (`#layanan`, `#tentang`, `#kontak`)
plus link ke `blog.html` dan `cv.html`, hero + CTA, 4 card layanan AI, section
tentang, form kontak (nama, email, pesan), dan footer. Memakai CSS variables,
Flexbox, CSS Grid, hover/transition, serta `@media` di 3 breakpoint. Menu
mobile dibuat dengan teknik checkbox (tanpa JavaScript).

**blog.html** — 6 artikel bertema AI. Tiap card menampilkan cover, badge
kategori berikon, judul yang mengarah ke `blog-detail.html`, ringkasan singkat,
serta penulis/tanggal/durasi baca dengan Bootstrap Icons (`bi-person`,
`bi-calendar3`, `bi-clock`). Memakai navbar, container, row, `col-*`, card,
badge, pagination, dan footer bawaan Bootstrap.

**blog-detail.html** — cover lebar, meta penulis/tanggal/kategori berikon,
judul `h1`, 5 paragraf pembahasan RAG, blockquote, list tips, alert, card
artikel terkait, dan area komentar sederhana (avatar + textarea + submit).

**cv.html** — header profil (avatar, nama, role, kontak, lokasi, GitHub,
LinkedIn), about, pendidikan, pengalaman (3 item), chip keahlian, 4 proyek,
dan sertifikat. Seluruhnya memakai utility Tailwind: `flex`/`grid` + `gap`,
spacing, breakpoint `sm:`/`md:`/`lg:`, serta `hover:` dan `transition`.

**Integrasi** — `index.html`, `blog.html`, dan `cv.html` saling tertaut dari
navbar dan footer di setiap halaman; judul artikel di `blog.html` membuka
`blog-detail.html`; `blog-detail.html` punya tombol kembali ke daftar blog.
Seluruh link ditulis relatif (`index.html`, bukan `/`) supaya navigasi tetap
jalan baik saat dibuka langsung dari folder maupun saat di-hosting.

## Yang masih perlu disesuaikan sebelum dikumpulkan

Bagian ini ditandai dengan komentar `<!-- GANTI: ... -->` di dalam `cv.html`:

- Nama lengkap (saat ini: `Stiy`), bila berbeda dengan yang tertera di KTM
- Nomor WhatsApp aktif
- URL GitHub dan LinkedIn pribadi
- Nama SMA/SMK dan tahun kelulusan
- Avatar CV memakai SVG di `assets/img/avatar-cv.svg` — boleh diganti pas foto
  asli (letakkan di `assets/img/`, lalu ubah `src` di `cv.html`)

## Cara menjalankan

- **Lokal:** buka `index.html` langsung di browser. Untuk pengalaman terbaik,
  gunakan ekstensi **Live Server** di VS Code.
- **Hosting statis:** unggah **isi** folder ini (bukan foldernya) agar
  `index.html` berada di root.

## Checklist

- [x] Landing page AI dengan external CSS, tanpa framework apa pun
- [x] Blog list & detail memakai Bootstrap 5 + Bootstrap Icons
- [x] CV memakai Tailwind CSS 4 sebagai sistem styling utama
- [x] Semantic HTML5 (`header`, `nav`, `main`, `section`, `article`, `footer`)
- [x] Responsive di desktop dan mobile
- [x] Tidak ada inline `style=` — seluruh styling lewat external/internal CSS
- [x] Semua gambar lokal di `assets/img/`, tanpa dependensi URL eksternal
- [x] Navigasi antar halaman berfungsi (link relatif), brand konsisten
- [x] Komentar singkat di bagian penting tiap file
- [ ] Data pribadi di `cv.html` sudah diisi (lihat daftar di atas)
- [ ] Sudah dicek tampilannya di browser sungguhan sebelum submit
