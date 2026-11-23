# 🎓 SIAKAD Platform — Fullstack Node.js + React

SIAKAD (Sistem Informasi Akademik) Platform adalah proyek fullstack sederhana yang mengintegrasikan **Node.js (Express)** sebagai backend dan **React.js** sebagai frontend.  
Didesain sebagai fondasi sistem akademik modern yang mudah dikembangkan dan mudah dipahami oleh tim pengembang.

---

## 🚀 Fitur Utama

✅ Backend dengan Express.js (API siap dikembangkan)  
✅ Frontend dengan React.js (SPA responsif)  
✅ Integrasi otomatis frontend–backend via proxy  
✅ Struktur proyek rapi dan modular  
✅ Skrip otomatis untuk instalasi & menjalankan keduanya sekaligus  

---

## 🗂️ Struktur Direktori

```
siakad-platform/
│
├── backend/                   # Backend (Node.js + Express)
│   ├── src/
│   │   ├── routes/            # Endpoint API
│   │   ├── controllers/       # Logika bisnis
│   │   ├── models/            # Struktur data & koneksi DB
│   │   ├── config/            # File konfigurasi & environment
│   │   └── index.js           # File utama server
│   ├── package.json
│   └── .env                   # File konfigurasi (opsional)
│
├── frontend/                  # Frontend (React.js)
│   ├── src/
│   ├── public/
│   └── package.json
│
├── package.json               # Root project (berisi skrip global)
├── .gitignore
└── README.md
```

---

## ⚙️ Persiapan Awal

Pastikan kamu sudah menginstal:
- **Node.js v18+**
- **npm (Node Package Manager)**

Kemudian buka terminal di direktori proyek:

```bash
npm run install-all
```

💡 Perintah di atas akan otomatis menginstal dependency untuk:
- `/backend`
- `/frontend`

---

## ▶️ Menjalankan Proyek

Untuk menjalankan **frontend & backend secara bersamaan**, cukup jalankan:

```bash
npm run start-all
```

📍 Default Port:
- **Frontend** → http://localhost:3000  
- **Backend** → http://localhost:5000  

Semuanya akan berjalan bersamaan berkat library `concurrently`.

---

## 🧩 Menjalankan Secara Terpisah

**Backend saja:**
```bash
cd backend
npm run dev
```

**Frontend saja:**
```bash
cd frontend
npm start
```

---

## 🔗 Integrasi Frontend ⇄ Backend

Koneksi sudah otomatis melalui proxy yang ada di `frontend/package.json`:

```json
"proxy": "http://localhost:5000"
```

Contoh pengujian koneksi:

**Backend (`backend/src/index.js`):**
```js
app.get("/api/test", (req, res) => {
  res.json({ message: "Koneksi ke backend berhasil!" });
});
```

**Frontend (`frontend/src/App.js`):**
```js
import { useEffect, useState } from "react";
import axios from "axios";

function App() {
  const [msg, setMsg] = useState("");

  useEffect(() => {
    axios.get("/api/test")
      .then(res => setMsg(res.data.message))
      .catch(() => setMsg("Gagal terhubung ke backend"));
  }, []);

  return <h2 style={{ textAlign: "center" }}>{msg}</h2>;
}

export default App;
```

💬 Hasil di browser:
```
Koneksi ke backend berhasil!
```

---

## 🧹 .gitignore (Root)

```
node_modules
.env
/build
/dist
.DS_Store
*.log
```

---

## 📜 Skrip Penting di package.json (Root)

```json
"scripts": {
  "install-all": "npm install --prefix backend && npm install --prefix frontend",
  "start-all": "concurrently \"npm run dev --prefix backend\" \"npm start --prefix frontend\""
}
```

Jika `concurrently` belum terinstal:
```bash
npm install concurrently
```

---

## 👥 Panduan untuk Tim

1. Clone repository ini:
   ```bash
   git clone https://github.com/<username>/<repo-name>.git
   cd siakad-platform
   ```

2. Install semua dependency:
   ```bash
   npm run install-all
   ```

3. Jalankan proyek:
   ```bash
   npm run start-all
   ```

✨ Setelah itu, frontend dan backend akan langsung aktif dan terhubung otomatis.

---

## 💬 Kontribusi
Jika ingin berkontribusi:
1. Fork repository ini
2. Buat branch baru (`feature/fitur-baru`)
3. Commit perubahan
4. Pull request ke branch `main`

---

## 👥 Tim Developer 
| Nama | Peran |
|------|--------|
| Ananda Whisnu | Backend |
| Muhammad Julianda Nu'man | Frontend |
| Nabil Maulana | Backend |
| M Takhlis Griska Rafi | Frontend|
