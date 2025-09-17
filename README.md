# 🐉 NetHunter untuk Realme C15 (RMX2180) UI2 Mediatek  
<img align='right' src='image/kali.png' width='220px' alt="Kali Linux Logo">

Custom ROM + Kernel NetHunter untuk perangkat **Realme C15 UI2 (RMX2180)** berbasis **Mediatek**, dirancang untuk mendukung berbagai fitur penetration testing dan perangkat eksternal.

### 🔧 Fitur Kernel NetHunter

1. Kernel telah mendukung **NetHunter** secara penuh.
2. Sudah terintegrasi dengan [**SukiSU v3.1.9**](https://github.com/SukiSU-Ultra/SukiSU-Ultra).
3. Aplikasi sistem yang tidak diperlukan telah dihapus untuk meningkatkan performa dan efisiensi.
4. Mendukung chipset USB Wi-Fi eksternal berikut:
   - **RTL8188EUS**, **RTL8188EU**, **RTL8188ETV**
   - **RTL8812AU/21AU**, **RTL8814AU**  
   *(Pengujian baru dilakukan pada RTL8188EUS)*
5. Mendukung **injeksi paket/frame**, saat ini hanya berfungsi untuk adaptor Wi-Fi eksternal.
6. Dukungan untuk perangkat eksternal seperti:
   - **Bluetooth (BT)**
   - **Radio (RL)**
   - **DVB**  
   *(Masih memerlukan pengujian lebih lanjut)*
7. Dukungan untuk perangkat **HID (Human Interface Device)**.
8. Mendukung **CAN** untuk integrasi dengan **CAR Arsenal**.

### 📦 Cara Instalasi

1. Unduh [NetHunter ROM](https://github.com/Frostleaft07/Nethunter_C15/releases/download/latest/RealmeUI2_Debloat_v2.2_Sukisu_Mediatek_Nethunter+modules_RMX2185.zip)
2. Reboot ke **TWRP Recovery**
3. Flash ROM yang telah diunduh
4. Lakukan **Format Data**
5. Reboot ke sistem

### 🔐 Mengaktifkan Root untuk NetHunter

1. Buka aplikasi **SukiSU Manager**
2. Aktifkan akses root untuk **NetHunter Terminal** dan **NetHunter App**

### 🐧 Instalasi Kali RootFS

1. Buka aplikasi **NetHunter**
2. Masuk ke **Kali Chroot Manager**
3. Tekan **Install**
4. Pilih opsi **Minimal** atau **Full**  
   *(Pastikan terhubung ke internet karena akan mengunduh file rootfs)*
5. Tunggu hingga proses selesai
6. Buka **NetHunter Terminal**
7. Pilih **New Session > New bash shell**
8. Jalankan perintah berikut:
   ```bash
   cd /data/local/nhsystem
   su -c ln -s kali-arm64 kalifs
   ```
9. Selesai

### 🛠️ Cara Memperbaiki HID yang Gagal Setup

1. reset dulu usb function di usb arsenal
2. Buka terminal dan jalankan:
   ```bash
   su -c rmdir /config/usb_gadget/g1/functions/hid*
   ```
3. Buka **NetHunter App**  
   Masuk ke **USB Arsenal**  
   Pilih OS > Pilih HID > Disable ADB > Set USB Function > Done

### 📁 Cara Load Module `.ko`

1. Buka terminal
2. Masuk ke direktori:
   ```bash
   cd /system/lib/modules
   ```
3. Untuk melihat semua module:
   ```bash
   ls
   ```
4. Untuk **load** module:
   ```bash
   insmod nama.ko
   ```
   Contoh: `insmod 8188eu.ko`
5. Untuk **unload** module:
   ```bash
   rmmod nama
   ```
   Contoh: `rmmod 8188eu`

### 🛜 Untuk Benerin wifite yang stuck
1. buka terminal
2. ```
   nano +210 /sbin/airmon-ng
   ```
3. kalo belum ketemu, pencet ctrl + w, cari text `yesorno`
4. hapus text `yesorno` sama `retcode=$?` Ke `retcode=1` trus save
5. jalanin lagi wifitenya

### 🔋 batre ngaco?, kalibrasi cik
1. kalo batre sudah 100%, buka terminal
2. ```
   su -c batcal
   ```
   pilih antara:
   `A` otomatis
   `C` Langsung kalibrasi
3. reboot

   catatan: `charger harus tetep terhubung dengan hp selama proses kalibrasi sampai reboot, baru bisa dilepas`

### 📦 Daftar Modul Kernel Tambahan (Non-`.ko`)

Berikut adalah modul tambahan yang tersedia di kernel, tidak termasuk file `.ko`:

```
ath6kl_usb       ath9k_htc         bcm203x           bfusb
bpa10x           btusb             carl9170          cdc_acm
cdc_ether        ch341             ems_usb           esd_usb2
ftdi_sio         gs_usb            hub               kvaser_usb
mt7601u          mt76x0            mt76x2u           peak_usb
pl2303           r8152             rndis_host        rndis_wlan
rt2500usb        rt2800usb         rt73usb           rtl8150
rtl8187          rtl8xxxu          snd-usb-audio     ums-alauda
ums-cypress      ums-datafab       ums-freecom       ums-isd200
ums-jumpshot     ums-karma         ums-onetouch      ums-sddr09
ums-sddr55       ums-usbat         usb               usb-storage
usb_8dev         usbfs             usbhid            usbserial_generic
xpad             zd1201            zd1211rw
```

🔗 Untuk informasi lebih lanjut tentang fitur dan dokumentasi resmi, kunjungi:  
👉 [Kali NetHunter Documentation](https://www.kali.org/docs/nethunter/)
