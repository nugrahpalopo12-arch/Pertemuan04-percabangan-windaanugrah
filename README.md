Tugas Pertemuan 4 — Struktur Kontrol Percabangan

| | |
|---|---|
| **Nama** | Winda Anugrah |
| **NIM** | IK2411016 |
| **Kelas** | IK2411 |
| **Mata Kuliah** | Pemrograman Basis Data |
| **Dosen** | Abdul Malik, S.Kom., M.Cs. |
| **Judul Tugas** | Kuis/Tugas Pertemuan 4 - Struktur Kontrol Percabangan |

---

## Deskripsi Tugas

Pada tugas ini dibuat sebuah procedure MySQL bernama `cek_predikat_mahasiswa` yang digunakan untuk menentukan predikat mahasiswa berdasarkan nilai yang dimasukkan. Selain itu, procedure juga menentukan status kelulusan apakah mahasiswa dinyatakan lulus atau tidak.

Ketentuan predikat:

| Nilai | Predikat |
|-------|----------|
| 90 – 100 | Sangat Memuaskan |
| 80 – 89 | Memuaskan |
| 70 – 79 | Baik |
| 60 – 69 | Cukup |
| < 60 | Kurang |

- Jika nilai >= 70 → Status: **Lulus**
- Jika nilai < 70 → Status: **Tidak Lulus**

---

## Cara Menjalankan Script SQL

### Menggunakan phpMyAdmin (XAMPP)

1. Pastikan XAMPP sudah berjalan (Apache + MySQL aktif)
2. Buka browser, akses `http://localhost/phpmyadmin`
3. Buat database baru bernama `db_percabangan`
4. Klik tab **SQL** → **Choose File** → pilih `kuis_pertemuan4_IK2411016.sql`
5. Klik **Go** untuk menjalankan

### Menggunakan MySQL Command Line

```bash
mysql -u root -p < kode_sql/kuis_pertemuan4_IK2411016.sql
```

### Menjalankan Procedure

Setelah script dijalankan, panggil procedure dengan perintah berikut:

```sql
CALL cek_predikat_mahasiswa(85);
```

Contoh output:

```
+-------+-----------+--------+
| nilai | predikat  | status |
+-------+-----------+--------+
|    85 | Memuaskan | Lulus  |
+-------+-----------+--------+
```

---

## Kode SQL

```sql
DELIMITER //

CREATE PROCEDURE cek_predikat_mahasiswa(IN p_nilai INT)
BEGIN
    DECLARE v_predikat VARCHAR(50);
    DECLARE v_status   VARCHAR(20);

    IF p_nilai >= 90 THEN
        SET v_predikat = 'Sangat Memuaskan';
    ELSEIF p_nilai >= 80 THEN
        SET v_predikat = 'Memuaskan';
    ELSEIF p_nilai >= 70 THEN
        SET v_predikat = 'Baik';
    ELSEIF p_nilai >= 60 THEN
        SET v_predikat = 'Cukup';
    ELSE
        SET v_predikat = 'Kurang';
    END IF;

    IF p_nilai >= 70 THEN
        SET v_status = 'Lulus';
    ELSE
        SET v_status = 'Tidak Lulus';
    END IF;

    SELECT
        p_nilai    AS nilai,
        v_predikat AS predikat,
        v_status   AS status;
END //

DELIMITER ;
```

---

## Hasil Pengujian

| Pemanggilan | Nilai | Predikat | Status |
|-------------|-------|----------|--------|
| `CALL cek_predikat_mahasiswa(85)` | 85 | Memuaskan | Lulus |
| `CALL cek_predikat_mahasiswa(60)` | 60 | Cukup | Tidak Lulus |

---

## Daftar File

```
pertemuan-04-percabangan/
├── README.md
├── kode_sql/
│   └── kuis_pertemuan4_IK2411016.sql
└── laporan/
    └── laporan_analisis_pertemuan4_IK2411016.pdf
```

| File | Keterangan |
|------|------------|
| `kode_sql/kuis_pertemuan4_IK2411016.sql` | Script SQL lengkap (procedure + pengujian) |
| `laporan/laporan_analisis_pertemuan4_IK2411016.pdf` | Laporan analisis lengkap dengan screenshot |
| `README.md` | Dokumen ini |emuan04-percabangan-windaanugrah
