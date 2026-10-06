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
**Jawaban:** setau ku package json itu kayak ktp suatu project, jadi fungsinya itu sebagai file konfigurasi project yang berisi informasi metadata, script, serta mengatur dependensi atau daftar library yang dibutuhkan untuk aplikasi. sama hal nya kayak pubspec.yaml di flutter

---

7. Apa fungsi `node_modules`?

**Jawaban:**

---

8. Apa fungsi `package-lock.json`?

**Jawaban:**

---

9. File apa yang menjadi entry point aplikasi Electron jika `package.json` berisi:

```json
{
    "main": "main.js"
}
```

**Jawaban:**

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

**Jawaban:**

---

11. Apa fungsi `app`?

**Jawaban:**

---

12. Apa fungsi `BrowserWindow`?

**Jawaban:**

---

13. Apa yang dilakukan kode berikut?

```js
const { app, BrowserWindow } = require("electron");
```

**Jawaban:**

---

14. Apa fungsi `createWindow()` pada kode tersebut?

**Jawaban:**

---

15. Apa yang terjadi ketika kode berikut dijalankan?

```js
new BrowserWindow({
    width: 800,
    height: 600
});
```

**Jawaban:**

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

**Jawaban:**

---

17. Apa arti `height: 600`?

**Jawaban:**

---

18. Coba ubah window menjadi ukuran:

```text
1200 × 800
```

Tuliskan kode JavaScript-nya.

**Jawaban:**

```js
```

---

19. Menurut lu, kenapa Electron menggunakan `BrowserWindow` untuk membuat aplikasi desktop?

**Jawaban:**

---

## 5. Menampilkan HTML

Perhatikan:

```js
win.loadFile("index.html");
```

20. Apa fungsi `loadFile()`?

**Jawaban:**

---

21. File apa yang akan ditampilkan oleh kode tersebut?

**Jawaban:**

---

22. Jika file HTML bernama:

```text
home.html
```

bagaimana cara mengubah kode agar Electron menampilkan file tersebut?

**Jawaban:**

```js
```

---

23. Apakah `index.html` merupakan Main Process atau Renderer?

**Jawaban:**

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

#### 29. Apakah Electron termasuk framework JavaScript?

**Jawaban:**

---

#### 30. Apakah Electron bisa menggunakan HTML dan CSS?

**Jawaban:**

---

#### 31. Apakah Electron hanya bisa membuat aplikasi untuk Windows?

**Jawaban:**

---

#### 32. Apa hubungan antara JavaScript, Node.js, Chromium, dan Electron?

**Jawaban:**

---

#### 33. Kalau website biasa berjalan di browser, sedangkan Electron berjalan sebagai aplikasi desktop, menurut lu bagaimana Electron bisa menampilkan HTML?

**Jawaban:**

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

* [ ] Gw tahu apa itu Electron.
* [ ] Gw tahu fungsi Chromium dalam Electron.
* [ ] Gw tahu fungsi Node.js dalam Electron.
* [ ] Gw tahu apa itu Main Process.
* [ ] Gw tahu fungsi `app`.
* [ ] Gw tahu fungsi `BrowserWindow`.
* [ ] Gw tahu fungsi `loadFile()`.
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
```

Tulis pertanyaan yang muncul setelah latihan:

```text
```
