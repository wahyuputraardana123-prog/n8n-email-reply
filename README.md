# AI Email Reply Workflow dengan n8n

Workflow n8n sederhana untuk membuat email dengan bantuan AI melalui chat, serta mengirimkannya menggunakan Gmail ketika diminta.

## Fitur

- Menerima instruksi melalui **When chat message received**.
- Menggunakan **AI Agent** untuk menyusun email yang singkat dan efektif.
- Menggunakan model `qwen/qwen3-32b` melalui OpenRouter.
- Menyimpan konteks percakapan dengan **Simple Memory**.
- Mengirim email melalui Gmail berdasarkan penerima, subjek, dan isi yang ditentukan AI.

## Alur kerja

```text
Chat message
    -> AI Agent
       -> OpenRouter Chat Model
       -> Simple Memory
       -> Gmail: Send a message
```

## Persyaratan

- n8n yang mendukung node LangChain dan Gmail Tool.
- Akun OpenRouter dan API key yang valid.
- Akun Google/Gmail dengan OAuth2 yang sudah terhubung ke n8n.

## Instalasi

1. Buka n8n.
2. Pilih **Import from File**.
3. Import file `Basic email reply n8n.json`.
4. Buka node **OpenRouter Chat Model** dan pilih atau buat kredensial OpenRouter.
5. Buka node **Send a message in Gmail** dan pilih atau buat kredensial Gmail OAuth2.
6. Simpan workflow.

## Cara menggunakan

Aktifkan workflow atau buka trigger chat, kemudian berikan instruksi seperti:

> Buat email dalam bahasa Indonesia untuk mengonfirmasi jadwal meeting besok pukul 10.00.

Jika ingin mengirim email, berikan instruksi yang jelas, misalnya:

> Kirim email tersebut ke nama@example.com dengan nada profesional.

Periksa kembali penerima, subjek, dan isi email sebelum mengizinkan pengiriman.

## Keamanan

File workflow biasanya tidak menyimpan nilai API key atau OAuth token secara langsung, tetapi berisi referensi kredensial n8n, ID workflow, webhook ID, dan metadata instance. Sebelum dipublikasikan, pastikan:

- API key, access token, refresh token, password, dan client secret tidak ada di file.
- Kredensial dikelola melalui **n8n Credentials**, bukan ditulis di node atau expression.
- Workflow tidak menggunakan data email pribadi atau isi pesan sensitif sebagai contoh.
- Jika workflow pernah berisi rahasia, lakukan rotasi key/token sebelum push ke GitHub.
- Jangan membagikan URL chat/webhook publik tanpa autentikasi dan pembatasan akses yang sesuai.

## Catatan konfigurasi

Model AI, kredensial, dan pengaturan trigger dapat berbeda tergantung versi n8n. Setelah import, periksa kembali semua node dan lakukan pengujian dengan alamat email uji sebelum mengirim email sungguhan.

## Lisensi

Tambahkan lisensi proyek sesuai kebutuhan Anda.
# n8n-email-reply
