<div align="center">
<img width="1000" height="1000" alt="SilentDeployer logo" src="https://github.com/user-attachments/assets/a3b9fd4f-1a9a-48f1-93c2-3ed31c4defaa" />

# SilentDeployer

Enterprise-Grade Zero-Touch Deployment Utility for Windows

</div>

SilentDeployer adalah utilitas otomasi instalasi perangkat lunak berbasis antarmuka grafis (GUI) Python yang dirancang khusus untuk lingkungan IT Enterprise. Aplikasi ini mengorkestrasi mass-deployment pada unit komputer/laptop baru (Fresh Install Windows) dengan menghasilkan dan mengeksekusi batch script secara 100% senyap di latar belakang.

(Proyek ini awalnya dikembangkan sebagai solusi dunia nyata untuk menangani tantangan deployment ratusan PC pada lingkungan manufaktur skala besar selama masa Praktik Kerja Lapangan).

✨ Fitur Utama (Core Features)

Zero-Touch Execution: Mengeksekusi antrean instalasi (.exe, .msi, dan Winget) secara senyap menggunakan parameter Silent Install (/S, /qn, /VERYSILENT) yang terintegrasi dalam JSON Database.

Dynamic Drive Resolution (Flashdisk-Ready): Arsitektur sistem secara dinamis mendeteksi dan menyesuaikan huruf drive (C:, D:, F:), membuat aplikasi ini 100% Portable untuk offline deployment via Flashdisk tanpa mematahkan path instalasi.

UAC Pre-Elevation Manifest: Dibangun dengan manifes uac_admin=True pada tingkat kompilator. Aplikasi secara otomatis meminta hak Administrator (SmartScreen) di awal, mencegah Access Denied pada subprocess dan menjaga integritas Working Directory OS.

Smart User Override: Menyediakan antarmuka tabel interaktif untuk System Administrator agar dapat mengedit argumen instalasi secara real-time (sangat berguna untuk installer non-standar/bandel).

Live Script Preview: Memvisualisasikan batch script yang di-generate secara instan sebelum dieksekusi, memastikan transparansi penuh dan keamanan kode.

🛠️ Arsitektur & Teknologi

Bahasa Utama: Python 3.11+

GUI Framework: CustomTkinter

Executable Build: PyInstaller (dengan UAC Manifest)

Package Manager: Terintegrasi penuh dengan Windows Package Manager (Winget).

Data Storage: JSON (Sesi Lokal persisten & Database Parameter Installer).

⚙️ Cara Penggunaan (Deployment Guide)

Persiapan (Untuk IT Administrator)

Unduh rilis terbaru SilentDeployer.exe dan database.json dari menu Releases.

Masukkan ke dalam satu folder utama di Flashdisk IT Anda.

Buat sub-folder (misal: Installers) dan masukkan semua file mentah .exe / .msi (Chrome, VLC, Office ODT, dll) ke dalamnya.

Eksekusi di Mesin Klien (Windows 10 / 11)

Colokkan Flashdisk ke komputer target.

Klik ganda SilentDeployer.exe (Setujui prompt Administrator UAC).

Tambahkan aplikasi ke dalam antrean (melalui opsi Browse File atau masukkan ID Winget).

Klik Install. Seluruh proses akan berjalan di latar belakang (subprocess) tanpa mengganggu layar (Zero Interruptions).

📝 Catatan Troubleshooting Enterprise (Field-Tested)

Aplikasi ini telah diuji di lapangan pada perangkat Fresh Install. Berikut adalah catatan penting dari hasil UAT (User Acceptance Testing):

Winget Crash (Exit Code -1073741819) pada Windows 11 Baru:
Ini bukan bug skrip. Pada Fresh Install Windows 11, komponen "App Installer" bawaan pabrik Microsoft masih sangat usang atau tertahan EULA awal. Solusi: Buka Microsoft Store -> Library -> klik Update All sebelum menggunakan Winget.

Exit Code 128 (Contoh: VLC Media Player):
Ini adalah Expected Behavior (ERROR_WAIT_NO_CHILDREN) jika skrip mencoba mengeksekusi Post-Kill pada aplikasi yang memang tidak terbuka pasca-instalasi, atau jika OneDrive memblokir pembuatan shortcut di Desktop. Aplikasi tetap terinstal dengan sukses.

Antivirus Enterprise (ESET, Kaspersky, Symantec):
Selalu gunakan file ekspor Custom MSI dari konsol server pusat (misal: ESET Protect). Installer publik dari internet akan memblokir perintah CLI silent demi keamanan anti-malware.

👨‍💻 Pengembang

Dikembangkan oleh [NAMA ANDA DI SINI] Proyek ini merupakan dedikasi untuk mempermudah pekerjaan IT Support di seluruh dunia, membuktikan bahwa utilitas internal dapat dibuat tangguh (robust), portabel, dan aman dari anomali sistem operasi modern.
