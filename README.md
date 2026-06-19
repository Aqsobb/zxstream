# AQSO STREAM NEXUS - ARCHITECTURE DOCUMENTATION

Aplikasi web frontend ini dikonstruksi menggunakan arsitektur **Single Page Application (SPA)** murni ber-framework Tailwind CSS, yang dikhususkan untuk berpasangan secara asinkronus bersama backend scraper **DEVNEXUS OMNI-ENGINE V6**.

## 🚀 CARA DEPLOY KE VERCEL (INSTAN)
1. Buat folder baru di komputer/HP Anda, masukkan file `index.html` di atas ke dalam folder tersebut.
2. Inisialisasi Git, buat repositori baru di GitHub, dan unggah file `index.html` tersebut.
3. Buka dashboard [Vercel](https://vercel.com), klik **Add New Project**, lalu impor repositori GitHub tersebut.
4. Klik **Deploy**. Selesai! Web Anda langsung aktif dengan domain HTTPS gratis (.vercel.app).

---

## 🔥 PANDUAN MENGHUBUNGKAN KE DATABASE FIREBASE (MIGRASI DARI DEMO MODE)

Web ini memiliki modul `app.state` terpusat yang saat ini berjalan di mode *Local Storage Device* (Mode Demo). Untuk merubahnya menjadi tingkat industri berbasis cloud database Firebase, ikuti instruksi berikut:

### LANGKAH 1: Masukkan SDK Firebase di Tag `<head>`
Buka `index.html`, pasang script Firebase App dan Firestore/Auth SDK tepat di atas tag penutup `</head>`:

```html
<script src="[https://www.gstatic.com/firebasejs/9.22.0/firebase-app-compat.js](https://www.gstatic.com/firebasejs/9.22.0/firebase-app-compat.js)"></script>
<script src="[https://www.gstatic.com/firebasejs/9.22.0/firebase-auth-compat.js](https://www.gstatic.com/firebasejs/9.22.0/firebase-auth-compat.js)"></script>
<script src="[https://www.gstatic.com/firebasejs/9.22.0/firebase-firestore-compat.js](https://www.gstatic.com/firebasejs/9.22.0/firebase-firestore-compat.js)"></script>
<script>
  // Isikan konfigurasi Credentials dari Web Console Firebase Anda
  const firebaseConfig = {
    apiKey: "AIzaSyAxxxx-xxxxxxxxxxxxxx",
    authDomain: "aqso-stream-nexus.firebaseapp.com",
    projectId: "aqso-stream-nexus",
    storageBucket: "aqso-stream-nexus.appspot.com",
    messagingSenderId: "1234567890",
    appId: "1:123456:web:abcd1234efgh"
  };
  firebase.initializeApp(firebaseConfig);
  const db = firebase.firestore();
  const auth = firebase.auth();
</script>
