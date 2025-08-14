# 🍏 Appleville Bot

[Appleville Bot](https://app.appleville.xyz?ref=cme83vfj6001os61kjjg2mbqz) adalah bot otomatis berbasis Python untuk game Appleville yang mendukung multi-akun farming.
Bot ini dapat melakukan otomatisasi seperti:

- Klaim hadiah harian (Daily Reward)
- Panen otomatis saat waktu tanam selesai
- Menanam kembali benih yang habis secara otomatis
- Membeli plot baru otomatis
- Menggunakan dan membeli ramuan (modifier) otomatis
- Menukar AP (AP Exchange) otomatis
- Multi-akun dengan pengaturan fleksibel

## ✨ Fitur Utama

- **Multi Akun**: Dapat mengatur banyak akun sekaligus dalam `akun.json`
- **Auto Claim Harian**: Klaim hadiah harian setiap 24 jam
- **Auto Harvest & Replant**: Panen dan menanam ulang otomatis sesuai konfigurasi
- **Auto Buy Seeds**: Jika stok benih habis, bot akan membeli otomatis
- **Auto Buy Modifier (Fertiliser)**: Jika stok ramuan habis, bot akan membeli dan langsung menggunakannya
- **Auto Buy Plot**: Membeli lahan baru otomatis jika diaktifkan
- **Auto AP Exchange**: Menukar AP menjadi item tertentu
- **Smart Timer**: Mengatur cooldown dan menyimpan data panen di `timers.json`
- **Anti Stuck**: Membersihkan plot yang tersinkronisasi secara otomatis

## 📂 Struktur File
```
.
├── appleville_bot.py   # File utama bot
├── akun.json           # Konfigurasi akun & pengaturan
├── timers.json         # Timer tanam & cooldown (dibuat otomatis)
├── requirements.txt    # Daftar dependencies
└── README.md           # Dokumentasi ini
```

## ⚙️ Instalasi

### 1. Clone repository
```bash
git clone https://github.com/jamalnggau1/Appleville-bot
cd Appleville-bot
```

### 2. Install dependencies
```bash
pip install -r requirements.txt
```

**requirements.txt**
```
requests
colorama
```

### 3. Buat file `akun.json`
Contoh:
```json
[
  {
    "name": "Akun Utama",
    "cookie": "COOKIE_DI_SINI",
    "plants": [
      {"slotIndex": 1, "seedKey": "seed_apple", "grow_time": 3600},
      {"slotIndex": 2, "seedKey": "seed_apple", "grow_time": 3600}
    ],
    "auto_buy_plot": {"enabled": true},
    "auto_exchange": {"enabled": true, "key": "exchange_item_key"},
    "auto_fertilise": {
      "enabled": true,
      "strategies": [
        {"apply_to_slots": [1, 2], "modifierKey": "fertiliser"}
      ]
    }
  },
  {
    "name": "Akun Kedua",
    "cookie": "COOKIE_AKUN_2",
    "plants": [
      {"slotIndex": 1, "seedKey": "seed_orange", "grow_time": 7200},
      {"slotIndex": 2, "seedKey": "seed_orange", "grow_time": 7200}
    ],
    "auto_buy_plot": {"enabled": true},
    "auto_exchange": {"enabled": true, "key": "exchange_item_key_2"},
    "auto_fertilise": {
      "enabled": true,
      "strategies": [
        {"apply_to_slots": [1, 2], "modifierKey": "fertiliser"}
      ]
    }
  }
]

```

### 4. Jalankan bot
```bash
python appleville_bot.py
```

## 📝 Format `akun.json`
| Key             | Tipe     | Deskripsi |
|-----------------|----------|-----------|
| name            | String   | Nama akun (untuk log) |
| cookie          | String   | Cookie sesi akun Appleville |
| plants          | Array    | Daftar slot tanam, benih, dan waktu tumbuh |
| auto_buy_plot   | Object   | `{ "enabled": true }` untuk auto beli lahan |
| auto_exchange   | Object   | `{ "enabled": true, "key": "item_key" }` untuk auto AP exchange |
| auto_fertilise  | Object   | Strategi penggunaan ramuan |

## 📌 Tips Penggunaan
- Cookie bisa diambil dari browser saat login di Appleville
- `grow_time` dalam detik (3600 = 1 jam)
- Bot akan menyimpan waktu panen di `timers.json` agar tidak memulai dari awal saat restart
- Jika ingin menghentikan bot, tekan **CTRL + C**

## ⚠️ Disclaimer
Bot ini dibuat untuk pembelajaran & otomasi pribadi.  
Segala risiko penggunaan (termasuk banned akun) menjadi tanggung jawab pengguna.
