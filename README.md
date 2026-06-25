```text
 ██████╗██╗      ██████╗ ██╗   ██╗██████╗     
██╔════╝██║     ██╔═══██╗██║   ██║██╔══██╗    
██║     ██║     ██║   ██║██║   ██║██║  ██║    
██║     ██║     ██║   ██║██║   ██║██║  ██║   
╚██████╗███████╗╚██████╗╚██████╔╝██████╔╝    
 ╚═════╝╚══════╝ ╚═════╝ ╚═════╝╚═════╝     

██████╗ ██████╗ ███╗   ███╗██████╗ ██╗   ██╗████████╗██╗███╗   ██╗ ██████╗
██╔════╝██╔═══██╗████╗ ████║██╔══██╗██║   ██║╚══██╔══╝██║████╗  ██║██╔════╝
██║     ██║   ██║██╔████╔██║██████╔╝██║   ██║   ██║   ██║██╔██╗ ██║██║  ███╗
██║     ██║   ██║██║╚██╔╝██║██╔═══╝ ██║   ██║   ██║   ██║██║╚██╗██║██║   ██║
╚██████╗╚██████╔╝██║ ╚═╝ ██║██║     ╚██████╔╝   ██║   ██║██║ ╚████║╚██████╔╝
 ╚═════╝ ╚═════╝╚═╝     ╚═╝╚═╝      ╚═════╝    ╚═╝   ╚═╝╚═╝  ╚═══╝ ╚═════╝

██╗    ██╗ ██████╗ ██████╗ ██████╗ ██████╗ ██████╗ ███████╗███████╗███████╗
██║    ██║██╔═══██╗██╔══██╗██╔══██╗██╔══██╗██╔══██╗██╔════╝██╔════╝██╔════╝
██║ █╗ ██║██║   ██║██████╔╝██║  ██║██████╔╝██████╔╝█████╗  ███████╗███████╗
██║███╗██║██║   ██║██╔══██╗██║  ██║██╔═══╝ ██╔══██╗██╔════╝╚════██║╚════██║
╚███╔███╔╝╚██████╗██║  ██║██████╔╝██║     ██║  ██║███████╗███████║███████║
 ╚══╝╚══╝  ╚═════╝╚═╝  ╚═╝╚═════╝ ╚═╝     ╚═╝  ╚═╝╚══════╝╚══════╝╚══════╝




[ TYPE: ENTERPRISE-READY ] [ ARCHITECTURE: MODULAR DOCKER CONTAINERS ]

🌐 MINGGU 1: FONDASI ARSITEKTUR & PROTOKOL ISOLASI
[ PHASE 01 / ACT 01: INITIALIZE ]
Repositori ini memuat progress tugas kelompok Cloud Computing untuk Minggu pertama
Fokus utama pada fase ini adalah meninggalkan metode legacy all-in-one server dan mulai
mengadopsi arsitektur cloud modern dengan pemisahan layer menggunakan Docker, serta
menerapkan network isolation protocols untuk keamanan data antar-container.


🏗️ ARSITEKTUR SISTEM (WEEK 1) - [ VISUALISASI_CYBER_STACK.TXT ]
Arsitektur ini didesain agar App Layer dan Database Layer tidak dapat "saling melihat"
secara langsung dari jaringan publik, memastikan data integrity dan attack vector reduction.




========================================================
                      [ PUBLIC_ACCESS ]
                           │
                           │ PORT: 80 / 8080
                           ▼
    ██████████████████████████████████████████████████████
    █                       [ DOCKER_HOST ]               █
    █======================================================█
    █                      [ NETWORKS ]                    █
    █                                                      █
    █   +------------+                    +------------+   █
    █   [  FRONTEND  ]──► [ FRONTEND-NET ] ◄──[BACKEND]    █
    █   [ WORDPRESS  ]        (PUBLIC)        [ (N/A) ]    █
    █   +------------+                    +------------+   █
    █          ▲                                 ▲         █
    █          │                                 │         █
    █          └────────────────────┐            │         █
    █                               │            │         █
    █                       +------------+  +------------+ █
    █    [ (N/A) ] ◄───────[  BACKEND  ] ──► [  DATABASE ] █
    █                      [ (PRIVATE) ]     [ (MARIADB) ] █
    █                       +------------+  +------------+ █
    █                                            ▲         █
    █                                            │         █
    █                                   +------------+     █
    █                                   [ DATA VOL. ]      █
    █                                   [ PERSISTENT ]     █
    █                                   +------------+     █
    ========================================================



✅ TARGET CAPAIAN - [ CHECKLIST ]
[x] [ 010 ] PROJECT_STRUCTURE_GIT: Membuat struktur folder project dan inisialisasi
                                   repositori Git.

[x] [ 110 ] APP_LAYER_WP: Menyusun container menggunakan image resmi WordPress.

[x] [ 111 ] DB_LAYER_SQL: Menyusun container database (MySQL/MariaDB)
                          dengan Docker Volumes untuk memastikan persistensi data.

[x] [ 011 ] NETWORK_ISOLATION: Membuat custom docker network (frontend-net dan backend-net)
                               untuk memastikan isolasi penuh antar-container.


***

## 🚀 MINGGU 2: OPTIMASI PERFORMA & OBJECT STORAGE

### `[ PHASE 02 / ACT 02: OPTIMIZE & STORE ]`

Melanjutkan fondasi arsitektur dasar terisolasi, fase kedua ini berfokus pada peningkatan
performa aplikasi (*caching layer*) dan efisiensi penyimpanan (*decoupling storage layer*).
Seluruh pengerjaan taktis pada fase ini juga disinkronisasikan dengan standar kompetensi
kelas cloud computing dari *bisa.ai*.

***

## 🏗️ EVOLUSI ARSITEKTUR (WEEK 2) - `[ VISUALISASI_CYBER_STACK_V2.TXT ]`

Pada arsitektur diperbarui ini, `WORDPRESS` bertindak sebagai jembatan sentral yang
menghubungkan *frontend* dengan tiga komponen *backend* terisolasi. `REDIS` meng-cache query
 database, sedangkan file media dialihkan (*offloaded*) langsung menuju `MINIO` melalui
interkoneksi private S3 API.


    ========================================================================
                          [ PUBLIC_ACCESS_GATEWAY ]
                               │
               ┌───────────────┴───────────────┐
               │ PORT: 80 / 8080               │ PORT: 9001 (Web Console)
               ▼                               ▼
    ████████████████████████████████████████████████████████████████████████
    █                            [ DOCKER_HOST ]                           █
    █======================================================================█
    █                           [ NETWORKS INTERSECT ]                     █
    █                                                                      █
    █     [ FRONTEND-NET ] (PUBLIC)            [ BACKEND-NET ] (PRIVATE)   █
    █     ┌────────────────────────┐          ┌────────────────────────┐   █
    █     │                        │          │                        │   █
    █     │  ► [ WORDPRESS APP ]   │◄────────►│  ► [ WORDPRESS APP ]   │   █
    █     │    (Web Service)       │          │    (Core Connection)   │   █
    █     │                        │          │                        │   █
    █     │  ► [ MINIO CONSOLE ]   │          │  ► [ REDIS CACHE ]     │   █
    █     │    (Management UI)     │          │    (In-Memory Cache)   │   █
    █     │                        │          │                        │   █
    █     └───────────┬────────────┘          │  ► [ DB MARIADB ]      │   █
    █                 │                       │    (Relational State)  │   █
    █                 ▼                       └───────────┬────────────┘   █
    █         [ MINIO STORAGE ]                           │                █
    █         (Object S3 API)                             ▼                █
    █                 │                            [ DATA VOLUMES ]        █
    █                 ▼                           (Persistent State)       █
    █         [( minio_data )]                            │                █
    █                                                     ▼                █
    █                                          [( db_data / wp_data )]     █
    ████████████████████████████████████████████████████████████████████████



✅ TARGET CAPAIAN MINGGU 2 - [ CHECKLIST ]
[x] [ 210 ] CACHING_LAYER_REDIS: Menyusun Caching Layer menggunakan container Redis
                                 alpine yang terintegrasi penuh untuk mempercepat
                                 query database internal.

[x] [ 220 ] OBJECT_STORAGE_MINIO: Membangun Cloud Storage Layer mandiri berbasis
                                  MinIO sebagai simulator S3 lokal.

[x] [ 221 ] WP_MEDIA_OFFLOAD: Mengonfigurasi modul WordPress agar setiap upload
                              aset gambar/media (wp-content/uploads) dialihkan secara
                              otomatis ke bucket Object Storage.

[x] [ 230 ] BISA_AI_COMPETENCY: Menyelesaikan seluruh modul instruksional, kuis,
                                dan verifikasi kepesertaan kelas Cloud Computing
                                di platform bisa.ai.
***

## 🔐 MINGGU 3: HARDENING, DOKUMENTASI, & PORTOFOLIO

### `[ PHASE 03 / ACT 03: SECURE & DELIVER ]`

Berdasarkan panduan final pada **image_083247.png**, fase ketiga ini berfokus pada
**Hardening** (penguatan keamanan) sistem. Fokus utama kelompok adalah melakukan
de-coupling data sensitif menggunakan variabel lingkungan, mencegah kebocoran data
(*credential leaks*) pada repositori publik, serta melakukan integrasi portofolio eksternal. 

Sesuai dengan penyesuaian instruksi terbaru, pengerjaan difokuskan penuh pada optimalisasi
repositori dan validasi platform tanpa beban dokumen fisik tambahan.

***

## 🛠️ SKEMA KEAMANAN ENV (WEEK 3) - `[ INJECT_PROT_SYSTEM.TXT ]`

Protokol ini memutus seluruh *hardcoded credentials* di dalam konfigurasi utama. File `.env`
 disimpan secara lokal (terproteksi oleh `.gitignore`), sementara `docker-compose.yml`
hanya memanggil variabel dinamis.

```text
  ┌──────────────────────────────┐
  │           [ .env ]           │  ◄─── [ BERISI: PASSWORD, USER, API KEYS ]
  │    (Lokal / Tersembunyi)     │       (Aman dari sniffing GitHub)
  └──────────────┬───────────────┘
                 │
                 │ (Injeksi Variabel Otomatis)
                 ▼
  ██████████████████████████████████
  █    [ DOCKER-COMPOSE.YML ]      █
  █================================█
  █  environment:                  █
  █   - WORDPRESS_DB_PASSWORD      █ ◄─── [ AMAN / BEBAS HARDCODE ]
  █   - MYSQL_ROOT_PASSWORD        █       (Siap dipublish ke publik)
  ██████████████████████████████████

✅ TARGET CAPAIAN MINGGU 3 - [ CHECKLIST ]
[x] [ 310 ] ENVIRONMENT_HARDENING: Menerapkan Best Practices Keamanan dengan memisahkan
                                   seluruh credentials (password database & akses root)
                                   ke dalam file .env.

[x] [ 311 ] ZERO_HARDCODE_VALIDATION: Membersihkan file docker-compose.yml dari teks
                                      sandi mentah agar aman saat di-push ke GitHub.

[x] [ 320 ] BISA_AI_PORTFOLIO: Membangun dan mempublikasikan portofolio proyek Cloud
                               Computing ini pada platform bisa.ai.

[x] [ 330 ] FINAL_REPO_DELIVERY: Finalisasi seluruh berkas repositori sebagai output
                                 monitoring utama.
