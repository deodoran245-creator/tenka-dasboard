# 🌐 Alip Bot Dashboard

Dashboard web standalone untuk mengelola bot WhatsApp Alip dengan fitur lengkap manajemen bot, user, dan credentials.

## ✨ Fitur Utama

- 🔐 **Authentication System** - Login dengan email/username dan password
- 📊 **Dashboard Overview** - Statistik bot dan monitoring real-time
- 👥 **User Management** - Kelola pengguna bot
- 📝 **Private Message Logs** - Monitor pesan pribadi
- 💰 **Sewa Management** - Kelola sesi sewa bot
- 👑 **Owner Management** - Kontrol akses owner
- ⚙️ **Settings** - Konfigurasi bot
- 🔑 **Credentials Management** - Ubah kredensial dashboard

## ⚡ Quick Setup (5 Menit)

### 1. **Konfigurasi Environment**
```bash
# Copy template environment
cp .env.example .env

# Edit file .env dengan text editor
nano .env  # atau gunakan editor favorit kamu
```

**Isi file .env dengan:**
```env
# Login Dashboard (bebas pilih)
ADMIN_EMAIL=dashboard@alipbot.com
ADMIN_USERNAME=admin
ADMIN_PASSWORD=alipbot2025

# Koneksi ke Bot Utama
BOT_API_URL=http://localhost:3000
BOT_API_KEY=alip-ai

# Port Dashboard
PORT=3001
```

### 2. **Install & Jalankan**
```bash
# Install dependencies
npm install

# Jalankan dashboard
npm start
```

### 3. **Akses Dashboard**
- **URL**: `http://localhost:3001`
- **Login**: Gunakan email/username/password dari file `.env`

## 📋 Penjelasan Konfigurasi

### 🔐 **ADMIN_EMAIL, ADMIN_USERNAME, ADMIN_PASSWORD**
- **Apa itu?** Kredensial untuk login ke dashboard
- **Contoh yang valid:**
  - Email: `admin@alipbot.com` atau `dashboard@gmail.com`
  - Username: `admin`, `paiz`, `kingpaiz`
  - Password: `alipbot2025`, `kingpaiz123`

### 🔗 **BOT_API_URL**
- **Apa itu?** URL bot WhatsApp utama kamu
- **Jika bot lokal**: `http://localhost:3000`
- **Jika di hosting**: `https://bot-alip.herokuapp.com`
- **Cara cek**: Bot harus sudah running dan accessible

### 🔑 **BOT_API_KEY**
- **Apa itu?** API key untuk akses bot
- **Default**: `alip-ai` (lihat di `settings.js` bot utama)
- **Lokasi**: `global.botSecretKey = "alip-ai"`

### 🔢 **PORT**
- **Apa itu?** Port untuk dashboard
- **Default**: `3001` (jangan sama dengan port bot)
- **Contoh**: `3001`, `8080`, `5000`

4. **Jalankan Dashboard**
   ```bash
   # Production
   npm start

   # Development
   npm run dev
   ```

## 🔧 Konfigurasi

### Environment Variables
- `ADMIN_EMAIL` - Email untuk login dashboard
- `ADMIN_USERNAME` - Username untuk login dashboard
- `ADMIN_PASSWORD` - Password untuk login dashboard
- `BOT_API_URL` - URL API bot utama (default: http://localhost:3000)
- `BOT_API_KEY` - API key bot utama
- `PORT` - Port server dashboard (default: 3001)

### File Structure
```
web dashboard/
├── dashboard-api.js      # Main API server
├── dashboard.html        # Main dashboard page
├── dashboard.js          # Dashboard functionality
├── dashboard.css         # Dashboard styling
├── login.html           # Login page
├── package.json         # Dependencies & scripts
├── .env                 # Environment configuration
└── README.md           # This file
```

## 🌐 Deployment

### VPS/Cloud Server
1. Upload folder ke server
2. Install Node.js dan NPM
3. Jalankan `npm install && npm start`
4. Setup reverse proxy (nginx/apache) jika perlu
5. Setup SSL certificate

### Platform Hosting
- **Railway**: Upload code, auto-deploy
- **Render**: Web service deployment
- **Vercel**: Static hosting (hanya frontend)
- **Heroku**: Git-based deployment

### Docker Deployment (Opsional)
```dockerfile
FROM node:18-alpine
WORKDIR /app
COPY package*.json ./
RUN npm ci --only=production
COPY . .
EXPOSE 3001
CMD ["npm", "start"]
```

## 🔒 Security

- ✅ Owner-only access untuk bot commands
- ✅ JWT authentication untuk API
- ✅ Input validation dan sanitization
- ✅ Password hashing (recommended)
- ✅ HTTPS recommended untuk production

## 📡 API Endpoints

### Authentication
- `POST /api/auth/login` - Login dashboard
- `POST /api/auth/logout` - Logout dashboard

### Dashboard Data
- `GET /api/dashboard/stats` - Get dashboard statistics
- `GET /api/users` - Get users list
- `GET /api/groups` - Get groups list
- `GET /api/pm-logs` - Get private message logs

### Management
- `GET /api/credentials` - Get current credentials
- `PUT /api/credentials` - Update credentials
- `GET /api/settings` - Get bot settings
- `PUT /api/settings` - Update bot settings

## 🛠️ Development

### Menambah Fitur Baru
1. Edit `dashboard-api.js` untuk API endpoints
2. Edit `dashboard.html` untuk UI
3. Edit `dashboard.js` untuk functionality
4. Edit `dashboard.css` untuk styling

### Bot Integration
Dashboard terhubung dengan bot melalui API calls ke bot utama. Pastikan:
- Bot utama running dan accessible
- API key sudah dikonfigurasi
- CORS sudah diatur dengan benar

## 📞 Support

- **YouTube**: [@alipclutch](https://youtube.com/@alipclutch)
- **Channel**: [Alip Channel](https://whatsapp.com/channel/0029VbC3jusK5cDD9mELOb18)
- **GitHub Issues**: Laporkan bug atau request fitur

## 📄 License

MIT License - bebas digunakan untuk keperluan pribadi dan komersial.

---

**Made with ❤️ by Alip Team**