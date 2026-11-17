# Sistem Cuti dan Tiket Pesawat

Hasil vibe coding dari list user story eksperimen 2.

| Term | User story | Fitur |
| --- | --- | --- |
| 1 | HRD manajer memilih tanggal, bulan, tahun cuti | Lihat pegawai yang mengajukan cuti, periode, lama cuti, riwayat cuti, dan sisa cuti |
| 2 | Pengguna memerlukan tiket sesuai tujuan | Cari jadwal, harga, dan maskapai; pesan tiket; batalkan pesanan |

## Menjalankan

```bash
npm install
npm start        # http://localhost:3000
npm test         # 11 test API
```

Data disimpan di memori (lihat `src/data.js`), jadi reset setiap server restart.

## API

| Method | Endpoint | Keterangan |
| --- | --- | --- |
| GET | `/api/cuti/pengajuan?tahun=&bulan=&tanggal=` | Tahun wajib, bulan dan tanggal opsional |
| GET | `/api/cuti/pegawai` | Daftar pegawai |
| GET | `/api/cuti/pegawai/:id` | Riwayat cuti dan sisa cuti tahun berjalan |
| GET | `/api/tiket/penerbangan?tujuan=` | Jadwal, maskapai, harga |
| POST | `/api/tiket/pesanan` | Body: `idPengguna`, `kodePenerbangan` |
| GET | `/api/tiket/pesanan?idPengguna=` | Pesanan pengguna |
| DELETE | `/api/tiket/pesanan/:id` | Batalkan pesanan |

## Upload ke GitHub

```bash
git init
git add .
git commit -m "Vibe coding user story term 1 dan 2"
git branch -M main
git remote add origin https://github.com/<username>/<nama-repo>.git
git push -u origin main
```

## Analisis SonarQube

SonarCloud (paling mudah): login ke sonarcloud.io dengan akun GitHub, import repo, lalu analisis berjalan otomatis (Automatic Analysis).

SonarQube lokal:

```bash
docker run -d --name sonarqube -p 9000:9000 sonarqube:community
# buka http://localhost:9000 (admin/admin), buat project dan token
npx sonar-scanner -Dsonar.host.url=http://localhost:9000 -Dsonar.token=<token>
```

Konfigurasi ada di `sonar-project.properties`.
