# Materi Teori: Trace Table untuk Verifikasi Kebenaran Algoritma

## Mata Kuliah: Logika dan Algoritma

---

## 1. Identitas Materi

- **Mata Kuliah:** Logika dan Algoritma
- **Topik:** Trace Table (Tabel Penelusuran) untuk Verifikasi Algoritma
- **Fokus:** Menelusuri langkah eksekusi algoritma dan memeriksa kebenaran hasilnya secara sistematis.
- **Bentuk pembelajaran:** Konsep, demonstrasi, latihan, dan studi kasus.
- **Prasyarat:** Variabel, tipe data, operator aritmatika/relasional/logika, percabangan, perulangan, dan algoritma/pseudocode dasar.

### Gambaran Umum

Dalam pembelajaran logika dan algoritma, sebuah algoritma tidak cukup hanya dapat ditulis atau dijalankan. Algoritma juga perlu diperiksa apakah langkah-langkahnya menghasilkan keluaran yang sesuai dengan spesifikasi masalah. Salah satu teknik dasar yang dapat digunakan sebelum algoritma diterjemahkan menjadi program adalah **trace table** atau **tabel penelusuran**.

Trace table dilakukan dengan mensimulasikan eksekusi algoritma secara manual. Setiap instruksi ditelusuri sesuai urutannya, perubahan nilai variabel dicatat, kondisi dievaluasi, cabang yang benar diikuti, dan setiap iterasi perulangan dicatat. Dengan cara tersebut, mahasiswa dapat melihat proses algoritma secara eksplisit, bukan hanya melihat output akhirnya.

---

## 2. Capaian Pembelajaran

Setelah mempelajari materi ini, mahasiswa diharapkan mampu:

1. Menjelaskan konsep dan fungsi **trace table**.
2. Mengidentifikasi variabel, kondisi, proses, dan output dalam algoritma.
3. Menentukan kolom trace table berdasarkan variabel yang berubah selama eksekusi.
4. Melakukan tracing algoritma **baris demi baris**.
5. Menentukan perubahan nilai variabel pada setiap langkah eksekusi.
6. Memeriksa hasil ekspresi aritmatika, relasional, dan logika.
7. Melakukan tracing algoritma yang memiliki:
   - sequence,
   - selection/percabangan,
   - nested selection,
   - loop/perulangan,
   - nested loop.
8. Menemukan kesalahan logika (**logical error**) menggunakan trace table.
9. Membandingkan hasil yang diharapkan dengan hasil aktual algoritma.
10. Menyimpulkan apakah algoritma telah bekerja sesuai spesifikasi.

### Indikator Penguasaan

Mahasiswa dapat dikatakan menguasai materi apabila mampu membaca pseudocode, menentukan nilai awal, menelusuri assignment dan kondisi, mengikuti jalur eksekusi yang benar, menelusuri seluruh iterasi loop, serta menunjukkan perbedaan antara **expected output** dan **actual output** apabila terdapat kesalahan logika.

---

# 3. Konsep Dasar Trace Table

## 3.1 Pengertian

**Trace table** atau **tabel penelusuran** adalah tabel yang digunakan untuk mencatat perubahan nilai variabel dan hasil kondisi selama algoritma dieksekusi.

Trace table membantu mahasiswa menjawab pertanyaan:

> **"Apa yang terjadi pada setiap langkah algoritma jika diberikan input tertentu?"**

Trace table bukan sekadar mencatat output akhir, tetapi menelusuri **proses menuju output**.

Secara sederhana, tracing dapat dipandang sebagai proses **manual execution**, yaitu menjalankan algoritma secara konseptual tanpa harus terlebih dahulu mengeksekusinya pada komputer.

Contohnya, jika algoritma memiliki:

```text
x = 10
y = 5
hasil = x + y
OUTPUT hasil
```

maka tracing tidak langsung menuliskan `15`. Kita perlu memperlihatkan bahwa:

1. `x` memperoleh nilai `10`.
2. `y` memperoleh nilai `5`.
3. `hasil` dihitung dari `10 + 5`, sehingga menjadi `15`.
4. `15` kemudian ditampilkan.

Dengan demikian, trace table memperlihatkan hubungan antara instruksi dan keadaan variabel setelah instruksi tersebut dijalankan.

---

## 3.2 Tujuan Trace Table

Trace table digunakan untuk:

- memeriksa kebenaran algoritma,
- memahami alur eksekusi,
- mengetahui perubahan nilai variabel,
- memeriksa kondisi percabangan,
- memeriksa jumlah iterasi,
- menemukan **logical error**,
- membuktikan bahwa output sesuai dengan input dan aturan algoritma.

### Mengapa Trace Table Penting?

Sebuah algoritma dapat saja mempunyai sintaks yang benar tetapi tetap menghasilkan jawaban yang salah. Kesalahan seperti salah operator, salah nilai awal, salah pembagi, salah batas kondisi, atau salah pembaruan variabel dapat diketahui melalui penelusuran.

Trace table juga melatih mahasiswa untuk tidak sekadar menebak output. Setiap nilai yang muncul harus mempunyai dasar dari statement yang telah dieksekusi.

---

## 3.3 Trace Table vs Output Table

| Aspek | Output Table | Trace Table |
|---|---|---|
| Fokus | Hasil akhir | Proses eksekusi |
| Variabel antara | Biasanya tidak dicatat | Dicatat |
| Kondisi | Tidak selalu dicatat | Dicatat bila relevan |
| Iterasi | Tidak terlihat | Terlihat |
| Debugging | Terbatas | Sangat membantu |
| Verifikasi algoritma | Sebagian | Lebih sistematis |

Output table terutama menunjukkan apa yang dihasilkan. Trace table menunjukkan **bagaimana hasil tersebut diperoleh**.

---

# 4. Komponen Trace Table

Trace table umumnya terdiri dari:

| Komponen | Fungsi |
|---|---|
| Step/Baris | Menunjukkan urutan eksekusi |
| Statement | Menunjukkan instruksi yang dijalankan |
| Input | Nilai masukan |
| Variabel | Nilai variabel setelah instruksi |
| Condition | Hasil evaluasi kondisi |
| Output | Hasil yang ditampilkan |

Tidak semua kolom harus digunakan. Kolom dipilih berdasarkan algoritma yang sedang dianalisis.

## 4.1 Prinsip Memilih Kolom

Jika algoritma memiliki variabel:

```text
a, b, total, rata_rata
```

maka trace table minimal dapat memiliki:

```text
Step | Statement | a | b | total | rata_rata | Output
```

Jika algoritma memiliki percabangan:

```text
nilai >= 60
```

tambahkan:

```text
Condition
```

Jika algoritma memiliki perulangan:

```text
i = 1 sampai 5
```

tambahkan:

```text
Iteration / i
```

### Prinsip Praktis

Kolom trace table sebaiknya cukup untuk menjawab tiga hal:

1. **Instruksi apa yang sedang dijalankan?**
2. **Bagaimana keadaan variabel setelah instruksi tersebut?**
3. **Mengapa jalur eksekusi tertentu dipilih?**

Untuk algoritma sederhana, tabel dapat dibuat ringkas. Untuk algoritma yang memiliki banyak kondisi dan loop, tabel perlu dibuat lebih detail.

---

# 5. Prosedur Melakukan Tracing

## Langkah 1 — Baca spesifikasi algoritma

Tentukan:

- input,
- proses,
- output,
- aturan atau kondisi yang digunakan.

Spesifikasi menjadi acuan ketika hasil aktual dibandingkan dengan hasil yang diharapkan.

## Langkah 2 — Baca pseudocode dari awal

Jangan langsung melihat output akhir.

Baca pseudocode dari statement pertama dan ikuti urutan eksekusinya.

## Langkah 3 — Identifikasi semua variabel

Catat variabel yang:

- menerima input,
- mengalami assignment,
- digunakan dalam kondisi,
- berubah dalam loop.

Variabel yang berubah perlu dicatat karena perubahan tersebut dapat memengaruhi instruksi berikutnya.

## Langkah 4 — Tentukan input pengujian

Pilih input yang relevan.

Untuk algoritma dengan percabangan, sebaiknya gunakan beberapa input yang mewakili:

- kondisi benar,
- kondisi salah,
- nilai batas (**boundary value**).

## Langkah 5 — Buat kolom trace table

Contoh:

```text
Step | Statement | x | y | hasil | Condition | Output
```

## Langkah 6 — Eksekusi satu instruksi setiap kali

Setiap assignment menyebabkan nilai variabel diperbarui.

Contoh:

```text
x = 10
y = 5
hasil = x + y
```

Tracing:

| Step | Statement | x | y | hasil |
|---:|---|---:|---:|---:|
| 1 | x = 10 | 10 | - | - |
| 2 | y = 5 | 10 | 5 | - |
| 3 | hasil = x + y | 10 | 5 | 15 |

Tanda `-` menunjukkan bahwa variabel tersebut belum memiliki nilai yang relevan pada langkah tersebut.

## Langkah 7 — Evaluasi kondisi

Untuk:

```text
if nilai >= 60
```

catat hasil kondisi:

```text
nilai = 75
75 >= 60 → TRUE
```

## Langkah 8 — Ikuti hanya jalur yang dieksekusi

Jika kondisi `TRUE`, jalankan blok `THEN`.

Jika `FALSE`, jalankan blok `ELSE` jika tersedia.

Jangan mencatat statement dari cabang yang tidak dieksekusi sebagai perubahan nilai aktual.

## Langkah 9 — Untuk loop, buat satu baris per iterasi

Catat perubahan:

- counter,
- kondisi loop,
- variabel yang diproses,
- hasil sementara.

## Langkah 10 — Bandingkan output aktual dan output yang diharapkan

Gunakan format:

```text
Expected Output = ...
Actual Output   = ...
Status          = BENAR / SALAH
```

Perbandingan ini menjadi dasar kesimpulan verifikasi algoritma.

---

# 6. Aturan Penting Saat Tracing

1. **Eksekusi sesuai urutan algoritma.**
2. Jangan mengubah nilai variabel sebelum statement yang mengubahnya dijalankan.
3. Untuk assignment, nilai lama digantikan oleh nilai baru.
4. Untuk kondisi, tuliskan hasil `TRUE/FALSE`.
5. Untuk percabangan, hanya jalur yang memenuhi kondisi yang dieksekusi.
6. Untuk loop, setiap iterasi harus ditelusuri.
7. Jika sebuah variabel belum memiliki nilai, gunakan `-` atau `undefined`.
8. Bedakan:
   - `=` sebagai assignment,
   - `==` sebagai perbandingan jika bahasa pemrograman yang digunakan memakai operator tersebut.
9. Untuk operator logika, hitung ekspresi secara sistematis.
10. Output akhir harus berasal dari nilai variabel yang benar-benar diperoleh dari tracing.

### Catatan tentang Assignment

Misalnya:

```text
x = 10
x = x + 5
```

Setelah statement pertama:

```text
x = 10
```

Setelah statement kedua:

```text
x = 15
```

Nilai lama `10` digunakan untuk menghitung nilai baru, kemudian digantikan oleh `15`.

---

# 7. Tracing Sequence / Algoritma Berurutan

**Sequence** adalah struktur algoritma yang menjalankan instruksi secara berurutan dari awal sampai akhir tanpa memilih cabang berdasarkan kondisi.

## Studi Kasus 1 — Menghitung Luas Persegi Panjang

### Algoritma

```text
INPUT panjang
INPUT lebar

luas = panjang * lebar

OUTPUT luas
```

### Input

```text
panjang = 10
lebar = 5
```

### Trace Table

| Step | Statement | panjang | lebar | luas | Output |
|---:|---|---:|---:|---:|---|
| 1 | INPUT panjang | 10 | - | - | - |
| 2 | INPUT lebar | 10 | 5 | - | - |
| 3 | luas = panjang × lebar | 10 | 5 | 50 | - |
| 4 | OUTPUT luas | 10 | 5 | 50 | 50 |

### Kesimpulan

Algoritma menghasilkan:

```text
Luas = 50
```

Tracing menunjukkan setiap variabel memperoleh nilai yang benar dan output sesuai rumus.

### Pola yang Perlu Dipahami

Pada sequence, penelusuran relatif langsung:

```text
INPUT → PROSES → OUTPUT
```

Tidak ada percabangan yang harus dipilih dan tidak ada iterasi yang harus diulang.

---

# 8. Tracing Operator Aritmatika

## Studi Kasus 2 — Menghitung Rata-Rata

### Algoritma

```text
INPUT a
INPUT b
INPUT c

total = a + b + c
rata = total / 3

OUTPUT rata
```

### Input

```text
a = 80
b = 70
c = 90
```

### Trace Table

| Step | Statement | a | b | c | total | rata | Output |
|---:|---|---:|---:|---:|---:|---:|---:|
| 1 | INPUT a | 80 | - | - | - | - | - |
| 2 | INPUT b | 80 | 70 | - | - | - | - |
| 3 | INPUT c | 80 | 70 | 90 | - | - | - |
| 4 | total = a+b+c | 80 | 70 | 90 | 240 | - | - |
| 5 | rata = total/3 | 80 | 70 | 90 | 240 | 80 | - |
| 6 | OUTPUT rata | 80 | 70 | 90 | 240 | 80 | 80 |

### Hasil

```text
Rata-rata = 80
```

Pada contoh ini, tracing operator aritmatika dilakukan dengan menghitung ekspresi berdasarkan nilai variabel yang telah tersedia pada saat statement dijalankan.

---

# 9. Tracing Percabangan IF–ELSE

Percabangan `IF–ELSE` membuat algoritma memilih salah satu jalur berdasarkan kondisi.

Secara umum:

```text
IF kondisi THEN
    proses A
ELSE
    proses B
END IF
```

Jika kondisi bernilai `TRUE`, proses A dijalankan. Jika `FALSE`, proses B dijalankan.

## Studi Kasus 3 — Menentukan Kelulusan

### Algoritma

```text
INPUT nilai

IF nilai >= 60 THEN
    status = "Lulus"
ELSE
    status = "Tidak Lulus"
END IF

OUTPUT status
```

### Pengujian A

```text
nilai = 75
```

### Trace Table

| Step | Statement | nilai | Condition | status | Output |
|---:|---|---:|---|---|---|
| 1 | INPUT nilai | 75 | - | - | - |
| 2 | nilai >= 60 | 75 | TRUE | - | - |
| 3 | status = "Lulus" | 75 | TRUE | Lulus | - |
| 4 | OUTPUT status | 75 | TRUE | Lulus | Lulus |

### Pengujian B

```text
nilai = 50
```

| Step | Statement | nilai | Condition | status | Output |
|---:|---|---:|---|---|---|
| 1 | INPUT nilai | 50 | - | - | - |
| 2 | nilai >= 60 | 50 | FALSE | - | - |
| 3 | status = "Tidak Lulus" | 50 | FALSE | Tidak Lulus | - |
| 4 | OUTPUT status | 50 | FALSE | Tidak Lulus | Tidak Lulus |

### Boundary Testing

Untuk kondisi:

```text
nilai >= 60
```

uji minimal:

```text
59 → Tidak Lulus
60 → Lulus
61 → Lulus
```

Trace table membantu memastikan operator `>=` diterapkan dengan benar.

---

# 10. Tracing Multiple Conditions

Multiple conditions dapat diwujudkan melalui rangkaian `IF`, `ELSE IF`, dan `ELSE`.

## Studi Kasus 4 — Menentukan Kategori Nilai

### Algoritma

```text
INPUT nilai

IF nilai >= 80 THEN
    kategori = "A"
ELSE IF nilai >= 70 THEN
    kategori = "B"
ELSE IF nilai >= 60 THEN
    kategori = "C"
ELSE
    kategori = "D"
END IF

OUTPUT kategori
```

### Input

```text
nilai = 75
```

### Trace Table

| Step | Statement | nilai | Kondisi | Hasil |
|---:|---|---:|---|---|
| 1 | INPUT nilai | 75 | - | - |
| 2 | nilai >= 80 | 75 | FALSE | Lanjut |
| 3 | nilai >= 70 | 75 | TRUE | Pilih B |
| 4 | kategori = "B" | 75 | TRUE | B |
| 5 | OUTPUT kategori | 75 | - | B |

Ketika kondisi `nilai >= 70` bernilai `TRUE`, cabang yang sesuai dipilih dan pemeriksaan cabang berikutnya tidak diperlukan.

### Pengujian Boundary

| Input | Expected |
|---:|---|
| 59 | D |
| 60 | C |
| 69 | C |
| 70 | B |
| 79 | B |
| 80 | A |

Pengujian tersebut membantu memeriksa batas setiap kategori.

---

# 11. Tracing Operator Logika AND

Operator **AND** bernilai `TRUE` hanya jika semua kondisi yang digabungkan bernilai `TRUE`.

## Studi Kasus 5 — Syarat Beasiswa

### Aturan

Mahasiswa memperoleh status `Memenuhi Syarat` apabila:

```text
IPK >= 3.00 AND penghasilan_orang_tua <= 5000000
```

### Algoritma

```text
INPUT ipk
INPUT penghasilan

IF ipk >= 3.00 AND penghasilan <= 5000000 THEN
    status = "Memenuhi Syarat"
ELSE
    status = "Tidak Memenuhi Syarat"
END IF

OUTPUT status
```

### Input

```text
ipk = 3.40
penghasilan = 4000000
```

### Trace Table

| Step | Statement | IPK | Penghasilan | Kondisi 1 | Kondisi 2 | AND | Status |
|---:|---|---:|---:|---|---|---|---|
| 1 | INPUT ipk | 3.40 | - | - | - | - | - |
| 2 | INPUT penghasilan | 3.40 | 4.000.000 | - | - | - | - |
| 3 | ipk >= 3.00 | 3.40 | 4.000.000 | TRUE | - | - | - |
| 4 | penghasilan <= 5.000.000 | 3.40 | 4.000.000 | TRUE | TRUE | - | - |
| 5 | Kondisi AND | 3.40 | 4.000.000 | TRUE | TRUE | TRUE | - |
| 6 | status = ... | 3.40 | 4.000.000 | TRUE | TRUE | TRUE | Memenuhi Syarat |

### Cara Menelusuri AND

Untuk:

```text
A AND B
```

periksa:

1. nilai A,
2. nilai B,
3. hasil gabungannya.

Jika salah satu kondisi `FALSE`, hasil `AND` menjadi `FALSE`.

---

# 12. Tracing Operator Logika OR

Operator **OR** bernilai `TRUE` jika setidaknya salah satu kondisi bernilai `TRUE`.

## Studi Kasus 6 — Akses Fasilitas Khusus

Mahasiswa memperoleh akses jika:

```text
status = "Dosen" OR status = "Admin"
```

### Input

```text
status = "Dosen"
```

### Trace Table

| Step | Statement | status | Kondisi 1 | Kondisi 2 | OR | Akses |
|---:|---|---|---|---|---|---|
| 1 | INPUT status | Dosen | - | - | - | - |
| 2 | status = Dosen | Dosen | TRUE | - | - | - |
| 3 | status = Admin | Dosen | TRUE | FALSE | - | - |
| 4 | Kondisi OR | Dosen | TRUE | FALSE | TRUE | - |
| 5 | Akses diberikan | Dosen | TRUE | FALSE | TRUE | Ya |

### Cara Menelusuri OR

Untuk:

```text
A OR B
```

periksa setiap kondisi secara terpisah. Jika minimal satu kondisi `TRUE`, hasil OR adalah `TRUE`.

---

# 13. Tracing Nested IF

**Nested IF** adalah percabangan `IF` yang berada di dalam percabangan lain.

## Studi Kasus 7 — Menentukan Bonus Karyawan

### Algoritma

```text
INPUT masa_kerja
INPUT kinerja

IF masa_kerja >= 5 THEN

    IF kinerja >= 90 THEN
        bonus = 20
    ELSE
        bonus = 10
    END IF

ELSE
    bonus = 5
END IF

OUTPUT bonus
```

### Input

```text
masa_kerja = 7
kinerja = 85
```

### Trace Table

| Step | Statement | Masa Kerja | Kinerja | Kondisi 1 | Kondisi 2 | Bonus |
|---:|---|---:|---:|---|---|---:|
| 1 | INPUT masa_kerja | 7 | - | - | - | - |
| 2 | INPUT kinerja | 7 | 85 | - | - | - |
| 3 | masa_kerja >= 5 | 7 | 85 | TRUE | - | - |
| 4 | kinerja >= 90 | 7 | 85 | TRUE | FALSE | - |
| 5 | bonus = 10 | 7 | 85 | TRUE | FALSE | 10 |
| 6 | OUTPUT bonus | 7 | 85 | TRUE | FALSE | 10 |

### Kesimpulan

Bonus yang dihasilkan:

```text
10
```

Dalam nested IF, tracing harus memperhatikan tingkat percabangan. Kondisi kedua baru relevan setelah kondisi pertama membawa eksekusi ke blok yang mengandung kondisi tersebut.

---

# 14. Tracing Perulangan FOR

Perulangan `FOR` digunakan ketika jumlah pengulangan dapat ditentukan melalui counter atau rentang iterasi.

## Studi Kasus 8 — Menghitung Jumlah Bilangan 1 sampai 5

### Algoritma

```text
sum = 0

FOR i = 1 TO 5
    sum = sum + i
END FOR

OUTPUT sum
```

### Trace Table

| Iterasi | i | sum sebelum | Perhitungan | sum sesudah |
|---:|---:|---:|---|---:|
| Awal | - | 0 | - | 0 |
| 1 | 1 | 0 | 0 + 1 | 1 |
| 2 | 2 | 1 | 1 + 2 | 3 |
| 3 | 3 | 3 | 3 + 3 | 6 |
| 4 | 4 | 6 | 6 + 4 | 10 |
| 5 | 5 | 10 | 10 + 5 | 15 |

### Output

```text
15
```

### Prinsip Tracing FOR

Untuk setiap iterasi, perhatikan:

1. nilai counter `i`,
2. nilai variabel sebelum proses,
3. perhitungan,
4. nilai variabel setelah proses.

---

# 15. Tracing WHILE

`WHILE` menjalankan blok selama kondisi bernilai `TRUE`.

## Studi Kasus 9 — Menghitung Mundur

### Algoritma

```text
i = 5

WHILE i > 0
    OUTPUT i
    i = i - 1
END WHILE
```

### Trace Table

| Iterasi | i sebelum kondisi | Kondisi i > 0 | Output | i sesudah |
|---:|---:|---|---:|---:|
| 1 | 5 | TRUE | 5 | 4 |
| 2 | 4 | TRUE | 4 | 3 |
| 3 | 3 | TRUE | 3 | 2 |
| 4 | 2 | TRUE | 2 | 1 |
| 5 | 1 | TRUE | 1 | 0 |
| 6 | 0 | FALSE | - | 0 |

### Output

```text
5 4 3 2 1
```

Perhatikan bahwa pengecekan kondisi pada nilai `0` tetap perlu ditelusuri. Hasil `FALSE` menyebabkan loop berhenti.

---

# 16. Tracing Nested Loop

**Nested loop** adalah perulangan yang berada di dalam perulangan lain. Tracing nested loop harus memperhatikan counter luar dan counter dalam.

## Studi Kasus 10 — Membuat Pola Bintang

### Algoritma

```text
FOR i = 1 TO 3

    FOR j = 1 TO i
        OUTPUT "*"
    END FOR

    OUTPUT newline

END FOR
```

### Trace Table

| Iterasi i | Iterasi j | Kondisi j <= i | Output |
|---:|---:|---|---|
| 1 | 1 | TRUE | * |
| 1 | 2 | FALSE | newline |
| 2 | 1 | TRUE | * |
| 2 | 2 | TRUE | * |
| 2 | 3 | FALSE | newline |
| 3 | 1 | TRUE | * |
| 3 | 2 | TRUE | * |
| 3 | 3 | TRUE | * |
| 3 | 4 | FALSE | newline |

### Output

```text
*
**
***
```

### Prinsip Penting

Pada nested loop, setiap nilai `i` dapat memicu beberapa nilai `j`. Oleh karena itu, tracing harus mencatat seluruh kombinasi iterasi yang benar-benar terjadi.

---

# 17. Studi Kasus Menemukan Logical Error

## Studi Kasus 11 — Kesalahan Perhitungan Rata-Rata

### Algoritma yang dibuat mahasiswa

```text
INPUT a
INPUT b
INPUT c

total = a + b + c
rata = total / 2

OUTPUT rata
```

### Input

```text
a = 80
b = 70
c = 90
```

### Trace Table

| Step | Statement | a | b | c | total | rata |
|---:|---|---:|---:|---:|---:|---:|
| 1 | INPUT a | 80 | - | - | - | - |
| 2 | INPUT b | 80 | 70 | - | - | - |
| 3 | INPUT c | 80 | 70 | 90 | - | - |
| 4 | total = a+b+c | 80 | 70 | 90 | 240 | - |
| 5 | rata = total/2 | 80 | 70 | 90 | 240 | 120 |

### Analisis

Expected:

```text
(80 + 70 + 90) / 3 = 80
```

Actual:

```text
240 / 2 = 120
```

### Kesimpulan

Terdapat **logical error** pada:

```text
rata = total / 2
```

Seharusnya:

```text
rata = total / 3
```

Trace table membantu menemukan kesalahan meskipun algoritma dapat dieksekusi tanpa **syntax error**.

### Perbedaan Syntax Error dan Logical Error

- **Syntax error:** kesalahan pada bentuk/aturan penulisan yang menyebabkan instruksi tidak dapat diproses sesuai sintaks bahasa.
- **Logical error:** algoritma dapat dieksekusi, tetapi logikanya menghasilkan hasil yang tidak sesuai spesifikasi.

Contoh studi kasus ini merupakan logical error karena operasi pembagian menggunakan `2`, padahal terdapat tiga nilai.

---

# 18. Studi Kasus Kesalahan Operator Kondisi

## Studi Kasus 12 — Batas Kelulusan

### Algoritma salah

```text
IF nilai > 60 THEN
    status = "Lulus"
ELSE
    status = "Tidak Lulus"
END IF
```

Spesifikasi menyatakan:

```text
nilai >= 60 → Lulus
```

### Input

```text
nilai = 60
```

### Trace Table

| Step | Statement | nilai | Condition | status |
|---:|---|---:|---|---|
| 1 | INPUT nilai | 60 | - | - |
| 2 | nilai > 60 | 60 | FALSE | - |
| 3 | status = "Tidak Lulus" | 60 | FALSE | Tidak Lulus |

### Expected vs Actual

```text
Expected : Lulus
Actual   : Tidak Lulus
```

### Kesimpulan

Kesalahan terdapat pada operator:

```text
>
```

yang seharusnya:

```text
>=
```

### Pelajaran dari Boundary Case

Kesalahan seperti ini sering hanya terlihat ketika input tepat berada di batas. Karena itu, pengujian `59`, `60`, dan `61` penting untuk kondisi kelulusan tersebut.

---

# 19. Studi Kasus Komprehensif

## Studi Kasus 13 — Sistem Penentuan Diskon Belanja

### Spesifikasi

| Total Belanja | Diskon |
|---:|---:|
| >= 1.000.000 | 20% |
| >= 500.000 | 10% |
| < 500.000 | 0% |

### Algoritma

```text
INPUT total

IF total >= 1000000 THEN
    diskon = 0.20
ELSE IF total >= 500000 THEN
    diskon = 0.10
ELSE
    diskon = 0
END IF

nilai_diskon = total * diskon
total_bayar = total - nilai_diskon

OUTPUT total_bayar
```

### Input

```text
total = 750000
```

### Trace Table

| Step | Statement | Total | Diskon | Nilai Diskon | Total Bayar | Condition |
|---:|---|---:|---:|---:|---:|---|
| 1 | INPUT total | 750.000 | - | - | - | - |
| 2 | total >= 1.000.000 | 750.000 | - | - | - | FALSE |
| 3 | total >= 500.000 | 750.000 | - | - | - | TRUE |
| 4 | diskon = 0.10 | 750.000 | 0.10 | - | - | TRUE |
| 5 | nilai_diskon = total × diskon | 750.000 | 0.10 | 75.000 | - | - |
| 6 | total_bayar = total - nilai_diskon | 750.000 | 0.10 | 75.000 | 675.000 | - |
| 7 | OUTPUT total_bayar | 750.000 | 0.10 | 75.000 | 675.000 | - |

### Hasil

```text
Total Bayar = Rp675.000
```

### Cara Berpikir pada Kasus Komprehensif

Kasus ini menggabungkan:

- input,
- percabangan bertingkat,
- operator relasional,
- assignment,
- operasi aritmatika,
- output.

Tracing harus dilakukan secara berurutan. Pertama tentukan kategori diskon, kemudian hitung nilai diskon, lalu hitung total bayar.

---

# 20. Studi Kasus Pencarian Nilai Terbesar

## Studi Kasus 14 — Mencari Nilai Maksimum

### Algoritma

```text
INPUT a
INPUT b
INPUT c

maks = a

IF b > maks THEN
    maks = b
END IF

IF c > maks THEN
    maks = c
END IF

OUTPUT maks
```

### Input

```text
a = 75
b = 90
c = 80
```

### Trace Table

| Step | Statement | a | b | c | maks | Condition |
|---:|---|---:|---:|---:|---:|---|
| 1 | INPUT a | 75 | - | - | - | - |
| 2 | INPUT b | 75 | 90 | - | - | - |
| 3 | INPUT c | 75 | 90 | 80 | - | - |
| 4 | maks = a | 75 | 90 | 80 | 75 | - |
| 5 | b > maks | 75 | 90 | 80 | 75 | TRUE |
| 6 | maks = b | 75 | 90 | 80 | 90 | - |
| 7 | c > maks | 75 | 90 | 80 | 90 | FALSE |
| 8 | OUTPUT maks | 75 | 90 | 80 | 90 | - |

### Hasil

```text
Nilai maksimum = 90
```

### Konsep yang Ditunjukkan

Variabel `maks` berfungsi sebagai nilai maksimum sementara. Nilainya dapat berubah selama algoritma berjalan. Trace table memperlihatkan bahwa:

```text
maks = 75
```

kemudian berubah menjadi:

```text
maks = 90
```

setelah kondisi `b > maks` bernilai `TRUE`.

---

# 21. Studi Kasus Pencarian pada Array

## Studi Kasus 15 — Linear Search

**Linear search** menelusuri data satu per satu sampai target ditemukan atau seluruh data selesai diperiksa.

### Algoritma

```text
data = [10, 25, 30, 45, 50]
target = 30

ditemukan = FALSE

FOR i = 0 TO 4

    IF data[i] == target THEN
        ditemukan = TRUE
        posisi = i
        BREAK
    END IF

END FOR

OUTPUT ditemukan
OUTPUT posisi
```

### Trace Table

| Iterasi | i | data[i] | target | data[i] == target | ditemukan | posisi |
|---:|---:|---:|---:|---|---|---:|
| Awal | - | - | 30 | - | FALSE | - |
| 1 | 0 | 10 | 30 | FALSE | FALSE | - |
| 2 | 1 | 25 | 30 | FALSE | FALSE | - |
| 3 | 2 | 30 | 30 | TRUE | TRUE | 2 |

### Kesimpulan

```text
Data ditemukan
Posisi = 2
```

Pada contoh ini, pencarian berhenti ketika target ditemukan pada indeks `2` karena terdapat instruksi `BREAK`.

---

# 22. Strategi Pengujian dengan Trace Table

Trace table sebaiknya tidak hanya menggunakan satu input.

Gunakan kombinasi berikut.

## 22.1 Normal Case

Input berada pada kondisi normal.

Contoh:

```text
nilai = 75
```

## 22.2 Boundary Case

Input berada tepat pada batas.

Contoh:

```text
nilai = 60
```

## 22.3 Below Boundary

```text
nilai = 59
```

## 22.4 Above Boundary

```text
nilai = 61
```

## 22.5 Extreme Case

Gunakan nilai sangat kecil atau sangat besar sesuai spesifikasi.

## 22.6 Invalid Input

Gunakan input yang tidak sesuai aturan jika algoritma memiliki validasi.

### Mengapa Banyak Test Case?

Satu input hanya menunjukkan satu jalur eksekusi. Algoritma yang mempunyai percabangan dapat mempunyai beberapa jalur. Oleh karena itu, pengujian perlu mencakup kondisi yang relevan agar kesalahan pada jalur lain tidak terlewatkan.

---

# 23. Template Trace Table

## Template Dasar

| Step | Statement | Var 1 | Var 2 | Var 3 | Condition | Output |
|---:|---|---|---|---|---|---|

## Template Assignment

| Step | Statement | Sebelum | Operasi | Sesudah |
|---:|---|---|---|---|

Template ini cocok ketika fokus utama adalah perubahan sebuah variabel akibat assignment.

## Template IF–ELSE

| Step | Statement | Variabel | Condition | TRUE/FALSE | Output |
|---:|---|---|---|---|---|

Template ini membantu memisahkan kondisi dengan hasil assignment pada cabang.

## Template FOR

| Iterasi | Counter | Kondisi | Nilai Sebelum | Proses | Nilai Sesudah | Output |
|---:|---:|---|---:|---|---:|---|

## Template WHILE

| Iterasi | Nilai Awal | Kondisi | Proses | Nilai Akhir | Output |
|---:|---:|---|---|---:|---|

### Prinsip Penggunaan Template

Template tidak harus digunakan secara kaku. Mahasiswa dapat menyesuaikan kolom dengan algoritma yang dianalisis. Variabel yang tidak berubah atau tidak relevan tidak perlu dicantumkan jika tidak membantu proses verifikasi.

---

# 24. Checklist Verifikasi Algoritma

Gunakan checklist berikut setelah tracing:

- [ ] Semua input sudah diberikan.
- [ ] Semua variabel sudah diidentifikasi.
- [ ] Nilai awal variabel sudah benar.
- [ ] Setiap assignment sudah ditelusuri.
- [ ] Setiap operator aritmatika sudah dihitung.
- [ ] Setiap kondisi sudah dievaluasi.
- [ ] Semua cabang yang relevan sudah diuji.
- [ ] Setiap iterasi loop sudah ditelusuri.
- [ ] Kondisi berhenti loop sudah diverifikasi.
- [ ] Output aktual sudah dicatat.
- [ ] Output aktual dibandingkan dengan expected output.
- [ ] Tidak terdapat logical error.
- [ ] Boundary value sudah diuji untuk kondisi yang memiliki batas.

Checklist membantu memastikan bahwa proses verifikasi tidak berhenti hanya karena output terlihat benar. Seluruh jalur dan kondisi yang relevan tetap perlu diperiksa.

---

# 25. Aktivitas Pembelajaran di Kelas

## Aktivitas 1 — Tracing Manual

Dosen memberikan pseudocode sederhana.

Mahasiswa:

1. menentukan variabel,
2. membuat trace table,
3. memberikan input,
4. melakukan tracing,
5. menentukan output.

Tujuan aktivitas adalah membangun kebiasaan membaca algoritma secara sistematis.

## Aktivitas 2 — Trace Table Berpasangan

Setiap pasangan mahasiswa:

- mahasiswa A membuat algoritma,
- mahasiswa B melakukan tracing,
- keduanya membandingkan expected dan actual output.

Aktivitas ini melatih mahasiswa melihat algoritma dari dua sudut: sebagai pembuat dan sebagai pemeriksa.

## Aktivitas 3 — Debugging

Dosen memberikan algoritma yang sengaja mengandung logical error.

Mahasiswa harus:

1. melakukan tracing,
2. menemukan baris kesalahan,
3. menjelaskan mengapa salah,
4. memperbaiki algoritma,
5. melakukan tracing ulang.

## Aktivitas 4 — Boundary Testing

Mahasiswa membuat trace table untuk:

```text
x < 10
x <= 10
x > 10
x >= 10
```

dengan input:

```text
9, 10, 11
```

Fokus aktivitas adalah melihat secara langsung perbedaan operator kondisi ketika input berada di bawah, tepat pada, dan di atas batas.

---

# 26. Latihan Mandiri

## Latihan 1 — Nilai Absolut

Buat trace table untuk:

```text
INPUT x

IF x < 0 THEN
    x = x * -1
END IF

OUTPUT x
```

Uji:

```text
x = -15
x = 0
x = 15
```

### Fokus

Perhatikan perubahan nilai `x` ketika kondisi bernilai `TRUE` dan ketika kondisi bernilai `FALSE`.

---

## Latihan 2 — Bilangan Ganjil/Genap

```text
INPUT n

IF n MOD 2 == 0 THEN
    status = "Genap"
ELSE
    status = "Ganjil"
END IF

OUTPUT status
```

Uji:

```text
n = 8
n = 7
n = 0
```

### Fokus

Perhatikan hasil `MOD 2` dan hubungan hasil tersebut dengan kondisi `== 0`.

---

## Latihan 3 — Penjumlahan Loop

```text
sum = 0

FOR i = 1 TO 10
    sum = sum + i
END FOR

OUTPUT sum
```

Buat trace table lengkap.

### Fokus

Catat setiap perubahan `i`, `sum` sebelum proses, perhitungan, dan `sum` sesudah proses.

---

## Latihan 4 — Faktorial

```text
INPUT n

faktorial = 1

FOR i = 1 TO n
    faktorial = faktorial * i
END FOR

OUTPUT faktorial
```

Uji:

```text
n = 5
```

### Fokus

Perhatikan bahwa nilai `faktorial` berubah pada setiap iterasi.

---

## Latihan 5 — Mencari Nilai Minimum

Buat algoritma dan trace table untuk mencari nilai terkecil dari tiga bilangan.

Uji:

```text
10, 5, 8
5, 5, 8
-2, 5, 8
```

### Fokus

Pastikan algoritma tetap dapat menangani nilai yang sama dan nilai negatif.

---

# 27. Tugas Studi Kasus

Mahasiswa diminta memilih satu kasus:

1. Sistem penilaian mahasiswa.
2. Sistem diskon toko.
3. Sistem tarif parkir.
4. Sistem perhitungan gaji.
5. Sistem penentuan biaya pengiriman.
6. Sistem validasi password.
7. Sistem pencarian data.
8. Sistem perhitungan cicilan.
9. Sistem perhitungan tarif listrik.
10. Sistem pemesanan tiket.

## Ketentuan Tugas

Mahasiswa harus menghasilkan:

1. Deskripsi masalah.
2. Input.
3. Proses.
4. Output.
5. Pseudocode.
6. Minimal 3 skenario pengujian.
7. Trace table untuk setiap skenario.
8. Expected output.
9. Actual output.
10. Kesimpulan kebenaran algoritma.
11. Jika ditemukan error, lakukan perbaikan dan tracing ulang.

### Alur Pengerjaan Tugas

```text
Deskripsi Masalah
       ↓
Input / Proses / Output
       ↓
Pseudocode
       ↓
Penentuan Test Case
       ↓
Trace Table
       ↓
Expected vs Actual
       ↓
Identifikasi Error
       ↓
Perbaikan
       ↓
Tracing Ulang
       ↓
Kesimpulan
```

---

# 28. Rubrik Penilaian

| Komponen | Bobot |
|---|---:|
| Identifikasi input/output | 10% |
| Identifikasi variabel | 10% |
| Pseudocode | 15% |
| Struktur trace table | 15% |
| Ketepatan tracing | 25% |
| Pengujian boundary/case | 10% |
| Identifikasi logical error | 10% |
| Kesimpulan | 5% |
| **Total** | **100%** |

### Interpretasi Komponen Penilaian

- **Identifikasi input/output:** ketepatan menentukan data masuk dan hasil yang diharapkan.
- **Identifikasi variabel:** ketepatan menentukan variabel yang diperlukan dan dilacak.
- **Pseudocode:** ketepatan menggambarkan langkah algoritma.
- **Struktur trace table:** kelengkapan dan kesesuaian kolom.
- **Ketepatan tracing:** ketepatan mengikuti setiap statement dan perubahan nilai.
- **Pengujian boundary/case:** kelengkapan pengujian kasus normal dan batas yang relevan.
- **Identifikasi logical error:** kemampuan menemukan kesalahan logika berdasarkan hasil tracing.
- **Kesimpulan:** kemampuan menentukan kesesuaian algoritma dengan spesifikasi.

---

# 29. Ringkasan Materi

Trace table merupakan teknik **manual execution** untuk menelusuri algoritma berdasarkan input tertentu. Proses dilakukan dengan membaca algoritma secara berurutan, mencatat nilai variabel, mengevaluasi kondisi, mengikuti cabang yang sesuai, serta mencatat setiap iterasi perulangan.

Pola umum tracing:

```text
INPUT
  ↓
INITIALIZATION
  ↓
PROCESS
  ↓
CONDITION
  ↓
UPDATE VARIABLE
  ↓
REPEAT / CONTINUE
  ↓
OUTPUT
```

Konsep terpenting:

> **Trace table tidak hanya menjawab "apa hasil algoritma?", tetapi menjelaskan "bagaimana algoritma sampai menghasilkan hasil tersebut?"**

Dengan kata lain, trace table merupakan alat untuk membuat keadaan internal algoritma terlihat pada setiap tahap eksekusi.

---

# 30. Kesimpulan Pembelajaran

Dengan trace table, mahasiswa dapat melakukan verifikasi algoritma secara sistematis sebelum algoritma diterjemahkan ke dalam bahasa pemrograman. Teknik ini sangat efektif untuk memahami sequence, selection, iteration, operator logika, perubahan variabel, boundary condition, serta menemukan **logical error**.

Urutan kerja yang direkomendasikan:

```text
Pahami masalah
      ↓
Identifikasi input/output
      ↓
Baca pseudocode
      ↓
Identifikasi variabel
      ↓
Tentukan test case
      ↓
Buat trace table
      ↓
Telusuri statement satu per satu
      ↓
Evaluasi kondisi
      ↓
Telusuri setiap iterasi
      ↓
Catat output aktual
      ↓
Bandingkan dengan expected output
      ↓
Validasi / perbaiki algoritma
```

## Prinsip Utama

**Algoritma yang dapat dijalankan belum tentu algoritma yang benar.**

Trace table membantu membuktikan bahwa **alur logika dan hasil algoritma sesuai dengan spesifikasi masalah**.

Dengan menguasai teknik ini, mahasiswa memiliki dasar yang kuat untuk melakukan pemeriksaan algoritma secara manual, memahami hubungan antara input–proses–output, serta menemukan kesalahan logika sebelum algoritma diimplementasikan dalam bahasa pemrograman.
