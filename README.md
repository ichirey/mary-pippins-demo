# Mary Pippins Recruitment OS — Live Demo (Deploy ke Vercel)

Folder ini isinya:
- `index.html` — dashboard-nya (frontend)
- `api/claude.js` — backend kecil (serverless function) yang manggil Claude API dengan aman
- `.env.example` — contoh nama environment variable yang perlu diisi di Vercel

Karena ada backend di dalamnya, **ini gak bisa di-deploy ke GitHub Pages** (GitHub Pages cuma buat file statis). Harus lewat Vercel (atau Railway/Render, tapi Vercel paling gampang buat kasus kayak gini).

## Langkah Deploy (± 5 menit)

1. **Push folder ini ke GitHub**
   - Buat repo baru di GitHub, misal `mary-pippins-demo`
   - Upload semua isi folder ini (index.html, folder api/, README.md) ke repo itu
   - JANGAN upload API key kamu ke mana pun di dalam kode

2. **Import ke Vercel**
   - Buka vercel.com, login pakai akun kamu yang biasa
   - "Add New Project" → pilih repo `mary-pippins-demo` yang baru di-push
   - Framework preset: pilih "Other" (bukan Next.js), biarkan default lainnya
   - Klik Deploy dulu (nanti error dulu gapapa, karena API key belum diisi)

3. **Isi API Key di Vercel**
   - Di project Vercel-nya → Settings → Environment Variables
   - Tambah variable baru:
     - Name: `ANTHROPIC_API_KEY`
     - Value: (API key Claude kamu, dari console.anthropic.com)
   - Save, lalu klik "Redeploy" di tab Deployments supaya env variable-nya kepakai

4. **Selesai**
   - Vercel kasih link seperti `mary-pippins-demo.vercel.app`
   - Link itu yang kamu share ke prospek — mereka bisa buka & coba AI-nya sendiri, gak butuh komputer kamu nyala atau chat Claude ini kebuka

## Kalau mau custom domain
Vercel Settings → Domains → tambahin domain kamu sendiri (misal `demo.marypippins.com.au`), tinggal arahin DNS-nya sesuai instruksi Vercel.

## Catatan biaya
Setiap pesan yang dikirim ke Claude (Copilot refresh, AI Summary, chat) itu manggil API beneran dan kena biaya kecil per pemakaian, ditagih ke akun Anthropic kamu. Untuk demo ke prospek, biayanya biasanya sangat kecil (cents), tapi kalau link-nya disebar luas/publik tanpa batas, ada baiknya nanti ditambah rate-limiting sederhana.
