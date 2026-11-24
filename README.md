# ZONE HUNTER ENGINE + TELEGRAM INLINE KEYBOARD SYSTEM

Paket lengkap **ZONE HUNTER ENGINE** beserta integrasi **Telegram Inline Keyboard & Navigation System** (`python-telegram-bot` v20+ async / adapter-ready).

## Fitur Utama Telegram UI
- **Main Menu (`🟡 XAUUSD`, `₿ BTCUSD`)**: Langsung menjalankan analisis Multi-Timeframe (`H4 -> H1 -> M15 -> M5`) tanpa menu Single/Multi TF.
- **Analysis Result Menu (`🔄 Refresh`, `🔀 Ganti Market`, `⬅️ Kembali`, `🏠 Menu Utama`)**:
  - `🔄 Refresh` selalu mengirim pesan analisis baru (pesan hasil analisis lama bersifat *immutable* — tidak diedit atau dihapus).
  - `🔀 Ganti Market` menampilkan pilihan `🟡 XAUUSD` dan `₿ BTCUSD`.
  - `⬅️ Kembali` menavigasi mundur menggunakan *navigation stack* per `(chat_id, user_id)`.
  - `🏠 Menu Utama` membawa pengguna ke halaman utama.
- **Keamanan Callback**:
  - `callback_data` ringkas (`<= 64` byte).
  - Selalu menjawab *callback query*.
  - Validasi kepemilikan `user_id` dan `chat_id`.
  - Penolakan *callback* kedaluwarsa (*TTL*) dan *lock* anti-klik ganda per pengguna.
- **Pemisahan Ketat**: Logika analisis berada di `zone_hunter/`, sedangkan antarmuka Telegram berada di `telegram_ui/`. Tidak ada transaksi/eksekusi order otomatis.

## Environment Variables
- `TELEGRAM_BOT_TOKEN` — Token bot Telegram dari BotFather.
- `TWELVE_DATA_API_KEY` — API key akun Twelve Data Anda.
- `TWELVE_DATA_RATE_LIMIT_PER_MIN` — Batas request per menit paket Twelve Data Anda (default: `8`).

## Menjalankan Pengujian
```bash
pip install -r requirements.txt
pytest -v
```

## Menjalankan Bot Telegram
```bash
python run_telegram_bot.py
```
