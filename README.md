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
Repositori ini memuat progress tugas kelompok Cloud Computing untuk Minggu 1. Fokus utama pada fase ini adalah meninggalkan metode legacy all-in-one server dan mulai mengadopsi arsitektur cloud modern dengan pemisahan layer menggunakan Docker, serta menerapkan network isolation protocols untuk keamanan data antar-container.

🏗️ ARSITEKTUR SISTEM (WEEK 1) - [ VISUALISASI_CYBER_STACK.TXT ]
Arsitektur ini didesain agar App Layer dan Database Layer tidak dapat "saling melihat" secara langsung dari jaringan publik, memastikan data integrity dan attack vector reduction.



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
