# 🍱 Monitor Berita — MBG · SPPG · Koperasi Desa Merah Putih

Dashboard pemantauan pemberitaan media Indonesia untuk tiga program pemerintah.

| Topik | Kata kunci pencarian |
|---|---|
| **Makan Bergizi Gratis (MBG)** | `Makan Bergizi Gratis MBG` |
| **SPPG** | `SPPG Satuan Pelayanan Pemenuhan Gizi dapur` |
| **Koperasi Desa Merah Putih** | `Koperasi Desa Merah Putih KDMP` |

---

## Cara Kerja

1. GitHub Actions menjalankan `scripts/fetch_news.py` setiap **6 jam**
2. Script mengambil berita dari Google News RSS
3. Berita **diakumulasi** ke `docs/data/news.json` — data lama tidak pernah dihapus
4. Dashboard di GitHub Pages membaca JSON dan menampilkan semua berita secara interaktif

---

## Setup (dari awal)

### 1. Buat repo baru di GitHub, upload/push semua file ini

### 2. Aktifkan GitHub Pages
- Settings → Pages → Source: **Deploy from a branch**
- Branch: `main`, folder: `/docs` → Save

### 3. Buat workflow (jika belum otomatis terbaca)
- Pergi ke tab **Actions** → New workflow → set up a workflow yourself
- Nama file: `update-news.yml`
- Isi dengan konten dari `.github/workflows/update-news.yml`

### 4. Jalankan fetch pertama kali
- Tab **Actions** → workflow "Update Berita Monitor MBG" → **Run workflow**
- Tunggu sekitar 1 menit, data pertama akan masuk

---

## Fitur Dashboard

- Filter topik: Semua / MBG / SPPG / Koperasi Desa
- Filter periode cepat: Hari ini / 7 hari / 30 hari / 90 hari / 6 bulan / 1 tahun / Semua waktu
- Filter bulan & tahun spesifik (dropdown)
- Pencarian judul dan nama media
- Urutan terbaru / terlama
- Grafik sebaran topik (donut) dan tren 30 hari (bar chart)
- Top 10 sumber media
- Ekspor Excel (.xlsx) dan CSV sesuai filter aktif
- Paginasi: 25 / 50 / 100 / Semua per halaman

---

## Struktur File

```
├── .github/workflows/update-news.yml   ← Scheduler otomatis tiap 6 jam
├── scripts/fetch_news.py               ← Script fetch & akumulasi
├── docs/index.html                     ← Dashboard GitHub Pages
├── docs/data/news.json                 ← Data berita (auto-generated)
└── README.md
```
