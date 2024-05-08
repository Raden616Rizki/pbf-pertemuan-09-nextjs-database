| Raden Rizki | 2141720064 | TI - 3C | 13 |

## Praktikum 1: Setup Database

### Langkah 1: Buat Project Baru dengan [Template](https://github.com/jti-polinema/09-nextjs-database)

![gambar-praktikum](../pbf-pertemuan-09-nextjs-database/img/praktikum_1_langkah_1.png)

### Langkah 2: Membuat Akun [Vercel](https://vercel.com/signup)

![gambar-praktikum](../pbf-pertemuan-09-nextjs-database/img/praktikum_1_langkah_2_1.png)

- Klik Continue with GitHub

![gambar-praktikum](../pbf-pertemuan-09-nextjs-database/img/praktikum_1_langkah_2_2.png)

![gambar-praktikum](../pbf-pertemuan-09-nextjs-database/img/praktikum_1_langkah_2_3.png)

### Langkah 3: Koneksikan dan Deploy Project Anda

- Klik Install > Pilih Repo > Install

![gambar-praktikum](../pbf-pertemuan-09-nextjs-database/img/praktikum_1_langkah_3_1.png)

- Klik Import > Pilih Framework > Deploy

![gambar-praktikum](../pbf-pertemuan-09-nextjs-database/img/praktikum_1_langkah_3_2.png)

![gambar-praktikum](../pbf-pertemuan-09-nextjs-database/img/praktikum_1_langkah_3_3.png)

**Soal 1**

Capture hasil deploy project Anda dan buatlah laporan di file README.md. Jelaskan apa yang telah Anda pelajari?

Dengan memanfaatkan Vercel, deployment proyek dapat dilakukan dengan mengimport ada memberi akses Vercel, baik ke semua repository yang dimiliki atau hanya yand dipilih saja. Selain itu, Vercel juga menyediakan preview dari laman yang sudah dibuat.

### Langkah 4: Membuat Basis Data Postgres

![gambar-praktikum](../pbf-pertemuan-09-nextjs-database/img/praktikum_1_langkah_4_1.png)

![gambar-praktikum](../pbf-pertemuan-09-nextjs-database/img/praktikum_1_langkah_4_2.png)

![gambar-praktikum](../pbf-pertemuan-09-nextjs-database/img/praktikum_1_langkah_4_3.png)

Show secret > Copy Snippet

![gambar-praktikum](../pbf-pertemuan-09-nextjs-database/img/praktikum_1_langkah_4_4.png)

![gambar-praktikum](../pbf-pertemuan-09-nextjs-database/img/praktikum_1_langkah_4_5.png)

![gambar-praktikum](../pbf-pertemuan-09-nextjs-database/img/praktikum_1_langkah_4_5.png)

Install Vercel Postgres SDK

```bash
npm i --save @vercel/postgres
```

**Soal 2**

Capture hasil basis data Anda dan buatlah laporan di file README.md. Jelaskan apa yang telah Anda pelajari?

Selain dalam hal deployment proyek dari Github, Vercel juga dapat membantu dalam pembuatan Database, pada praktikum ini dilakukan pembuatan database Postgre dengan Vercel, untuk mengakses Database ini maka perlu dibuat file .env dan menambahkan file tersebut ke .gitignore agar kode untuk akses database tersebut tidak ikut terpush ke Github.

### Langkah 5: Melakukan seed ke basis data

![gambar-praktikum](../pbf-pertemuan-09-nextjs-database/img/praktikum_1_langkah_5_1.png)

![gambar-praktikum](../pbf-pertemuan-09-nextjs-database/img/praktikum_1_langkah_5_2.png)

```bash
 "seed": "node -r dotenv/config ./src/seeder/seed.js"
```

![gambar-praktikum](../pbf-pertemuan-09-nextjs-database/img/praktikum_1_langkah_5_3.png)

```bash
npm run seed
```

Error: Cannot find module 'dotenv/config'

```bash
npm i --save dotenv
```

Error: Cannot find module 'data.js'

![gambar-praktikum](../pbf-pertemuan-09-nextjs-database/img/praktikum_1_langkah_5_4.png)

Error: Cannot find module 'bcrypt'

```bash
npm i --save bcrypt
```

![gambar-praktikum](../pbf-pertemuan-09-nextjs-database/img/praktikum_1_langkah_5_5.png)

**Soal 3**

Capture hasil npm run seed Anda dan buatlah laporan di file README.md. Jelaskan apa yang telah Anda pelajari ?

Dari file yand sudah dibuat tersebut, masing-masing memiliki kegunaan. File seed.js berguna untuk menginputkan data dan tabel kedalam database, sedangkan data.js berguna untuk menentukan data apa saja yang akan diinputkan ditiap tabel.

### Langkah 6: Menjelajah Basis Data

![gambar-praktikum](../pbf-pertemuan-09-nextjs-database/img/praktikum_1_langkah_6_1.png)

```bash
SELECT invoices.amount, customers.name
FROM invoices
JOIN customers ON invoices.customer_id = customers.id
WHERE invoices.amount = 666;
```

![gambar-praktikum](../pbf-pertemuan-09-nextjs-database/img/praktikum_1_langkah_6_2.png)

Soal 4
Capture hasil query Anda dan buatlah laporan di file README.md. Jelaskan apa yang telah Anda pelajari ? 

Dari Query diatas berguna untuk menggabungkan tabel invoices dan customers, dengan hanya menampilkan data amount dan name dari masing-masing tabel dengan key berupa customer_id, dan data yang ditampilkan adalah amount dari invoices yang memiliki nilai 666.

Cobalah eksekusi query SQL yang lain sesuai kreasi Anda, capture hasilnya dan jelaskan!

![gambar-praktikum](../pbf-pertemuan-09-nextjs-database/img/praktikum_1_langkah_6_3.png)

```bash
SELECT customers.name, invoices.amount, invoices.status, invoices.date
FROM invoices
JOIN customers ON invoices.customer_id = customers.id
WHERE customers.name = 'Lee Robinson';
```

Masih sama seperti sebelumnya yaitu menggabungkan tabel invoices dan customers berdasarkan customer_id, namun data yang ditampilkan adalah dari kolom customers.name, invoices.amount, invoices.status, dan invoices.date yang memiliki customers.name Lee Robinson.
