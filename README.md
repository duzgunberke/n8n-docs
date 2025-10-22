## 🔧 **1. Google Cloud Console Setup**

### API'leri Aktif mi check:
```
https://console.cloud.google.com → yeni proje oluştur
APIs & Services → Library:
✅ Google Docs API
✅ Google Sheets API  
✅ Google Drive API
```

### OAuth Credential Oluştur:
```
APIs & Services → Credentials → Create Credentials → OAuth 2.0 Client ID
Application type: Web application
Name: n8n-timesheet
Authorized redirect URIs: 
http://localhost:5678/rest/oauth2-credential/callback
```
**Client ID ve Client Secret'i kaydet!**

---

## 🔑 **2. N8N'de Credentials Ekle**

### Google OAuth:
```
n8n → Settings → Credentials → Add Credential → Google OAuth2 API
Client ID: [Google Console'dan aldığın]
Client Secret: [Google Console'dan aldığın]
Scope: https://www.googleapis.com/auth/documents https://www.googleapis.com/auth/spreadsheets https://www.googleapis.com/auth/drive
```
**"Connect my account" → Google'la giriş yap**
**Credential adı: "google-oauth-credential"**

### Claude API:
```
Add Credential → Anthropic API
API Key: [anthropic.com'dan alacağın sk-ant-... anahtarı]
Credential adı: "claude-api-credential"
```

---

## 📋 **3. Doküman ID'lerini Al**

### Google Docs Oluştur:
```
docs.google.com → Yeni döküman oluştur
Örnek içerik ekle:
15/12/2024
Berke Düzgün
- Frontend geliştirme
- API entegrasyonu

URL'den ID'yi kopyala:
https://docs.google.com/document/d/1ABC123XYZ.../edit
ID: 1ABC123XYZ...
```

### Google Sheets Oluştur:
```
sheets.google.com → Yeni spreadsheet
URL'den ID'yi kopyala:
https://docs.google.com/spreadsheets/d/1XYZ789ABC.../edit
ID: 1XYZ789ABC...
```

---

## ⚙️ **4. Workflow Node'larını Güncelle**

### Read Google Docs node:
```
Credentials: google-oauth-credential seç
Doc ID or URL: [Google Docs ID'sini yapıştır]
```

### Write to Sheet node:
```
Credentials: google-oauth-credential seç  
Spreadsheet ID: [Google Sheets ID'sini yapıştır]
```

### Claude Process node:
```
Credentials: claude-api-credential seç
```

---


