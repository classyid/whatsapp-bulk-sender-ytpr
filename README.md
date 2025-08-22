# WhatsApp Bulk Sender YTPR

Sistem WhatsApp Bulk Sender untuk Yayasan Taman Pendidikan Rahmat - Aplikasi web berbasis Flask untuk mengirim pesan WhatsApp massal dengan fitur anti-ban, multi-user, dan logging lengkap.

## Fitur Utama

### 🔐 **Sistem Authentication**
- Login/logout dengan session management
- Multi-user support dengan role-based access
- Ganti password dan profile management
- User management untuk admin

### 📱 **WhatsApp Integration**
- Kirim pesan teks individual dan massal
- Kirim media (gambar, dokumen, audio, video, sticker)
- Test send untuk semua jenis media
- Integrasi dengan WhatsApp Bot API

### 🛡️ **Anti-Ban System**
- Random delay antar pesan (3-7 detik default)
- Batch processing dengan delay lebih lama
- Daily message limits (300 pesan/hari default)
- Template variables untuk variasi pesan

### 📊 **Logging & Monitoring**
- Message logs detail dengan export Excel
- Activity logs untuk bulk sending
- Progress tracking real-time
- Emergency stop functionality

### 🎨 **User Interface**
- Responsive design (desktop & mobile)
- Islamic-themed dengan logo yayasan
- Dashboard informatif dengan statistik
- Modern UI dengan Tailwind CSS

## Teknologi

- **Backend**: Python Flask
- **Database**: SQLite
- **Frontend**: HTML, CSS (Tailwind), JavaScript
- **Authentication**: Werkzeug Security
- **File Processing**: Pandas, openpyxl
- **API Integration**: Requests

## Persyaratan Sistem

- Python 3.8+
- WhatsApp Bot API (eksternal)
- RAM minimal 512MB
- Storage minimal 1GB

## Instalasi

### 1. Clone Repository
```bash
git clone https://github.com/classyid/whatsapp-bulk-sender-ytpr.git
cd whatsapp-bulk-sender-ytpr
```

### 2. Buat Virtual Environment
```bash
python3 -m venv venv
source venv/bin/activate  # Linux/Mac
# atau venv\Scripts\activate  # Windows
```

### 3. Install Dependencies
```bash
pip install -r requirements.txt
```

### 4. Setup Folder
```bash
mkdir uploads static
# Letakkan logo.png di folder static/
```

### 5. Jalankan Aplikasi
```bash
python3 app.py
```

### 6. Akses Aplikasi
- Buka browser: `http://localhost:5000`
- **Default Login:**
  - Username: `admin`
  - Password: `admin123`

## Konfigurasi WhatsApp Bot API

Aplikasi ini memerlukan WhatsApp Bot API eksternal. Pastikan API berjalan dan setup URL di menu Settings.

**API Endpoints yang Diperlukan:**
- `POST /api/send-message` - Kirim teks
- `POST /api/send-image` - Kirim gambar
- `POST /api/send-document` - Kirim dokumen
- `POST /api/send-audio` - Kirim audio
- `POST /api/send-video` - Kirim video
- `GET /api/status` - Status bot

## Penggunaan

### **Login Pertama Kali**
1. Akses `http://localhost:5000`
2. Login dengan username: `admin`, password: `admin123`
3. Ganti password di menu Profile

### **Setup API WhatsApp**
1. Masuk ke menu Settings
2. Set API Base URL ke URL WhatsApp Bot API Anda
3. Test koneksi di menu Device Status

### **Kirim Pesan Individual**
1. Pilih menu "Kirim Pesan"
2. Masukkan nomor dan pesan
3. Klik "Kirim Pesan"

### **Kirim Media**
1. Pilih menu "Kirim Media"
2. Pilih jenis media dan upload file
3. Tambahkan caption (opsional)
4. Klik "Kirim Media"

### **Kirim Massal**
1. Siapkan file CSV/Excel dengan kolom 'phone'
2. Pilih menu "Kirim Massal"
3. Upload file data
4. Pilih jenis pengiriman (teks/media)
5. Buat template pesan dengan variabel
6. Gunakan mode test untuk uji coba
7. Mulai pengiriman massal

### **Template Variables**
Gunakan variabel ini dalam pesan untuk personalisasi:
- `{salam}` - Salam Islami otomatis
- `{sapaan}` - Sapaan acak
- `{variasi_penutup}` - Penutup Islami
- `{nama_kolom}` - Data dari kolom CSV

**Contoh Template:**
```
{salam}
{sapaan},

Kami informasikan bahwa pembayaran untuk {nama_siswa} kelas {kelas} sejumlah {nominal} telah jatuh tempo pada {tanggal_tempo}.

{variasi_penutup}
```

## Format File CSV

File CSV harus memiliki struktur:
```csv
phone,nama_siswa,kelas,nominal,tanggal_tempo
628123456789,Ahmad,1A,Rp500.000,10 Agustus 2024
628987654321,Fatimah,2B,Rp500.000,10 Agustus 2024
```

## Pengaturan Anti-Ban

### **Rekomendasi Pengaturan:**
- **Min Delay**: 3 detik
- **Max Delay**: 7 detik  
- **Batch Size**: 10 pesan
- **Batch Delay**: 60 detik
- **Max per Day**: 300 pesan

### **Tips Menghindari Ban:**
- Jangan kirim pesan identik ke banyak nomor
- Gunakan variasi template dengan variables
- Hindari spam dan konten promosi berlebihan
- Batasi pengiriman sesuai rekomendasi
- Gunakan mode test sebelum bulk sending

## User Management

Admin dapat mengelola user melalui menu "Manajemen User":
- Tambah user baru
- Aktifkan/nonaktifkan user
- Hapus user (kecuali admin)

## Monitoring & Logs

### **Message Logs**
- Riwayat semua pengiriman
- Filter berdasarkan tanggal dan status
- Export ke Excel
- Success rate tracking

### **Activity Logs**
- Log aktivitas bulk sending
- Detail session dan statistik
- Tracking success/failure per campaign

### **Emergency Stop**
- Hentikan semua proses bulk sending
- Monitor sesi aktif
- Force stop untuk situasi darurat

## Troubleshooting

### **Bot Tidak Terhubung**
1. Cek URL API di Settings
2. Pastikan WhatsApp Bot API berjalan
3. Test koneksi di Device Status

### **Bulk Sending Stuck**
1. Cek log di terminal
2. Pastikan format CSV benar
3. Gunakan Emergency Stop jika perlu

### **File Upload Error**
1. Cek ukuran file (max sesuai jenis media)
2. Pastikan format file didukung
3. Cek permission folder uploads

## Security

- Password di-hash dengan bcrypt
- Session-based authentication
- Input validation dan sanitization
- SQL injection protection
- File upload security

## Kontribusi

1. Fork repository
2. Buat feature branch
3. Commit perubahan
4. Push ke branch
5. Buat Pull Request

## Lisensi

Copyright © 2025 Yayasan Taman Pendidikan Rahmat, Kediri

## Support

Untuk bantuan teknis atau pertanyaan:
- Buat issue di GitHub
- Dokumentasi lengkap tersedia di wiki

---

**Dibuat khusus untuk Yayasan Taman Pendidikan Rahmat, Kota Kediri**
