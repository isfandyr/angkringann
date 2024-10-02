# Angkringan Mas Pithik

Angkringan Mas Pithik adalah aplikasi web untuk manajemen dan pemesanan makanan dari warung angkringan. Aplikasi ini memungkinkan pelanggan untuk melihat menu, melakukan pemesanan, dan melacak status pesanan mereka. Sementara itu, pemilik warung dapat mengelola menu, pesanan, dan melihat laporan penjualan.

## Fitur Utama

- Autentikasi pengguna (login/register)
- Manajemen menu (untuk admin)
- Pemesanan makanan
- Keranjang belanja
- Pembayaran
- Riwayat transaksi
- Dashboard admin

## Teknologi yang Digunakan

- React.js
- Supabase (Backend as a Service)
- Tailwind CSS
- Framer Motion (untuk animasi)

## Panduan Instalasi

1. Clone repositori ini
2. Jalankan `npm install` untuk menginstal dependensi
3. Buat proyek baru di Supabase dan dapatkan URL dan API Key
4. Buat file `.env` di root proyek dan tambahkan kredensial Supabase:

   ```
   REACT_APP_SUPABASE_URL=YOUR_SUPABASE_URL
   REACT_APP_SUPABASE_ANON_KEY=YOUR_SUPABASE_ANON_KEY
   ```

5. Jalankan `npm start` untuk memulai aplikasi dalam mode pengembangan

## Struktur Database Supabase

Berikut adalah tabel dan kolom yang diperlukan di Supabase:

### Tabel: users

| Kolom      | Tipe Data | Keterangan                    |
|------------|-----------|-------------------------------|
| id         | uuid      | Primary Key                   |
| email      | text      | Email pengguna                |
| is_admin   | boolean   | Status admin                  |
| created_at | timestamp | Waktu pembuatan akun          |

### Tabel: profiles

| Kolom        | Tipe Data | Keterangan                    |
|--------------|-----------|-------------------------------|
| id           | uuid      | Primary Key (sama dengan users.id) |
| name         | text      | Nama pengguna                 |
| phone_number | text      | Nomor telepon pengguna        |
| updated_at   | timestamp | Waktu terakhir update profil  |

### Tabel: menu_items

| Kolom       | Tipe Data | Keterangan                    |
|-------------|-----------|-------------------------------|
| id          | uuid      | Primary Key                   |
| title       | text      | Nama menu                     |
| description | text      | Deskripsi menu                |
| price       | numeric   | Harga menu                    |
| category    | text      | Kategori menu                 |
| image_url   | text      | URL gambar menu               |
| status      | text      | Status menu (active/draft)    |
| created_at  | timestamp | Waktu pembuatan menu          |

### Tabel: orders

| Kolom          | Tipe Data | Keterangan                    |
|----------------|-----------|-------------------------------|
| id             | uuid      | Primary Key                   |
| user_id        | uuid      | Foreign Key ke users.id       |
| total_amount   | numeric   | Total harga pesanan           |
| status         | text      | Status pesanan                |
| payment_status | text      | Status pembayaran             |
| payment_method | text      | Metode pembayaran             |
| created_at     | timestamp | Waktu pembuatan pesanan       |

### Tabel: order_items

| Kolom        | Tipe Data | Keterangan                    |
|--------------|-----------|-------------------------------|
| id           | uuid      | Primary Key                   |
| order_id     | uuid      | Foreign Key ke orders.id      |
| menu_item_id | uuid      | Foreign Key ke menu_items.id  |
| quantity     | integer   | Jumlah item yang dipesan      |
| price        | numeric   | Harga per item saat dipesan   |

### Tabel: notifications

| Kolom     | Tipe Data | Keterangan                    |
|-----------|-----------|-------------------------------|
| id        | uuid      | Primary Key                   |
| user_id   | uuid      | Foreign Key ke users.id       |
| message   | text      | Isi notifikasi                |
| read      | boolean   | Status dibaca                 |
| created_at| timestamp | Waktu pembuatan notifikasi    |

### Tabel: bank_accounts

| Kolom          | Tipe Data | Keterangan                    |
|----------------|-----------|-------------------------------|
| id             | uuid      | Primary Key                   |
| bank_name      | text      | Nama bank                     |
| account_number | text      | Nomor rekening                |
| account_name   | text      | Nama pemilik rekening         |

### Tabel: qris_codes

| Kolom     | Tipe Data | Keterangan                    |
|-----------|-----------|-------------------------------|
| id        | uuid      | Primary Key                   |
| qris_url  | text      | URL gambar kode QRIS          |
| is_active | boolean   | Status aktif                  |

## Konfigurasi Tambahan

1. Aktifkan autentikasi email di Supabase
2. Atur kebijakan keamanan (RLS) untuk setiap tabel
3. Buat bucket storage untuk menyimpan gambar menu

## Kontribusi

Kontribusi selalu diterima. Silakan buat issue atau pull request untuk perbaikan atau penambahan fitur.
