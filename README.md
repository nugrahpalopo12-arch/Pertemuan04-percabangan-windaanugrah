# 📚 Pemrograman Basis Data — Pertemuan 4

## Struktur Kontrol Percabangan IF-THEN-ELSE pada MySQL

> **Nama:** Winda Anugrah  
> **NIM:** IK2411016  
> **Dosen:** Abdul Malik, S.Kom., M.Cs.  
> **Mata Kuliah:** Pemrograman Basis Data — 2025/2026

---

## Tentang Tugas Ini

Tugas ini mengimplementasikan struktur percabangan `IF-THEN-ELSEIF-ELSE` di dalam stored procedure MySQL. Procedure yang dibuat bernama `cek_predikat_mahasiswa`, yang secara otomatis menentukan **predikat** dan **status kelulusan** mahasiswa berdasarkan nilai yang dimasukkan.

---

## Logika yang Digunakan

```
Nilai 90–100  →  Sangat Memuaskan  →  Lulus
Nilai 80–89   →  Memuaskan         →  Lulus
Nilai 70–79   →  Baik              →  Lulus
Nilai 60–69   →  Cukup             →  Tidak Lulus
Nilai < 60    →  Kurang            →  Tidak Lulus
```

---

## Cara Pakai

**1. Jalankan script SQL di phpMyAdmin**
```
localhost/phpmyadmin → database db_percabangan → tab SQL → import file
```

**2. Panggil procedure**
```sql
CALL cek_predikat_mahasiswa(85);
-- Output: nilai=85 | predikat=Memuaskan | status=Lulus

CALL cek_predikat_mahasiswa(60);
-- Output: nilai=60 | predikat=Cukup | status=Tidak Lulus
```

---

## Struktur Repository

```
pbasisdata-pertemuan4-winda-IK2411016/
│
├── 📄 README.md
├── 📁 kode_sql/
│   └── kuis_pertemuan4_IK2411016.sql
└── 📁 laporan/
    └── laporan_analisis_pertemuan4_IK2411016.pdf
```

---

## Hasil Pengujian

| Input | Predikat | Status |
|:-----:|:--------:|:------:|
| 85 | Memuaskan | ✅ Lulus |
| 60 | Cukup | ❌ Tidak Lulus |
