
#  BinusGO!

**Transit Cerdas Menuju Kampus BINUS**


Smart transit planner berbasis web untuk membantu sivitas akademika BINUS University menemukan rute angkutan umum terbaik menuju kampus di wilayah Jabodetabek.
Mengagregasi data **TransJakarta**, **KRL Commuterline**, **LRT Jabodebek**, dan **Mikrotrans** dalam satu platform.


</div>

---

## 📋 Daftar Isi

- [Tentang Proyek](#-tentang-proyek)
- [Fitur Utama](#-fitur-utama)
- [Tech Stack](#-tech-stack)
- [Struktur Proyek](#-struktur-proyek)
- [Cara Menjalankan](#-cara-menjalankan)
- [Akun Demo](#-akun-demo)
- [Status Pengembangan](#-status-pengembangan)
- [Kontribusi Tim](#-kontribusi-tim)
- [Panduan Kontribusi](#-panduan-kontribusi)

---

## 🏫 Tentang Proyek

BinusGO! adalah proyek **PKM-KC (Program Kreativitas Mahasiswa – Karya Cipta)** yang dikembangkan oleh mahasiswa Jurusan Cyber Security BINUS University. Aplikasi ini hadir untuk menjawab permasalahan nyata yang dialami sivitas akademika BINUS: sulitnya menemukan rute angkutan umum yang optimal dari lokasi masing-masing menuju kampus Binus Greater Jakarta.

**Mengapa BinusGO!?**

- 🗺️ Google Maps tidak memiliki konteks spesifik kampus BINUS (titik *drop-off* terdekat ke gerbang, jadwal aktual moda)
- 🚌 Informasi KRL, Transjakarta, dan Mikrotrans tersebar di platform berbeda
- ⏰ Tidak ada rekomendasi yang mempertimbangkan jam sibuk dengan jam normal secara kontekstual

BinusGO! menyatukan semua informasi tersebut dalam satu antarmuka yang sederhana dan aman.

---

## ✨ Fitur Utama

| Fitur | Deskripsi | Status |
|---|---|---|
| Route Planner | Input lokasi asal → rekomendasi rute multi-moda ke kampus tujuan | ✅ MVP |
| Peta Interaktif | Visualisasi rute, marker kampus, dan halte via Leaflet | ✅ MVP |
| Auth (JWT) | Register, login, httpOnly cookie + Bearer token | ✅ MVP |
| Saved Locations | Simpan lokasi favorit pengguna (auth-gated) | ✅ MVP |
| Trip History | Riwayat pencarian rute otomatis tercatat (auth-gated) | ✅ MVP |
| Admin Dashboard | Statistik penggunaan + visualisasi Recharts | ✅ MVP |
| Admin CRUD | Manajemen kampus, rute, pengguna, laporan, activity log | 🔧 TODO |
| OAuth | Login via Google / Microsoft | 🔧 TODO |
| Real-time Routing | Integrasi API rute real-time (GTFS live feed) | 🔧 TODO |

---

## 🛠️ Tech Stack

### Frontend
| Teknologi | Versi | Kegunaan |
|---|---|---|
| React | 18 | UI framework |
| Vite | 5 | Build tool & dev server |
| Tailwind CSS | 3 | Utility-first styling |
| React Router | v6 | Client-side routing |
| Leaflet / React-Leaflet | - | Peta interaktif |
| Recharts | - | Visualisasi data (dashboard) |
| Lucide React | - | Icon library |

### Backend
| Teknologi | Versi | Kegunaan |
|---|---|---|
| Node.js | 18+ | Runtime environment |
| Express | 4 | Web framework |
| MongoDB | 7 | Database utama |
| Mongoose | - | ODM / schema modeling |
| JWT + bcrypt | - | Autentikasi & enkripsi password |

---

## 📁 Struktur Proyek

```
BinusGO/
├── client/                  # React (Vite) — Frontend
│   ├── src/
│   │   ├── components/      # Komponen UI reusable
│   │   ├── pages/           # Halaman (Landing, Planner, History, dll.)
│   │   ├── hooks/           # Custom React hooks
│   │   ├── services/        # API calls ke backend
│   │   └── utils/           # Helper functions
│   ├── public/
│   └── package.json
│
├── server/                  # Express + MongoDB — Backend
│   ├── controllers/         # Logic handler per route
│   ├── models/              # Mongoose schema (User, Route, Campus)
│   ├── routes/              # Endpoint definitions
│   ├── middleware/          # Auth, error handler, rate limiter
│   ├── seed/                # Seed data kampus & rute
│   ├── .env.example
│   └── package.json
│
└── README.md
```

---

## 🚀 Cara Menjalankan

### Prasyarat

Pastikan kamu sudah menginstal:
- [Node.js](https://nodejs.org) v18 atau lebih baru
- [MongoDB](https://mongodb.com) (lokal atau MongoDB Atlas)
- `npm` atau `yarn`

### 1. Clone Repository

Ketik cmd pada File BinusGO!

```bash
git clone https://github.com/<username>/BinusGO.git
cd BinusGO
```

### 2. Setup Backend

Buka terminal pada VSCode

```bash
cd server
npm install

# Salin file konfigurasi environment
cp .env.example .env
```

Edit file `.env` dan isi variabel berikut:

```env
MONGO_URI=mongodb://localhost:27017/binusgo
JWT_SECRET=your_jwt_secret_here
PORT=5000
```

```bash
# Seed data awal (kampus + rute)
npm run seed

# Jalankan server (port 5000)
npm run dev
```

### 3. Setup Frontend

Buka Terminal baru lagi pada VSCode

```bash
# Buka terminal baru
cd client
npm install

# Jalankan dev server (port 5173)
npm run dev
```

### 4. Buka Aplikasi

```
http://localhost:5173
```

---

## 🔑 Akun Demo

Tersedia setelah menjalankan `npm run seed` di direktori `server`.

| Role | Email | Password |
|---|---|---|
| Admin | `admin@binus.edu` | `admin123` |
| Student | `student@binus.ac.id` | `student123` |

> ⚠️ **Catatan keamanan:** Ganti kredensial default sebelum deployment ke lingkungan produksi.

---

## 📊 Status Pengembangan

```
[■■■■■■■■░░] 80% — MVP selesai, integrasi real-time API dalam pengerjaan
```

- [x] Proposal & perencanaan sistem
- [x] Desain UI/UX (wireframe → high-fidelity prototype)
- [x] Pengembangan MVP (frontend + backend)
- [x] Integrasi data statis (kampus, rute, halte)
- [ ] Integrasi API real-time (GTFS live, Transjakarta)
- [ ] User testing dengan sivitas akademika BINUS
- [ ] Deployment publik

---

## 👥 Kontribusi Tim

Proyek ini dikembangkan oleh mahasiswa **Jurusan Cyber Security, BINUS University** sebagai bagian dari PKM-KC 2025/2026.

| Nama | NIM | Peran | Kontribusi |
|---|---|---|---|
| Shinji Prudent Zhang | 2802402104 | Project Manager & Backend Lead | Arsitektur sistem, routing engine, koordinasi tim |
| Aryo Bismo Kuntjoro Jakti | 2802414161 | Frontend Developer | UI/UX, React components, Leaflet map integration |
| Dominick Jovan Hilman | 2802392305 | Data & API Engineer | Integrasi API, database schema, seed data |
| Akraam Misbah Hidayatullah | 2802420473 | Riset & Dokumentasi | Proposal PKM-KC, riset pasar, laporan kemajuan |

**Dosen Pembimbing:** [Dwi Nurmelly Handayani, S.Kom., MTI], [D6320]

---

## 🤝 Panduan Kontribusi

Kontribusi sangat kami sambut! Ikuti langkah berikut:

### Mengajukan Pull Request

```bash
# 1. Fork repository ini
# 2. Buat branch fitur baru
git checkout -b feat/nama-fitur

# 3. Commit perubahan dengan format konvensional
git commit -m "feat: tambah fitur notifikasi gangguan KRL"

# 4. Push ke branch kamu
git push origin feat/nama-fitur

# 5. Buka Pull Request ke branch main
```

### Konvensi Commit

| Prefix | Kegunaan |
|---|---|
| `feat:` | Fitur baru |
| `fix:` | Perbaikan bug |
| `docs:` | Perubahan dokumentasi |
| `style:` | Formatting, tanpa perubahan logika |
| `refactor:` | Refactoring kode |
| `test:` | Penambahan atau perbaikan tes |
| `chore:` | Update dependency, konfigurasi |

### Code Style
- Gunakan **ESLint** dan **Prettier** yang sudah dikonfigurasi
- Tulis nama variabel dan komentar dalam **Bahasa Inggris**
- Setiap fitur baru wajib disertai dokumentasi singkat

---

<div align="center">

Dibuat dengan ❤️ oleh Tim BinusGO! — BINUS University, Jurusan Cyber Security

**#PKM-KC #BINUSUniversity #TransitPlanner #SmartCampus**

</div>