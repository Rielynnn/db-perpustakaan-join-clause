# db-perpustakaan-join-clause
## Apa Itu Join Clause?
- INNER JOIN: Mengambil baris yang memiliki nilai cocok di kedua tabel.
- LEFT JOIN (LEFT OUTER JOIN): Mengambil semua baris dari tabel kiri, dan baris yang cocok dari tabel kanan. Jika tidak ada kecocokan, hasilnya adalah NULL.
- RIGHT JOIN (RIGHT OUTER JOIN): Kebalikan dari LEFT JOIN, mengambil semua baris dari tabel kanan dan yang cocok dari kiri.
- FULL JOIN (FULL OUTER JOIN): Mengambil semua baris ketika ada kecocokan di salah satu tabel.
> Sumber: [W3Schools](https://www.w3schools.com/sql/sql_join.asp)

## Tools Yang Digunakan
![Laragon-Icon-Image](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQSKjcbOP1ApfK9xkBStjyBNWvvoVlSSzHezQ&s)\
With\
![Cmder-Icon-Image](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQC3gFFSs4KkpFP0C7H-kWQEsOM5O50PVOFHZdd1MxoFw&s)

## Langkah-Langkah Pembuatan
### 1. Menentukan Struktur database
```
.
├── db_hotel/
│   ├── pelanggan
│   ├── kamar
|   ├── reservasi
├──
.
```
### 2. Membuat Database
Query
```
create database db_hotel;
```
### 3. Menggunakan Database
Query
```
use db_hotel;
```
### 4. Membuat Tabel Pelanggan
Struktur Tabel
```
.
├── pelanggan/
│   ├── id_pelanggan int primary key
│   ├── nama_pelanggan(100)
|   ├── usia int(3)
|   ├── alamat varchar(500)
├──
.
```
Query
```
create table pelanggan(
    -> id_pelanggan int auto_increment primary key,
    -> nama_pelanggan varchar(100) not null,
    -> usia int(3) not null,
    -> alamat varchar(500) not null);
```
Hasil
```
+----------------+--------------+------+-----+---------+----------------+
| Field          | Type         | Null | Key | Default | Extra          |
+----------------+--------------+------+-----+---------+----------------+
| id_pelanggan   | int          | NO   | PRI | NULL    | auto_increment |
| nama_pelanggan | varchar(100) | NO   |     | NULL    |                |
| usia           | int          | NO   |     | NULL    |                |
| alamat         | varchar(500) | NO   |     | NULL    |                |
+----------------+--------------+------+-----+---------+----------------+
```
### 5. Memasukkan Data Pada Tabel Pelanggan
Query
```
INSERT INTO pelanggan (id_pelanggan, nama_pelanggan, usia, alamat) VALUES
(1, 'Andi Saputra', 21, 'Jakarta'),
(2, 'Budi Hartono', 25, 'Bandung'),
(3, 'Citra Lestari', 19, 'Surabaya'),
(4, 'Dewi Anggraini', 30, 'Medan'),
(5, 'Eko Pratama', 28, 'Yogyakarta'),
(6, 'Fajar Nugroho', 23, 'Semarang'),
(7, 'Gina Maharani', 27, 'Palembang'),
(8, 'Hendra Wijaya', 35, 'Makassar'),
(9, 'Intan Permata', 22, 'Depok'),
(10, 'Joko Susanto', 40, 'Bekasi');
```
Hasil
```
+--------------+----------------+------+------------+
| id_pelanggan | nama_pelanggan | usia | alamat     |
+--------------+----------------+------+------------+
|            1 | Andi Saputra   |   21 | Jakarta    |
|            2 | Budi Hartono   |   25 | Bandung    |
|            3 | Citra Lestari  |   19 | Surabaya   |
|            4 | Dewi Anggraini |   30 | Medan      |
|            5 | Eko Pratama    |   28 | Yogyakarta |
|            6 | Fajar Nugroho  |   23 | Semarang   |
|            7 | Gina Maharani  |   27 | Palembang  |
|            8 | Hendra Wijaya  |   35 | Makassar   |
|            9 | Intan Permata  |   22 | Depok      |
|           10 | Joko Susanto   |   40 | Bekasi     |
+--------------+----------------+------+------------+
```
### 6. Membuat Tabel Kamar
Struktur Tabel
```
.
├── kamar/
│   ├── id_kamar int primary key
│   ├── nomor_kamar int(3)
|   ├── tipe_kamar varchar(5)
|   ├── fasilitas_kamar varchar(500)
├──
.
```
Query
```
create table kamar(
    -> id_kamar int auto_increment primary key,
    -> nomor_kamar int(3) not null,
    -> tipe_kamar varchar(5) not null,
    -> fasilitas_kamar varchar(500) not null);
```
Hasil
```
+-----------------+--------------+------+-----+---------+----------------+
| Field           | Type         | Null | Key | Default | Extra          |
+-----------------+--------------+------+-----+---------+----------------+
| id_kamar        | int          | NO   | PRI | NULL    | auto_increment |
| nomor_kamar     | int          | NO   |     | NULL    |                |
| tipe_kamar      | varchar(5)   | NO   |     | NULL    |                |
| fasilitas_kamar | varchar(500) | NO   |     | NULL    |                |
+-----------------+--------------+------+-----+---------+----------------+
```
### 7. Memasukkan Data Pada Tabel Kamar
Query
```
INSERT INTO kamar (id_kamar, nomor_kamar, tipe_kamar, fasilitas_kamar) VALUES
(1, '101', 'STD', 'Fan, TV'),
(2, '102', 'STD', 'AC, TV'),
(3, '103', 'STD', 'AC, WiFi'),
(4, '201', 'VIP', 'AC, TV, WiFi'),
(5, '202', 'VIP', 'AC, TV, WiFi, Balkon'),
(6, '203', 'VIP', 'AC, TV, Mini Bar'),
(7, '301', 'VVIP', 'AC, TV, WiFi, Bathtub'),
(8, '302', 'VVIP', 'AC, TV, WiFi, Mini Bar'),
(9, '401', 'VVIP', 'AC, TV, WiFi, 2 Bed'),
(10, '402', 'STD', 'AC, TV');
```
Hasil
```
+----------+-------------+------------------------+------------+
| id_kamar | nomor_kamar | fasilitas_kamar        | tipe_kamar |
+----------+-------------+------------------------+------------+
|        1 |         101 | Fan, TV                | STD        |
|        2 |         102 | AC, TV                 | STD        |
|        3 |         103 | AC, WiFi               | STD        |
|        4 |         201 | AC, TV, WiFi           | VIP        |
|        5 |         202 | AC, TV, WiFi, Balkon   | VIP        |
|        6 |         203 | AC, TV, Mini Bar       | VIP        |
|        7 |         301 | AC, TV, WiFi, Bathtub  | VVIP       |
|        8 |         302 | AC, TV, WiFi, Mini Bar | VVIP       |
|        9 |         401 | AC, TV, WiFi, 2 Bed    | VVIP       |
|       10 |         402 | AC, TV                 | STD        |
+----------+-------------+------------------------+------------+
```
### 8. Membuat Tabel Reservasi
Struktur Tabel
```
.
├── reservasi/
│   ├── id_reservasi int primary key
│   ├── id_pelanggan int foreign key
|   ├── id_kamar int foreign key
|   ├── tanggal_reservasi date
├──
.
```
Query
```
 create table reservasi(
    -> id_reservasi int auto_increment primary key,
    -> id_pelanggan int,
    -> id_kamar int,
    -> tanggal_reservasi date,
    -> foreign key (id_pelanggan) references pelanggan(id_pelanggan),
    -> foreign key (id_kamar) references kamar(id_kamar));
```
Hasil
```
+-------------------+------+------+-----+---------+----------------+
| Field             | Type | Null | Key | Default | Extra          |
+-------------------+------+------+-----+---------+----------------+
| id_reservasi      | int  | NO   | PRI | NULL    | auto_increment |
| id_pelanggan      | int  | YES  | MUL | NULL    |                |
| id_kamar          | int  | YES  | MUL | NULL    |                |
| tanggal_reservasi | date | YES  |     | NULL    |                |
+-------------------+------+------+-----+---------+----------------+
```
### 9. Memasukkan Data Pada Tabel Reservasi
Query
```
INSERT INTO reservasi (id_reservasi, id_pelanggan, id_kamar, tanggal_reservasi) VALUES
(1, 1, 1, '2026-03-01'),
(2, 2, 4, '2026-03-02'),
(3, 3, 7, '2026-03-02'),
(4, 4, 2, '2026-03-03'),
(5, 5, 5, '2026-03-04'),
(6, 6, 8, '2026-03-04'),
(7, 7, 3, '2026-03-05'),
(8, 8, 9, '2026-03-06'),
(9, 9, 6, '2026-03-06'),
(10, 10, 10, '2026-03-07');
```
Hasil
```
+--------------+--------------+----------+-------------------+
| id_reservasi | id_pelanggan | id_kamar | tanggal_reservasi |
+--------------+--------------+----------+-------------------+
|            1 |            1 |        1 | 2026-03-01        |
|            2 |            2 |        4 | 2026-03-02        |
|            3 |            3 |        7 | 2026-03-02        |
|            4 |            4 |        2 | 2026-03-03        |
|            5 |            5 |        5 | 2026-03-04        |
|            6 |            6 |        8 | 2026-03-04        |
|            7 |            7 |        3 | 2026-03-05        |
|            8 |            8 |        9 | 2026-03-06        |
|            9 |            9 |        6 | 2026-03-06        |
|           10 |           10 |       10 | 2026-03-07        |
+--------------+--------------+----------+-------------------+
```
### 10. Menampilkan Data Yang Sama Pada Kedua Tabel Menggunakan _INNER_ JOIN
Query
```
select reservasi.id_reservasi, pelanggan.nama_pelanggan, kamar.nomor_kamar, kamar.fasilitas_kamar, reservasi.tanggal_reservasi
    -> from reservasi
    -> inner join pelanggan
    -> on reservasi.id_pelanggan=pelanggan.id_pelanggan
    -> inner join kamar
    -> on reservasi.id_kamar=kamar.id_kamar;
```
Hasil
```
+--------------+----------------+-------------+------------------------+-------------------+
| id_reservasi | nama_pelanggan | nomor_kamar | fasilitas_kamar        | tanggal_reservasi |
+--------------+----------------+-------------+------------------------+-------------------+
|            1 | Andi Saputra   |         101 | Fan, TV                | 2026-03-01        |
|            2 | Budi Hartono   |         201 | AC, TV, WiFi           | 2026-03-02        |
|            3 | Citra Lestari  |         301 | AC, TV, WiFi, Bathtub  | 2026-03-02        |
|            4 | Dewi Anggraini |         102 | AC, TV                 | 2026-03-03        |
|            5 | Eko Pratama    |         202 | AC, TV, WiFi, Balkon   | 2026-03-04        |
|            6 | Fajar Nugroho  |         302 | AC, TV, WiFi, Mini Bar | 2026-03-04        |
|            7 | Gina Maharani  |         103 | AC, WiFi               | 2026-03-05        |
|            8 | Hendra Wijaya  |         401 | AC, TV, WiFi, 2 Bed    | 2026-03-06        |
|            9 | Intan Permata  |         203 | AC, TV, Mini Bar       | 2026-03-06        |
|           10 | Joko Susanto   |         402 | AC, TV                 | 2026-03-07        |
+--------------+----------------+-------------+------------------------+-------------------+
```
### 11. Menambahkan Data Baru Pada Tabel Kamar
Query
```
insert into kamar (nomor_kamar, tipe_kamar, fasilitas_kamar) values ('505', 'VVIP', 'Kasur Royal, Playstation 5, Netflix');
```
### 12. Menampilkan Data Baru di Tabel Kamar Menggunakan _LEFT_ JOIN
Query
```
 select reservasi.id_reservasi, pelanggan.nama_pelanggan, kamar.nomor_kamar, kamar.fasilitas_kamar, reservasi.tanggal_reservasi
    -> from reservasi
    -> left join pelanggan
    -> on reservasi.id_pelanggan=pelanggan.id_pelanggan
    -> right join kamar
    -> on reservasi.id_kamar=kamar.id_kamar;
```
Hasil
```
+--------------+----------------+-------------+-------------------------------------+-------------------+
| id_reservasi | nama_pelanggan | nomor_kamar | fasilitas_kamar                     | tanggal_reservasi |
+--------------+----------------+-------------+-------------------------------------+-------------------+
|            1 | Andi Saputra   |         101 | Fan, TV                             | 2026-03-01        |
|            4 | Dewi Anggraini |         102 | AC, TV                              | 2026-03-03        |
|            7 | Gina Maharani  |         103 | AC, WiFi                            | 2026-03-05        |
|            2 | Budi Hartono   |         201 | AC, TV, WiFi                        | 2026-03-02        |
|            5 | Eko Pratama    |         202 | AC, TV, WiFi, Balkon                | 2026-03-04        |
|            9 | Intan Permata  |         203 | AC, TV, Mini Bar                    | 2026-03-06        |
|            3 | Citra Lestari  |         301 | AC, TV, WiFi, Bathtub               | 2026-03-02        |
|            6 | Fajar Nugroho  |         302 | AC, TV, WiFi, Mini Bar              | 2026-03-04        |
|            8 | Hendra Wijaya  |         401 | AC, TV, WiFi, 2 Bed                 | 2026-03-06        |
|           10 | Joko Susanto   |         402 | AC, TV                              | 2026-03-07        |
|         NULL | NULL           |         505 | Kasur Royal, Playstation 5, Netflix | NULL              |
+--------------+----------------+-------------+-------------------------------------+-------------------+
```
### 13. Menambahkan Data Baru Pada Tabel Pelanggan
Query
```
insert into pelanggan (nama_pelanggan, usia, alamat) values ('Yi Sang', '30', 'Canto');
```
### 14. Menampilkan Data Baru di Tabel Pelanggan Menggunakan _RIGHT_ JOIN
Query
```
 select reservasi.id_reservasi, pelanggan.nama_pelanggan, kamar.nomor_kamar, kamar.fasilitas_kamar, reservasi.tanggal_reservasi
    -> from reservasi
    -> right join pelanggan
    -> on reservasi.id_pelanggan=pelanggan.id_pelanggan
    -> left join kamar
    -> on reservasi.id_kamar=kamar.id_kamar;
```
Hasil
```
+--------------+----------------+-------------+------------------------+-------------------+
| id_reservasi | nama_pelanggan | nomor_kamar | fasilitas_kamar        | tanggal_reservasi |
+--------------+----------------+-------------+------------------------+-------------------+
|            1 | Andi Saputra   |         101 | Fan, TV                | 2026-03-01        |
|            2 | Budi Hartono   |         201 | AC, TV, WiFi           | 2026-03-02        |
|            3 | Citra Lestari  |         301 | AC, TV, WiFi, Bathtub  | 2026-03-02        |
|            4 | Dewi Anggraini |         102 | AC, TV                 | 2026-03-03        |
|            5 | Eko Pratama    |         202 | AC, TV, WiFi, Balkon   | 2026-03-04        |
|            6 | Fajar Nugroho  |         302 | AC, TV, WiFi, Mini Bar | 2026-03-04        |
|            7 | Gina Maharani  |         103 | AC, WiFi               | 2026-03-05        |
|            8 | Hendra Wijaya  |         401 | AC, TV, WiFi, 2 Bed    | 2026-03-06        |
|            9 | Intan Permata  |         203 | AC, TV, Mini Bar       | 2026-03-06        |
|           10 | Joko Susanto   |         402 | AC, TV                 | 2026-03-07        |
|         NULL | Yi Sang        |        NULL | NULL                   | NULL              |
+--------------+----------------+-------------+------------------------+-------------------+
```
### 15. Menampilkan Semua Data Baru di Kedua Tabel Menggunakan Simulasi _FULL_ JOIN 
Query
```
select reservasi.id_reservasi, pelanggan.nama_pelanggan, kamar.nomor_kamar, kamar.fasilitas_kamar, reservasi.tanggal_reservasi
    -> from reservasi
    -> left join pelanggan
    -> on reservasi.id_pelanggan=pelanggan.id_pelanggan
    -> right join kamar
    -> on reservasi.id_kamar=kamar.id_kamar
    -> union
    -> select reservasi.id_reservasi, pelanggan.nama_pelanggan, kamar.nomor_kamar, kamar.fasilitas_kamar, reservasi.tanggal_reservasi
    -> from reservasi
    -> right join pelanggan
    -> on reservasi.id_pelanggan=pelanggan.id_pelanggan
    -> left join kamar
    -> on reservasi.id_kamar=kamar.id_kamar;
```
Hasil
```
+--------------+----------------+-------------+-------------------------------------+-------------------+
| id_reservasi | nama_pelanggan | nomor_kamar | fasilitas_kamar                     | tanggal_reservasi |
+--------------+----------------+-------------+-------------------------------------+-------------------+
|            1 | Andi Saputra   |         101 | Fan, TV                             | 2026-03-01        |
|            4 | Dewi Anggraini |         102 | AC, TV                              | 2026-03-03        |
|            7 | Gina Maharani  |         103 | AC, WiFi                            | 2026-03-05        |
|            2 | Budi Hartono   |         201 | AC, TV, WiFi                        | 2026-03-02        |
|            5 | Eko Pratama    |         202 | AC, TV, WiFi, Balkon                | 2026-03-04        |
|            9 | Intan Permata  |         203 | AC, TV, Mini Bar                    | 2026-03-06        |
|            3 | Citra Lestari  |         301 | AC, TV, WiFi, Bathtub               | 2026-03-02        |
|            6 | Fajar Nugroho  |         302 | AC, TV, WiFi, Mini Bar              | 2026-03-04        |
|            8 | Hendra Wijaya  |         401 | AC, TV, WiFi, 2 Bed                 | 2026-03-06        |
|           10 | Joko Susanto   |         402 | AC, TV                              | 2026-03-07        |
|         NULL | NULL           |         505 | Kasur Royal, Playstation 5, Netflix | NULL              |
|         NULL | Yi Sang        |        NULL | NULL                                | NULL              |
+--------------+----------------+-------------+-------------------------------------+-------------------+
```
> FULL JOIN pada MYSQL tidak memungkinkan. Oleh karena itu, ini hanya simulasi yang mendekati.
