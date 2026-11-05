# ED-BPT — Executive Directive & Budget Performance Tracker

Aplikasi pelacak direktif dan kinerja anggaran. Frontend satu halaman (`public/index.html`),
backend Netlify Functions, database Netlify Database (Drizzle ORM).

## Struktur
- `public/index.html` — aplikasi
- `netlify/functions/state.mts` — API `/api/state` (muat/simpan data)
- `netlify/functions/drive.mts` — placeholder Google Drive
- `lib/auth.ts` — pemeriksaan kode akses
- `db/schema.ts` — skema tabel; migrasi di `netlify/database/migrations`

## Deploy
1. Push repo ini ke GitHub (disarankan **private**).
2. Di Netlify: Add new site → Import from Git → pilih repo ini.
3. Aktifkan Netlify Database untuk situs tersebut.
4. Site configuration → Environment variables: tambahkan `APP_ACCESS_CODE`.
5. Deploy, buka situs, masukkan kode akses saat diminta.

## Pengembangan lokal
```
npm install
cp .env.example .env   # isi APP_ACCESS_CODE
npx netlify dev
```
Ubah skema di `db/schema.ts`, lalu `npm run db:generate` untuk membuat migrasi baru.

## Catatan keamanan
- Jangan commit `.env` atau data asli ke repo.
- Satu kode akses dipakai bersama; login di aplikasi belum diverifikasi server.
