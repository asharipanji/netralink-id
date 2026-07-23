# Netralink.id — Landing Page

Landing page statis untuk **Netralink.id**, Internet Service Provider lokal yang melayani Kabupaten Bandung dan sekitarnya.

## Struktur

```
.
├── index.html          # Seluruh halaman (HTML + CSS inline, single file)
├── .nojekyll           # Menonaktifkan Jekyll di GitHub Pages
└── .github/workflows/
    └── deploy-pages.yml  # Auto-deploy ke GitHub Pages saat push ke main
```

## Menjalankan Secara Lokal

```bash
python3 -m http.server 8000
# buka http://localhost:8000
```

## Deploy ke GitHub Pages

1. Push repo ini ke GitHub.
2. Buka **Settings → Pages → Build and deployment → Source: GitHub Actions**.
3. Workflow `deploy-pages.yml` akan otomatis jalan setiap push ke branch `main`.

### Custom Domain

Buat file `CNAME` berisi satu baris domain, lalu arahkan DNS:

```
netralink.id
```

| Type  | Name | Value                  |
|-------|------|------------------------|
| A     | @    | 185.199.108.153        |
| A     | @    | 185.199.109.153        |
| A     | @    | 185.199.110.153        |
| A     | @    | 185.199.111.153        |
| CNAME | www  | <username>.github.io   |

## Yang Masih Perlu Diisi

- [ ] Nomor WhatsApp di footer (`0812-xxxx-xxxx`)
- [ ] Alamat lengkap kantor
- [ ] Meta description, Open Graph, dan favicon untuk SEO
- [ ] Link WhatsApp aktif pada tombol CTA (`https://wa.me/62...`)

## Lisensi

Hak cipta © 2026 Netralink.id. Seluruh hak cipta dilindungi.
