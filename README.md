# Netralink.id — Landing Page

Landing page statis untuk **Netralink.id**, Internet Service Provider lokal yang melayani Kabupaten Bandung dan sekitarnya.

## Struktur

```
.
├── index.html          # Seluruh halaman (HTML + CSS inline, single file)
├── .nojekyll           # Sisa dari deploy berbasis branch; tidak dipakai lagi
│                       # (Jekyll tidak pernah jalan pada deploy via Actions)
└── .github/workflows/
    └── deploy-pages.yml  # Auto-deploy ke GitHub Pages saat push ke main
```

Workflow menyalin hanya `index.html` (dan folder `assets/` bila ada) ke `_site/`
sebelum diunggah — jadi `README.md` dan `.gitignore` **tidak** ikut tayang di situs.

## Menjalankan Secara Lokal

```bash
python3 -m http.server 8000
```

Lalu buka <http://localhost:8000>.

## Deploy ke GitHub Pages

> **Syarat:** GitHub Pages hanya tersedia untuk repo **publik** pada akun GitHub Free.
> Repo privat butuh GitHub Pro/Team/Enterprise. Selama repo ini privat dan akun
> masih Free, workflow di bawah tidak akan berhasil menerbitkan situs.

1. **Lebih dulu** buka **Settings → Pages → Build and deployment → Source: GitHub Actions**.
   Kalau langkah ini dilewati, run pertama gagal di `Get Pages site failed` —
   `configure-pages` tidak bisa mengaktifkan Pages sendiri dengan `GITHUB_TOKEN`.
2. Push ke branch `main`.
3. Cek tab **Actions** sampai hijau. Kalau sudah terlanjur merah karena urutan
   langkah 1, cukup **Re-run all jobs**.
4. Situs tayang di `https://<username>.github.io/<repo>/`.

### Custom Domain

> Pada deploy via GitHub Actions, **file `CNAME` di repo tidak berpengaruh apa pun.**
> Domain harus diatur lewat Settings, bukan lewat file.

1. **Settings → Pages → Custom domain →** isi `netralink.id` → **Save**.
2. Atur DNS di registrar:

| Type  | Name | Value                    |
|-------|------|--------------------------|
| A     | @    | 185.199.108.153          |
| A     | @    | 185.199.109.153          |
| A     | @    | 185.199.110.153          |
| A     | @    | 185.199.111.153          |
| AAAA  | @    | 2606:50c0:8000::153      |
| AAAA  | @    | 2606:50c0:8001::153      |
| AAAA  | @    | 2606:50c0:8002::153      |
| AAAA  | @    | 2606:50c0:8003::153      |
| CNAME | www  | `<username>.github.io`   |

3. Tunggu pengecekan DNS hijau, lalu centang **Enforce HTTPS**
   (opsinya bisa baru muncul sampai 24 jam kemudian).

Jangan mengarahkan subdomain `www` ke apex `netralink.id` — kombinasi itu
merusak Enforce HTTPS. Pakai pola A/AAAA + CNAME `www` seperti tabel di atas.

## Yang Masih Perlu Diisi

- [ ] Nomor WhatsApp di footer (`0812-xxxx-xxxx` masih placeholder)
- [ ] Alamat lengkap kantor (baru "Soreang, Kab. Bandung")
- [ ] Link WhatsApp aktif pada 7 tombol CTA (`https://wa.me/62...`) — sekarang
      semuanya hanya loncat ke footer, jadi tidak ada jalur konversi nyata
- [ ] Gambar share 1200×630 di `assets/og-image.jpg`, lalu buka komentar blok
      `og:image` / `twitter:image` di `index.html`
- [ ] Verifikasi testimoni dan angka klaim (99.9% uptime, 10.000+ pelanggan)
      sebelum situs dibuat publik
- [ ] `canonical` dan `og:url` menunjuk ke `https://netralink.id/`. Selama domain
      itu belum aktif, jangan diindeks — atau tunda publikasi sampai DNS pindah.

Sudah selesai: meta description, Open Graph, Twitter Card, favicon, JSON-LD
(Organization / LocalBusiness / Service), menu mobile, dan perbaikan aksesibilitas.

## Lisensi

Hak cipta © 2026 Netralink.id. Seluruh hak cipta dilindungi.
Tidak ada lisensi yang diberikan untuk menggunakan, menyalin, atau membuat karya
turunan dari kode ini.
