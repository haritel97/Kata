# Kata Majlis (Netlify + Gemini)

## Struktur
- `index.html` – halaman web (3 tab: ucapan, pantun, surat rayuan)
- `netlify/functions/generate.mjs` – fungsi server yang panggil Gemini
- `netlify.toml` – tetapan Netlify

## Langkah pasang
1. Dapatkan kunci API di https://aistudio.google.com/apikey
2. Muat naik folder ini ke GitHub, kemudian di Netlify: Add new site > Import from Git.
   (Atau Netlify CLI: `npm i -g netlify-cli`, `netlify login`, `netlify deploy --prod`)
3. Netlify > Site configuration > Environment variables, tambah:
   - `GEMINI_API_KEY` = kunci anda
   - `GEMINI_MODEL` (pilihan) = nama model semasa, lalai `gemini-2.5-flash`
4. Deploy semula. Siap.

## Uji di komputer
`netlify dev` (letak kunci dalam fail `.env`: GEMINI_API_KEY=...)

## Bayaran
Dalam `index.html`, tukar `PAY_URL` kepada pautan ToyyibPay/Billplz anda.

## Nota penting
- Had percuma 3/hari disimpan dalam pelayar, jadi pengguna boleh mengelaknya. Cukup untuk fasa uji.
  Untuk had sebenar, tambah log masuk atau kod akses selepas bayaran (disahkan di server).
- Fungsi ada had kasar 30 permintaan/jam/IP dan prompt dibina di server supaya endpoint
  tidak boleh digunakan sebagai chatbot percuma.
- Tetapkan had perbelanjaan/kuota di Google AI Studio supaya kos terkawal.
