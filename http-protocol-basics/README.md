# Fundamentals of HTTP Protocol in API Testing

Dokumen ini berisi rangkuman konsep dasar protokol HTTP, struktur anatomi request-response, metode HTTP yang sering digunakan, serta klasifikasi HTTP Status Code untuk keperluan manual API testing.

---

## 1. Anatomi HTTP Request & Response

### HTTP Request
Setiap kali Client (Postman/Browser/App) mengirimkan permintaan ke Server, request terdiri dari:
- **Request Line:** HTTP Method + Endpoint URL + HTTP Version (contoh: `GET /users HTTP/1.1`)
- **Headers:** Meta-data tambahan seperti `Content-Type: application/json`, `Authorization`, `User-Agent`.
- **Body / Payload:** Data yang dikirimkan ke server (umumnya untuk metode `POST`, `PUT`, atau `PATCH`).

### HTTP Response
Server memproses permintaan dan mengembalikan:
- **Status Line:** HTTP Version + Status Code + Reason Phrase (contoh: `HTTP/1.1 200 OK`)
- **Headers:** Meta-data dari server seperti `Content-Type`, `Date`, `Cache-Control`.
- **Response Body:** Payload balasan dari server (biasanya berupa struktur data JSON atau XML).

---

## 2. Metode HTTP (HTTP Methods / Verbs)

| HTTP Method | Fungsi Utama | Memiliki Body Request? | Idempotent? |
| :--- | :--- | :---: | :---: |
| **GET** | Mengambil data dari server | Tidak | Ya |
| **POST** | Membuat/mengirim data baru ke server | Ya | Tidak |
| **PUT** | Memperbarui seluruh data resource secara utuh | Ya | Ya |
| **PATCH** | Memperbarui sebagian data resource (parsial) | Ya | Tidak |
| **DELETE** | Menghapus data dari server | Tidak | Ya |

> **Catatan Idempotent:** Sifat di mana berapa kali pun request yang sama dikirimkan, hasil akhir di sisi server tetap bernilai sama dan tidak menimbulkan efek samping ganda.

---

## 3. Klasifikasi HTTP Status Code

### 2xx - Success (Berhasil)
- `200 OK`: Request berhasil diproses dan mengembalikan data (biasanya pada GET, PUT, PATCH).
- `201 Created`: Request berhasil dan resource baru sukses dibuat di server (biasanya pada POST).
- `204 No Content`: Request berhasil diproses tetapi server tidak mengembalikan data apa pun (biasanya pada DELETE).

### 4xx - Client Errors (Kesalahan Klien)
- `400 Bad Request`: Format payload/sintaks request salah atau ada parameter wajib yang hilang.
- `401 Unauthorized`: Klien belum melakukan autentikasi (tidak ada token atau token tidak valid).
- `403 Forbidden`: Klien sudah terautentikasi tetapi tidak memiliki hak akses (authorization) ke resource tersebut.
- `404 Not Found`: Endpoint URL atau ID resource yang dicari tidak ditemukan di server.
- `422 Unprocessable Entity`: Format payload benar, tetapi isinya melanggar aturan validasi bisnis.

### 5xx - Server Errors (Kesalahan Server)
- `500 Internal Server Error`: Ada error yang tidak tertangani di kode program server.
- `502 Bad Gateway`: Server perantara (proxy/gateway) menerima respons yang tidak valid dari server hulu.
- `503 Service Unavailable`: Server sedang *down*, *overloaded*, atau dalam pemeliharaan (maintenance).