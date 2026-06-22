===========================================================================
OWASP ZAP + OWASP Juice Shop
===========================================================================

NAMA 
-------------
  - Annaufal Afif Seno     


TOPIK / TOOL
------------
  Tool   : OWASP ZAP (Zed Attack Proxy) v2.17.0
  Target : OWASP Juice Shop v20.0.0 (http://127.0.0.1:3000)
  Proxy  : 127.0.0.1:8090
  OS     : Windows 11 | Browser: Mozilla Firefox 150.0.3

===========================================================================
  STRUKTUR FOLDER
===========================================================================

  NamaKelompok_ZAP/

  ├── evidence/
  │   ├── screenshot_proxy_setting.png   → Bukti konfigurasi proxy ZAP & Firefox
  │   ├── screenshot_http_history.png    → Bukti tab History ZAP menangkap traffic
  │   ├── screenshot_finding_1.png       → Bukti alert: Absence of Anti-CSRF Tokens
  │   ├── screenshot_finding_2.png       → Bukti alert: CSP Wildcard Directive
  │   └── screenshot_finding_3.png       → Bukti alert: Application Error Disclosure
  ├── traffic/
  │   └── catatan_request_response.txt  → Catatan manual request & response HTTP
  └── README.txt                         → File ini

===========================================================================
  DESKRIPSI ISI FILE
===========================================================================

1. Laporan_Praktikum.pdf
   Laporan lengkap praktikum mencakup:
   - Latar belakang dan ruang lingkup pengujian
   - Lingkungan dan konfigurasi praktikum
   - Langkah konfigurasi proxy ZAP dan Firefox
   - Tabel endpoint yang dieksplorasi (14 endpoint)
   - Tiga temuan keamanan utama beserta bukti teknis
   - Validasi manual (Missing Cookie Security Flags)
   - Rekomendasi perbaikan
   - Kesimpulan dan daftar pustaka

2. Slide_Presentasi.pdf
   Slide ringkasan hasil praktikum untuk presentasi kelas,
   mencakup temuan utama, bukti, dan rekomendasi.

3. evidence/screenshot_proxy_setting.png
   Tangkapan layar yang menunjukkan:
   - Konfigurasi Local Proxies di OWASP ZAP (127.0.0.1:8090)
   - Konfigurasi Manual Proxy di Firefox (127.0.0.1:8090)

4. evidence/screenshot_http_history.png
   Tangkapan layar tab History ZAP yang memperlihatkan request
   HTTP dari Firefox tertangkap oleh proxy ZAP.

5. evidence/screenshot_finding_1.png
   Tangkapan layar alert ZAP: "Absence of Anti-CSRF Tokens"
   - Risk: Medium | CWE-352 | Endpoint: /profile

6. evidence/screenshot_finding_2.png
   Tangkapan layar alert ZAP: "CSP: Wildcard Directive"
   - Risk: Medium | CWE-693 | Endpoint: /profile
   - Directive bermasalah: script-src 'self' 'unsafe-eval'

7. evidence/screenshot_finding_3.png
   Tangkapan layar alert ZAP: "Application Error Disclosure"
   - Risk: Low | CWE-550 | Endpoint: /api
   - Evidence: <title>Error: Unexpected path: /api</title>

8. traffic/catatan_request_response.txt
   Catatan manual seluruh request dan response HTTP yang
   tertangkap ZAP selama sesi eksplorasi, mencakup:
   - 16 pasang request/response
   - Header HTTP lengkap
   - Body request/response (ringkasan)
   - Anotasi temuan keamanan pada request relevan

===========================================================================
  RINGKASAN TEMUAN KEAMANAN
===========================================================================

  No | Temuan                       | Risk   | CWE | Endpoint
  ---+------------------------------+--------+-----+--------------------
  1  | Absence of Anti-CSRF Tokens  | Medium | 352 | /profile
  2  | CSP: Wildcard Directive      | Medium | 693 | /profile
  3  | Application Error Disclosure | Low    | 550 | /api
  +  | Missing Cookie Flags         | Medium | —   | /profile (manual)

===========================================================================
  PERNYATAAN ETIK
===========================================================================

  Seluruh pengujian dalam praktikum ini dilakukan:
  ✔ Hanya pada lingkungan lokal (localhost) yang terisolasi
  ✔ Menggunakan aplikasi latihan OWASP Juice Shop
  ✔ Dengan metode passive scan dan eksplorasi manual
  ✔ Tanpa brute force, DoS, atau eksploitasi aktif
  ✔ Tanpa menyentuh sistem publik atau jaringan kampus
  ✔ Sesuai batasan etik yang ditetapkan dosen pengampu

===========================================================================
  CATATAN TEKNIS
===========================================================================

  - Juice Shop dijalankan via Docker pada port 3000
  - ZAP dikonfigurasi pada port 8090 (bukan default 8080)
  - Sertifikat ZAP telah diimpor ke Firefox untuk intercept HTTPS
  - Semua traffic direkam menggunakan fitur History & Search ZAP
  - Validasi manual dilakukan melalui tab Response di ZAP

===========================================================================
  END OF README
===========================================================================
