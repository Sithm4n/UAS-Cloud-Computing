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
pppppppppppppp

