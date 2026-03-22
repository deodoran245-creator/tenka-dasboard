# 📋 PANDUAN LENGKAP API CONFIGURATION DASHBOARD

## 🎯 APA ITU API CONFIGURATION?

API Configuration adalah **pengaturan koneksi** antara Dashboard Web dengan Bot WhatsApp Anda. Tanpa konfigurasi ini, dashboard tidak bisa:
- ✅ Mengontrol bot (start/stop/restart)
- ✅ Melihat status bot
- ✅ Mengelola users dan groups
- ✅ Mengakses data bot

## 🤔 MENGAPA HARUS KONFIGURASI API?

Karena dashboard dan bot adalah **2 aplikasi terpisah**:
- 🤖 **Bot**: Running di terminal/command line
- 🌐 **Dashboard**: Web interface di browser

Mereka perlu "berkomunikasi" melalui HTTP API untuk saling mengirim data.

## 📝 APA SAJA YANG PERLU DIKONFIGURASI?

### 1. **BOT_API_URL** (URL Bot)
- Jika bot running di **localhost**: `http://localhost:3000`
- Jika bot di **hosting/VPS**: `https://domain-anda.com`
- Jika bot di **Railway/Heroku**: `https://nama-app-anda.herokuapp.com`

### 2. **BOT_API_KEY** (API Key)
- Default: `alip-ai`
- Lokasi: `settings.js` line 29: `global.botSecretKey = "alip-ai"`

### 3. **DASHBOARD_PASSWORD** (Password Login)
- Password untuk login ke dashboard
- Bisa custom sesuai keinginan

## 🚀 CARA MENDAPATKAN KONFIGURASI API

### **METODE 1: Otomatis dari Bot (TIDAK ADA)**
❌ **TIDAK ADA** command khusus di bot untuk generate API config.
Bot tidak punya fitur auto-generate konfigurasi dashboard.

### **METODE 2: Manual Setup (YANG BENAR)**

#### **Step 1: Cek Bot Sedang Running**
```bash
# Pastikan bot aktif dan port 3000 terbuka
node index.js
# atau
npm start
```

#### **Step 2: Cek BOT_API_KEY**
Buka file `settings.js`:
```javascript
// Line 29 di settings.js
global.botSecretKey = "alip-ai"  // ← Ini BOT_API_KEY
```

#### **Step 3: Tentukan BOT_API_URL**
- **Local**: `http://localhost:3000`
- **Hosting**: `https://domain-anda.com`
- **Railway**: `https://nama-app-railway.up.railway.app`

#### **Step 4: Setup di Dashboard**

**Opsi A: Via Login Page**
1. Buka dashboard login
2. Klik tombol **"⚙️ Setup"** (pojok kanan bawah)
3. Isi:
   - **API Base URL**: `http://localhost:3000/api`
   - **Dashboard Password**: `passwordmu`
   - **Confirm Password**: `passwordmu`

**Opsi B: Via Dashboard Settings**
1. Login ke dashboard
2. Pergi ke menu **"Settings"**
3. Bagian **"API Configuration"**
4. Isi **API Key** field
5. Klik **"Regenerate"** jika perlu

## 📋 CONTOH KONFIGURASI LENGKAP

### **Untuk Bot Local:**
```
BOT_API_URL=http://localhost:3000
BOT_API_KEY=alip-ai
DASHBOARD_PASSWORD=admin123
```

### **Untuk Bot Hosting:**
```
BOT_API_URL=https://bot-tenka-md.herokuapp.com
BOT_API_KEY=alip-ai
DASHBOARD_PASSWORD=kingpaiz123
```

## 🔧 CARA MENGECEK KONFIGURASI BERHASIL

### **Test 1: Bot API Reachable**
Buka browser: `http://localhost:3000/api/status`
- ✅ Berhasil: Return JSON data
- ❌ Gagal: Connection refused / timeout

### **Test 2: Dashboard Connection**
1. Login dashboard
2. Cek menu **"Bot Control"**
3. Klik **"Check Status"**
- ✅ Berhasil: Status bot muncul
- ❌ Gagal: Error connection

### **Test 3: Bot Control**
1. Di dashboard **"Bot Control"**
2. Klik **"Start Bot"** / **"Stop Bot"**
- ✅ Berhasil: Bot merespon
- ❌ Gagal: No response

## 🆘 TROUBLESHOOTING

### **Error: "Connection Failed"**
- ✅ Cek bot sedang running
- ✅ Cek port 3000 tidak blocked
- ✅ Cek BOT_API_URL benar
- ✅ Cek BOT_API_KEY match dengan settings.js

### **Error: "Invalid API Key"**
- ✅ Pastikan BOT_API_KEY = "alip-ai" (default)
- ✅ Cek tidak ada spasi di sekitar value

### **Error: "Port Already in Use"**
- ✅ Ganti port dashboard ke 3001 di .env
- ✅ Atau stop aplikasi lain yang pakai port 3000

## 📁 FILE KONFIGURASI

### **.env (Dashboard)**
```env
BOT_API_URL=http://localhost:3000
BOT_API_KEY=alip-ai
ADMIN_PASSWORD=yourpassword
```

### **settings.js (Bot)**
```javascript
global.botSecretKey = "alip-ai"  // Jangan ubah
global.dashboardPassword = "yourpassword"
```

## 🎯 RINGKASAN

1. **API Configuration** = Koneksi dashboard ↔ bot
2. **Wajib setup** agar dashboard bisa kontrol bot
3. **Tidak ada auto-generate** dari bot
4. **Manual setup** via dashboard login atau settings
5. **BOT_API_KEY** = "alip-ai" (default di settings.js)
6. **BOT_API_URL** = tergantung di mana bot running

---
📞 **Butuh bantuan?** Setup step by step atau ada error?</content>
<parameter name="filePath">c:\Users\Administrator\Videos\Bot gabung sc terbaru\alip v10.5.0\web dashboard\API_CONFIGURATION_GUIDE.md