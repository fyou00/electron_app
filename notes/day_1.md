## Electron.js — Day 1

### Fundamentals

> Target: memahami konsep dasar Electron, struktur project, Main Process, BrowserWindow, dan bagaimana HTML ditampilkan sebagai aplikasi desktop.

---

## 1. Apa itu Electron?

1. Apa itu Electron.js menurut pemahaman lu sendiri?
**Jawaban:** electron adalah framework javascript open source yang bertujuan untuk membuat aplikasi desktop berbasis website dengan html, css, dan js

---

2. Electron menggunakan dua teknologi utama untuk menjalankan aplikasi desktop. Apa saja?
**Jawaban:** chromium dan nodejs

---

3. Apa fungsi Chromium di Electron?
**Jawaban:** chromium berfungsi untuk mengatur antarmuka aplikasi yang akan dibangun

---

4. Apa fungsi Node.js di Electron?
**Jawaban:** sedangkan nodejs berfungsi untuk menangani  proses backend seperti mengatur logika aplikasi, memberi akses ke os, pembuatan window, basis data, dll

---

5. Menurut lu, apa perbedaan utama aplikasi Electron dengan website yang dibuka menggunakan Chrome?
**Jawaban:** menurutku lebih ke bagian tingkat akses ke komputer langsung, kalo web aksesnya terbatas hanya seperti kamera, mic, localstorage. sedangkan electron dapat read/write file ke harddisk secara bebas, modifikasi sistem file, dan mengakses notifikasi

---

## 2. Project Electron Pertama

Misalnya kita mempunyai struktur:

```text
electron-hello-world/
├── node_modules/
├── index.html
├── main.js
├── package.json
└── package-lock.json
```

6. Apa fungsi `package.json`?
**Jawaban:** setau ku package json itu kayak ktp suatu project, jadi fungsinya itu sebagai file konfigurasi project yang berisi informasi metadata, script, serta mengatur dependensi atau daftar library yang dibutuhkan untuk aplikasi. sama hal nya kayak pubspec.yaml di flutter.

---

7. Apa fungsi `node_modules`?
**Jawaban:** direktori atau folder templat menyimpan semua library, dependencies, packages, yang di unduh melalui npm (package manager). contoh npm install vite, maka vite akan tersimpan dalam node_modules.

---

8. Apa fungsi `package-lock.json`?
**Jawaban:**  file yang otomatis dibuat saat menginstall dependencies node js, sebagai catatan snapshot versi spesifik paket yang di install.

---

9. File apa yang menjadi entry point aplikasi Electron jika `package.json` berisi:
    ```json
    {
        "main": "main.js"
    }
    ```
    **Jawaban:** yang akan menjadi entry point aplikasi electron adalah file yang menjadi value dari key "main". pada contoh diatas maka file main.js adalah entry point nya. 

---

## 3. Main Process

Perhatikan kode berikut:

```js
const { app, BrowserWindow } = require("electron");

function createWindow() {
    const win = new BrowserWindow({
        width: 800,
        height: 600
    });

    win.loadFile("index.html");
}

app.whenReady().then(() => {
    createWindow();
});
```

10. Apa yang dimaksud dengan **Main Process**?
**Jawaban:** kode utama yang berfungsi sebagai entry point untuk seluruh aplikasi. kode/file ini adalah yang pertama dijalankan saat aplikasi dibuka.

---

11. Apa fungsi `app`?
**Jawaban:** mengontrol event lifecycle dari aplikasi. contohnya seperti saat aplikasi siap app.whenReady(), ketika window ditutup, atau saat aplikasi keluar app.Quit(). bisa dibilang juga yang mengurus sistem secara keseluruhan mulai dari buka sampai tutup aplikasi. 

---

12. Apa fungsi `BrowserWindow`?
**Jawaban:** untuk membuat, menampilkan, kelola window/jendela aplikasi.

---

13. Apa yang dilakukan kode berikut?
    ```js
    const { app, BrowserWindow } = require("electron");
    ```
    **Jawaban:** kode tersebut melakukan import module app dan BrowserWindow

---

14. Apa fungsi `createWindow()` pada kode tersebut?
**Jawaban:** function createWindow() berfungsi untuk membuat/memunculkan window pertama saat aplikasi dijalankan

---

15. Apa yang terjadi ketika kode berikut dijalankan?
    ```js
    new BrowserWindow({
        width: 800,
        height: 600
    });
    ```
    **Jawaban:** akan membuat BrowserWindow berukuran 800x600 px. disimpan dalam const win

---

## 4. BrowserWindow

Perhatikan:

```js
const win = new BrowserWindow({
    width: 800,
    height: 600
});
```

16. Apa arti `width: 800`?
**Jawaban:** lebar jendela adalah 800 px, x axis.

---

17. Apa arti `height: 600`?
**Jawaban:** tinggi jendela adalah 600 px, y axis.

---

18. Coba ubah window menjadi ukuran: `1200 × 800`. Tuliskan kode JavaScript-nya.

    **Jawaban:**
    ```js
    new BrowserWindow({
      width: 1200,
      height: 800
    })
    ```
    
---

19. Menurut lu, kenapa Electron menggunakan `BrowserWindow` untuk membuat aplikasi desktop?
**Jawaban:** karena modul ini bisa membuat teknologi web seperti html, css, js dapat berjalan di dalam bentuk desktop app.

---

## 5. Menampilkan HTML

Perhatikan:

```js
win.loadFile("index.html");
```

20. Apa fungsi `loadFile()`?
**Jawaban:** function loadFile() memanggil file output lokal dalam format html untuk ditampilkan di aplikasi 

---

21. File apa yang akan ditampilkan oleh kode tersebut?
**Jawaban:** index.html

---

22. Jika file HTML bernama `home.html`
    bagaimana cara mengubah kode agar Electron menampilkan file tersebut?
**Jawaban:** tinggal mengubah parameter di dalam function loadFile() sesuai dengan file yang dituju
    ```js
    win.loadFile("home.html")
    ```

---

23. Apakah `index.html` merupakan Main Process atau Renderer?
**Jawaban:** index.html bukan merupakan main process, tetapi dia adalah renderer. fungsinya untuk menampilkan interface ke aplikasi mirip web biasa.

---

## 6. app.whenReady()

Perhatikan:

```js
app.whenReady().then(() => {
    createWindow();
});
```

24. Menurut lu, apa maksud dari `app.whenReady()`?

**Jawaban:**

---

25. Kenapa kita tidak langsung menjalankan:

```js
createWindow();
```

tanpa `app.whenReady()`?

**Jawaban:**

---

26. Apa yang dilakukan `.then()` pada kode:

```js
app.whenReady().then(() => {
    createWindow();
});
```

**Jawaban:**

---

## 7. Alur Program

Perhatikan kode lengkap:

```js
const { app, BrowserWindow } = require("electron");

function createWindow() {
    const win = new BrowserWindow({
        width: 800,
        height: 600
    });

    win.loadFile("index.html");
}

app.whenReady().then(() => {
    createWindow();
});
```

27. Urutkan kejadian berikut dari awal sampai akhir:

```text
[ ] BrowserWindow dibuat
[ ] Electron dijalankan
[ ] index.html dimuat
[ ] app menjadi ready
[ ] createWindow() dipanggil
```

**Jawaban:**

```text
1.
2.
3.
4.
5.
```

---

28. Gambarkan alur program tersebut menggunakan diagram sederhana.

**Jawaban:**

```text
```

---

## 8. Eksperimen

Sekarang jangan cuma baca. Ubah kode dan lihat hasilnya.

#### Eksperimen 1

Buat window berukuran:

```text
1000 × 700
```

Kode:

```js
```

---

#### Eksperimen 2

Buat HTML berikut:

```html
<h1>Hello Electron</h1>
<p>Saya sedang belajar Electron.</p>
```

Kemudian tampilkan melalui `BrowserWindow`.

**Jawaban:**

---

#### Eksperimen 3

Ubah teks HTML menjadi sesuatu yang lu mau.

**Hasil:**

---

## 9. Pertanyaan Konsep

Jawab menggunakan bahasa lu sendiri.

29. Apakah Electron termasuk framework JavaScript?
**Jawaban:** iya, electron adalah framework javascript untuk membangun aplikasi desktop cross platform meggunakan teknologi web (html, css, js)

---

30. Apakah Electron bisa menggunakan HTML dan CSS?
**Jawaban:** jelas bisa

---

31. Apakah Electron hanya bisa membuat aplikasi untuk Windows?
**Jawaban:** tidak, electron bisa juga untuk macos dengan flag --platform=darwin dan juga untuk linux dengan flag --platform=linux. windows --platform=win32

---

32. Apa hubungan antara JavaScript, Node.js, Chromium, dan Electron?
**Jawaban:**

---

33. Kalau website biasa berjalan di browser, sedangkan Electron berjalan sebagai aplikasi desktop, menurut lu bagaimana Electron bisa menampilkan HTML?
**Jawaban:** dengan kerja sama chromium dan node js. chromium lah yang berperan dalam menampilkan html ke jendela aplikasi, sedangkan node js untuk mengelola proses (akses sistem operasi)

---

## 10. Tantangan

Jangan lihat tutorial. Coba buat sendiri.

Buat aplikasi Electron dengan ketentuan:

```text
Window:
- Width: 1000
- Height: 700

HTML:
- Judul: "My First Electron App"
- Paragraf berisi nama lu
- Satu tombol bertuliskan "Click Me"
```

Struktur:

```text
my-electron-app/
├── main.js
├── index.html
├── package.json
└── node_modules/
```

#### Tulis kode `main.js`

```js
```

#### Tulis kode `index.html`

```html
```

---

## 11. Self Check

Setelah selesai, kasih tanda:

* [x] Gw tahu apa itu Electron.
* [x] Gw tahu fungsi Chromium dalam Electron.
* [x] Gw tahu fungsi Node.js dalam Electron.
* [x] Gw tahu apa itu Main Process.
* [x] Gw tahu fungsi `app`.
* [x] Gw tahu fungsi `BrowserWindow`.
* [x] Gw tahu fungsi `loadFile()`.
* [ ] Gw tahu fungsi `app.whenReady()`.
* [ ] Gw bisa membuat window Electron sendiri.
* [ ] Gw bisa menampilkan HTML dari Electron.
* [ ] Gw bisa menjelaskan alur `main.js → BrowserWindow → index.html`.

---

## 🎯 Day 1 Challenge

Tanpa melihat contoh sebelumnya, buat dari folder kosong:

```text
electron-day-1/
```

Target:

```text
npm start
      ↓
Electron membuka window
      ↓
Window menampilkan HTML
      ↓
HTML berisi:
"Hello World!"
"Electron Day 1"
```

Kalau berhasil tanpa copy-paste, berarti fondasi Day 1 lu sudah aman.

---

### Catatan Bebas

Tulis hal yang masih bikin bingung:

```text
```

Tulis konsep yang baru lu pahami hari ini:

```text
Electron mengikuti konvensi JavaScript yang umum dalam hal ini, di mana modul dengan notasi PascalCase merupakan konstruktor kelas yang dapat diinstansiasi (misalnya `BrowserWindow`, `Tray`, `Notification`), sedangkan modul dengan notasi camelCase tidak dapat diinstansiasi (misalnya `app`, `ipcRenderer`, `webContents`).
```

Tulis pertanyaan yang muncul setelah latihan:

```text
```
