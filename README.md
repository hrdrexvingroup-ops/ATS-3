# CV Matching System (ATS) - AI-Powered Candidate Ranking

> Advanced CV matching system dengan AI scoring menggunakan Groq API

## 🎯 Fitur Utama

✅ **Input Fleksibel**
- Nama posisi, kualifikasi, job description
- Simpan requirement untuk analisis multiple batch

✅ **Upload Multiple CV**
- Format: PDF, DOCX (max 10 file @ 10MB each)
- Drag & drop atau klik upload

✅ **AI Scoring dengan Groq**
- Groq API (llama-3.3-70b) untuk analisis kecocokan
- Fallback ke keyword-based scoring jika API tidak tersedia
- Optional - sistem tetap berjalan tanpa API Key

✅ **Parsing CV Cerdas**
- **Nama**: Deteksi dari pattern atau ekstraksi otomatis
- **Usia**: Dari kata "umur/usia" atau tahun lahir (19xx/20xx)
- **Pendidikan**: S2, S1, D4, D3, SMA, SMK
- **Jurusan**: Teknik Sipil, Akuntansi, Informatika, dll (30+ keyword)
- **Alamat**: Deteksi kota besar Indonesia atau ekstraksi pola
- **Pengalaman**: Ambil dari pola "Nama Perusahaan (tahun-tahun)"

✅ **Hasil Profesional**
- Tabel ranking dengan skor 0-100
- Badge rekomendasi: High Priority / Layak Interview / Cadangan
- Export ke Excel (XLSX)

✅ **UI Modern**
- Responsive design (desktop/tablet/mobile)
- Gradient header, card-based layout
- Toast notifications
- Loading spinner
- Dark mode ready

## 🚀 Quick Start

### Opsi 1: Buka Langsung (No Setup)
1. Download file `cv_matching_ats.html`
2. Buka di browser (Firefox, Chrome, Safari, Edge)
3. Mulai gunakan langsung!

### Opsi 2: Deploy ke GitHub Pages (Recommended)

```bash
# 1. Clone atau buat repo
git clone https://github.com/username/cv-matching-ats.git
cd cv-matching-ats

# 2. Buat file struktur
# Letakkan cv_matching_ats.html di root folder

# 3. Push ke GitHub
git add .
git commit -m "Add CV Matching System"
git push origin main

# 4. Aktifkan GitHub Pages
# Settings > Pages > Source: main branch
# Akses: https://username.github.io/cv-matching-ats/cv_matching_ats.html
```

### Opsi 3: Local Server (Rekomendasi untuk development)

```bash
# Python 3
python -m http.server 8000

# Node.js (npm)
npm install -g http-server
http-server

# Akses: http://localhost:8000
```

## 🔧 Cara Pakai

### 1️⃣ Setup API Key (Optional tapi Recommended)

1. **Daftar Groq**: https://groq.com (gratis)
2. **Generate API Key**: 
   - Login ke console.groq.com
   - Copy API Key (format: `gsk_...`)
3. **Masukkan ke Aplikasi**:
   - Tab "Groq API Key"
   - Paste API Key
   - Klik "Simpan"
   - Tunggu notifikasi "API Groq Terhubung"

### 2️⃣ Input Requirement Pekerjaan

1. Tab "Informasi Posisi"
2. Isi:
   - **Nama Posisi**: Contoh "Senior Engineer"
   - **Kualifikasi** (required):
     ```
     - Pendidikan S1 Teknik Sipil
     - Pengalaman 3+ tahun
     - Menguasai AutoCAD, SAP
     ```
   - **Job Description** (optional): Deskripsi lengkap pekerjaan
3. Klik "Simpan Requirement"

### 3️⃣ Upload CV Kandidat

1. Tab "Upload CV Kandidat"
2. Drag file atau klik untuk browse
3. Pilih 1-10 file PDF/DOCX
4. Lihat preview file yang diupload

### 4️⃣ Jalankan Analisis

1. Klik "Mulai Analisis CV"
2. Tunggu loading spinner selesai
3. Lihat hasil di tabel (otomatis sorted by score)

### 5️⃣ Export Hasil

1. Klik "Export" (XLSX file)
2. File otomatis download
3. Nama file: `CV_Ranking_[posisi]_[tanggal].xlsx`

## 📊 Sistem Scoring

### Dengan Groq API (Recommended)
- AI menganalisis keseluruhan CV vs requirement
- Skor berdasarkan semantic matching
- Lebih akurat untuk CV yang tidak terstruktur

### Fallback Scoring (Tanpa API)
Breakdown poin:
- **Pendidikan (40 poin)**
  - S2: 40, S1: 35, D4: 28, D3: 20, SMA: 10, SMK: 12
- **Jurusan (30 poin)**: Match dengan requirement keywords
- **Pengalaman (20 poin)**: Match dengan requirement keywords
- **Bonus (10 poin)**: Alamat + Usia detected

**Rekomendasi**:
- ≥75: **High Priority** ✅
- 50-74: **Layak Interview** 🟡
- <50: **Cadangan** ⚠️

## 🔐 Keamanan

✅ **API Key Tersimpan Aman**
- Disimpan di `localStorage` browser (hanya local)
- Tidak dikirim ke server mana pun (kecuali Groq API)
- Tidak ada tracking atau logging

✅ **Data Privacy**
- Semua processing lokal (frontend only)
- Tidak ada backend server
- File CV hanya dibaca di browser RAM, tidak disimpan

## 📱 Browser Compatibility

| Browser | Desktop | Tablet | Mobile |
|---------|---------|--------|--------|
| Chrome  | ✅      | ✅     | ✅     |
| Firefox | ✅      | ✅     | ✅     |
| Safari  | ✅      | ✅     | ✅     |
| Edge    | ✅      | ✅     | ✅     |

## 📦 Dependencies (CDN)

Semua library diambil dari CDN publik:

```html
<!-- PDF Reading -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/pdf.js/3.11.174/pdf.min.js"></script>

<!-- DOCX Reading -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/mammoth/1.6.0/mammoth.min.js"></script>

<!-- Excel Export -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/xlsx/0.18.5/xlsx.min.js"></script>

<!-- Icons -->
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
```

**Tidak perlu npm install atau npm build!**

## 🛠️ Troubleshooting

### ❌ "Data kandidat tidak muncul"
**Solusi**:
1. Buka Developer Console (F12)
2. Periksa tab "Console" untuk error
3. Pastikan browser support ES6+
4. Clear browser cache (Ctrl+Shift+Del)

### ❌ "CV tidak terbaca"
**Penyebab & Solusi**:
- PDF: Gunakan PDF normal (bukan scanned image) → Re-save dengan "Export as PDF"
- DOCX: Buka di Word, save ulang sebagai .docx
- Size: Pastikan <10MB

### ❌ "API Key gagal"
**Periksa**:
1. API Key format: Harus mulai `gsk_`
2. API Key valid: Test di https://console.groq.com
3. Internet connection: Pastikan stabil
4. Browser allow CORS: Groq API support CORS

### ❌ "Export Excel tidak bekerja"
**Solusi**:
1. Pastikan sudah ada hasil analisis
2. Download manager aktif (check browser download settings)
3. File akan otomatis download ke folder "Downloads"

## 📚 File Structure (untuk GitHub)

```
cv-matching-ats/
├── cv_matching_ats.html      ← Main file (buka ini di browser)
├── README.md                  ← Dokumentasi (file ini)
├── LICENSE                    ← MIT License (optional)
└── .gitignore                ← Ignore files (optional)
```

**Hanya 1 file HTML yang dibutuhkan!** Semua CSS dan JavaScript sudah embedded.

## 🎨 Customization

### Ubah Warna Tema
Edit CSS variables di `<style>`:
```css
:root {
    --primary: #1e3c72;           /* Warna utama */
    --primary-light: #2a5298;     /* Warna terang */
    --success: #10b981;           /* Warna sukses */
    --danger: #ef4444;            /* Warna error */
    /* ... dll */
}
```

### Tambah Major Keyword
Cari di JavaScript `parseCV()`:
```javascript
let majors = [
    'teknik sipil',
    'akuntansi',
    'manajemen',
    // Tambah di sini:
    'custom major'
];
```

### Ubah Model Groq
Cari `scoreWithGroq()`, ubah:
```javascript
model: 'llama-3.3-70b-versatile'  // Ganti dengan model Groq lain
```

## 📞 Support & Issues

- **Bug Report**: Buka Issue di GitHub
- **Feature Request**: Discussion di GitHub
- **Documentation**: Lihat README ini
- **API Issues**: Contact Groq support (groq.com)

## 📄 License

MIT License - Bebas digunakan, modifikasi, dan distribusi

## 🎯 Roadmap (Future)

- [ ] Batch processing dari folder
- [ ] Scoring customization per requirement
- [ ] Email results automation
- [ ] Dark mode toggle
- [ ] Multi-language support (EN, ID)
- [ ] Database integration (optional)

## 🙌 Credits

- **Groq API**: AI-powered CV analysis
- **PDF.js**: PDF reading
- **Mammoth.js**: DOCX reading  
- **XLSX**: Excel export
- **Font Awesome**: Icons

---

**Version**: 1.0  
**Last Updated**: 2025  
**Built for**: HR & Recruitment Teams

Enjoy! 🚀
