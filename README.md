---
# 📦 Backend: Bill of Lading Extractor (via OpenAI GPT-4o Mini)

Proyek ini adalah backend **Flask API** untuk mengekstrak informasi penting dari file **PDF Bill of Lading**, menggunakan **OpenAI GPT-4o Mini**. Proyek ini bisa di-*upload* ke **cPanel** via ZIP dan dijalankan menggunakan **Python App** (mod\_wsgi).
---

## 📁 Struktur Folder

```
backend/
├── uploads/              # Tempat file PDF disimpan sementara
├── __pycache__/          # Cache Python (boleh dihapus)
├── app.py                # Main entry Flask app
├── .env                  # File API key OpenAI (jangan dishare publik)
├── requirements.txt      # Dependensi Python
└── README.md             # Dokumentasi ini
```

---

## 🚀 Cara Menjalankan Secara Lokal

### 1. Buat Virtual Environment

```bash
python -m venv venv
source venv/bin/activate  # Linux/Mac
venv\Scripts\activate     # Windows
```

### 2. Instal Dependency

```bash
pip install -r requirements.txt
```

### 3. Buat File `.env`

Isi file `.env` seperti berikut:

```
OPENAI_API_KEY=sk-xxxxxxxxxxxxxxxxxxxxxx
```

### 4. Jalankan

```bash
python app.py
```

Akses melalui browser di: `http://localhost:5000`

---

## 🔗 Endpoint API

### `POST /upload`

- **Deskripsi:** Upload file PDF Bill of Lading
- **Form Data:**
  `file`: PDF yang ingin diekstrak
- **Response:** JSON berisi hasil ekstraksi

#### Contoh cURL:

```bash
curl -X POST http://localhost:5000/upload \
  -F "file=@your_file.pdf"
```

---

## 🌍 Cara Hosting di cPanel

1. **Zip folder `backend/`**
2. **Upload ke cPanel > File Manager**, lalu ekstrak
3. Buka **Setup Python App** (di cPanel)

   - Python version: `3.8` atau `3.9`
   - App directory: arahkan ke folder hasil ekstrak (`/backend`)
   - Entry file: `app.py`

4. Tambahkan environment variable:

   ```
   OPENAI_API_KEY=sk-xxxxxxxxxxxxxxxxxxxxxx
   ```

5. Jalankan aplikasinya
6. Akses endpoint: `https://yourdomain.com/upload`

> Jika app tidak berjalan, pastikan `requirements.txt` sudah di-_install_ di panel Python App, atau gunakan tombol "Run pip install".

---

## ✅ Contoh File `.env.example`

```env
# Copy dan rename ke .env
OPENAI_API_KEY=your_openai_key_here
```

---

## 🧪 Requirements

### requirements.txt

```txt
Flask
flask-cors
pdfplumber
openai
python-dotenv
```

---
