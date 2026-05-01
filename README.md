# 📊 Multi-Asset RSI & MA Crossover Alerts

Sistem asisten trading otomatis berbasis **n8n** yang dirancang untuk memantau pergerakan harga aset saham (AAPL, TSLA, MSFT) dan Cryptocurrency (BTC) secara real-time. Sistem ini menghitung indikator teknikal secara mandiri menggunakan **JavaScript** dan mengirimkan sinyal beli/jual langsung ke **Telegram**.

## 🚀 Fitur Utama
- **Pemantauan Multi-Aset**: Memantau beberapa aset sekaligus dalam satu alur kerja yang terorganisir.
- **Indikator Teknikal Kustom**: Kalkulasi mandiri untuk RSI (14) dan SMA (50 & 200) menggunakan Code Node JavaScript tanpa ketergantungan library eksternal.
- **Intelijen Sinyal**: 
  - 🟢 **Golden Cross**: Deteksi sinyal Bullish (SMA 50 memotong ke atas SMA 200).
  - 🔻 **Death Cross**: Deteksi sinyal Bearish (SMA 50 memotong ke bawah SMA 200).
  - 🔵 **RSI Oversold/Overbought**: Mengidentifikasi titik jenuh harga pasar.
- **Penjadwalan Otomatis**: Berjalan otomatis setiap pagi pada jam pembukaan pasar (09:00 WIB).

## 🛠️ Arsitektur Workflow
1. **Schedule Trigger**: Menjalankan alur kerja secara terjadwal.
2. **HTTP Request**: Mengambil data harga historis yang akurat dari Yahoo Finance API.
3. **Merge & Set**: Mengelola dan menggabungkan input dari berbagai simbol aset.
4. **Code Node (JavaScript)**: "Otak" sistem yang memproses algoritma teknikal SMA & RSI.
5. **Telegram Bot**: Mengirimkan notifikasi sinyal lengkap dengan data harga terakhir ke pengguna.

## 📋 Prasyarat
- Akun [n8n](https://n8n.io/) (Self-hosted atau Cloud).
- Bot Telegram (dibuat melalui @BotFather).
- Koneksi internet untuk akses API Yahoo Finance.

## ⚙️ Cara Instalasi
1. Clone repositori ini.
2. Impor file `Asa_RSI_MA.json`
3. Konfigurasikan Chat ID dan API Token Telegram pada node Telegram.
4. Aktifkan workflow.

## 📝 Catatan Teknis
Sistem ini menggunakan parameter `range: 1y` pada permintaan API untuk memastikan data historis mencukupi bagi kalkulasi **SMA 200**. Interval waktu disesuaikan ke `1h` atau `1d` untuk menjaga stabilitas data dari server Yahoo Finance.
---
