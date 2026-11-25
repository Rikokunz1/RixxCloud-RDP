# ⚡ RixxCloud-RDP (Fork Edition) — Free RDP 6 Jam

Repo ini yang lo **fork ke GitHub lo sendiri**. Workflow-nya nyalain Windows Server di runner GitHub Actions milik lo, bikin user RDP, buka tunnel, lalu kirim Host + Username + Password ke Telegram lo via bot **@Mycloud1221bot** (bot milik owner panel).

> ⚠️ Pakai hanya di akun/repo lo sendiri & patuhi ToS GitHub. Runner ephemeral, max ±6 jam, jangan simpan data sensitif.

## Langkah Setup (sekali aja)
1. **Fork** repo ini (tombol Fork di kanan atas GitHub)
2. Di repo fork lo: **Settings → Secrets and variables → Actions → New repository secret**, tambahkan:
   | Secret | Isi |
   |---|---|
   | `TELEGRAM_BOT_TOKEN` | Token bot dari @BotFather (punya owner panel) |
   | `NGROK_AUTH_TOKEN` | (OPSIONAL) Token ngrok — cuma dipake kalau akun ngrok lo udah add card. Tanpa ini workflow otomatis pake bore.pub gratis. |
   | `PANEL_CALLBACK_SECRET` | (Opsional) samakan dengan env panel, biar sesi muncul di RixxPanel |
3. Tab **Actions** → kalau ada peringatan kuning, klik **"I understand my workflows, go ahead and enable them"**

## Cara Jalanin RDP
1. Tab **Actions** → workflow **RixxCloud Personal RDP (Fork)** → **Run workflow**
2. Isi:
   - `telegram_chat_id`: Chat ID lo (tanya @userinfobot di Telegram, atau chat bot lalu lihat ID lo)
   - `username`: bebas, default `rixxcloud`
   - `panel_url`: (opsional) URL panel RixxCloud lo, contoh `https://rixxcloud.vercel.app`
3. Klik **Run workflow** → tunggu ±2-3 menit → cek DM bot Telegram: Host, Username, Password dikirim otomatis
4. Connect: Windows `Win+R → mstsc`, HP pake aplikasi **Windows App** → masukin host (contoh `0.tcp.ap.ngrok.io:12345`) + kredensial tadi

## Keamanan
- Password digenerate random tiap run & di-mask dari log Actions (`::add-mask::`)
- Password **nggak pernah** di-print ke log publik
- Sesi mati otomatis saat workflow selesai/timeout (±6 jam)
