# SIMONI - Sistem Monitoring Imunisasi Lombok Tengah

![SIMONI Logo](https://img.shields.io/badge/SIMONI-Immunization%20Monitoring-blue?style=for-the-badge)

Sistem monitoring imunisasi berbasis web untuk Dinas Kesehatan Kabupaten Lombok Tengah, Nusa Tenggara Barat. Aplikasi ini menyediakan manajemen pasien, penjadwalan imunisasi, pelaporan, dan administrasi sistem dengan kontrol akses berbasis peran.

## 🚀 Fitur Utama

- **🔐 Sistem Autentikasi Multi-Peran**: Admin, Dokter, dan Pasien
- **📊 Dashboard Real-time**: Statistik dan grafik interaktif
- **👥 Manajemen Pasien**: CRUD lengkap dengan pencarian dan filter
- **📅 Kalender Imunisasi**: Penjadwalan dan tracking interaktif
- **📈 Sistem Pelaporan**: Export Excel/PDF dengan berbagai filter
- **⚙️ Panel Admin**: Manajemen pengguna dan konfigurasi sistem

## 🛠️ Teknologi yang Digunakan

### Frontend
- **React 18** dengan TypeScript
- **Tailwind CSS** untuk styling
- **shadcn/ui** untuk komponen UI
- **TanStack Query** untuk state management
- **Chart.js** untuk visualisasi data
- **Wouter** untuk routing

### Backend
- **Express.js** dengan TypeScript
- **bcrypt** untuk enkripsi password
- **express-session** untuk manajemen sesi
- **Drizzle ORM** untuk schema database
- **Zod** untuk validasi data

## 📋 Prasyarat

Pastikan Anda memiliki software berikut terinstall:

- **Node.js** (versi 18 atau lebih baru)
- **npm** atau **yarn**
- **Visual Studio Code** (versi terbaru)
- **Git**

## 🚀 Instalasi dan Menjalankan Aplikasi

### 1. Clone Repository

```bash
git clone https://github.com/username/simoni-lombok-tengah.git
cd simoni-lombok-tengah
```

### 2. Install Dependencies

```bash
npm install
```

### 3. Jalankan Aplikasi

```bash
npm run dev
```

Aplikasi akan berjalan di `http://localhost:5000`

## 📱 Cara Menggunakan

### Login Sistem

Akses aplikasi melalui browser dan gunakan kredensial sesuai peran:

- **Administrator**: Akses penuh ke seluruh sistem
- **Dokter**: Manajemen pasien, jadwal, dan laporan
- **Pasien**: Melihat dashboard dan jadwal imunisasi

### Navigasi Sistem

1. **Dashboard**: Statistik real-time dan aktivitas terbaru
2. **Manajemen Pasien**: Tambah, edit, cari pasien
3. **Kalender**: Jadwal imunisasi dan appointment
4. **Laporan**: Generate dan export laporan
5. **Admin Panel**: Manajemen pengguna (khusus admin)

## 🏗️ Struktur Project

```
simoni-lombok-tengah/
├── client/                 # Frontend React app
│   ├── src/
│   │   ├── components/     # Komponen UI reusable
│   │   ├── pages/          # Halaman aplikasi
│   │   ├── hooks/          # Custom React hooks
│   │   ├── lib/            # Utilities dan konfigurasi
│   │   └── ...
│   └── index.html
├── server/                 # Backend Express app
│   ├── index.ts           # Entry point server
│   ├── routes.ts          # API routes
│   ├── storage.ts         # Data layer
│   └── vite.ts            # Vite configuration
├── shared/                # Shared types dan schema
│   └── schema.ts          # Database schema
├── package.json
└── README.md
```

## 🔧 Development

### Menjalankan dalam Mode Development

```bash
npm run dev
```

### Build untuk Production

```bash
npm run build
```

### Type Checking

```bash
npm run type-check
```

## 🛠️ Konfigurasi Visual Studio Code

### Extensions yang Disarankan

Install extensions berikut untuk pengalaman development yang optimal:

1. **TypeScript and JavaScript Language Features** (built-in)
2. **ES7+ React/Redux/React-Native snippets**
3. **Tailwind CSS IntelliSense**
4. **Auto Rename Tag**
5. **Bracket Pair Colorizer**
6. **GitLens**

### Settings VSCode

Buat file `.vscode/settings.json`:

```json
{
  "typescript.preferences.importModuleSpecifier": "relative",
  "editor.formatOnSave": true,
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "tailwindCSS.includeLanguages": {
    "typescript": "typescript",
    "typescriptreact": "typescriptreact"
  },
  "files.associations": {
    "*.css": "tailwindcss"
  }
}
```

### Launch Configuration

Buat file `.vscode/launch.json` untuk debugging:

```json
{
  "version": "0.2.0",
  "configurations": [
    {
      "name": "Launch via NPM",
      "request": "launch",
      "runtimeArgs": ["run", "dev"],
      "runtimeExecutable": "npm",
      "skipFiles": ["<node_internals>/**"],
      "type": "node",
      "console": "integratedTerminal"
    }
  ]
}
```

## 📊 Database Schema

Aplikasi menggunakan in-memory storage dengan schema sebagai berikut:

### Users
- id, username, password, name, role, isActive, lastLogin, createdAt

### Patients  
- id, name, nik, birthDate, address, phoneNumber, parentName, status

### Immunizations
- id, patientId, vaccineType, scheduledDate, actualDate, status, notes, administeredBy

### Activities
- id, type, description, patientId, userId, createdAt

## 🔒 Keamanan

- Password di-hash menggunakan bcrypt
- Session-based authentication
- Role-based access control
- Input validation dengan Zod
- CSRF protection ready

## 🌐 Deployment

### Environment Variables

Buat file `.env` untuk production:

```env
NODE_ENV=production
SESSION_SECRET=your-secret-session-key
PORT=5000
```

### Docker Support (Opsional)

```dockerfile
FROM node:18-alpine
WORKDIR /app
COPY package*.json ./
RUN npm ci --only=production
COPY . .
RUN npm run build
EXPOSE 5000
CMD ["npm", "start"]
```

## 🤝 Kontribusi

1. Fork repository
2. Buat feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit perubahan (`git commit -m 'Add some AmazingFeature'`)
4. Push ke branch (`git push origin feature/AmazingFeature`)
5. Buat Pull Request

## 📝 License

Distributed under the MIT License. See `LICENSE` for more information.

## 👥 Tim Pengembang

- **Developer**: Sistem dikembangkan untuk Dinas Kesehatan Lombok Tengah
- **Contact**: admin@dinkes-loteng.go.id

## 🆘 Troubleshooting

### Error: Cannot find module

```bash
rm -rf node_modules package-lock.json
npm install
```

### Port sudah digunakan

```bash
# Cek process yang menggunakan port 5000
lsof -ti:5000
# Kill process
kill -9 $(lsof -ti:5000)
```

### TypeScript errors

```bash
npm run type-check
```

## 📞 Support

Jika mengalami masalah atau memiliki pertanyaan:

1. Cek bagian [Troubleshooting](#🆘-troubleshooting)
2. Buat issue di GitHub repository
3. Hubungi tim pengembang

---

**SIMONI** - Membantu monitoring imunisasi yang lebih efektif untuk kesehatan masyarakat Lombok Tengah 🏥💉