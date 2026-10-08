1. Pelanggaran pada Text Overflow
Row melanggar aturan "constraints go down" karena meneruskan batasan lebar tanpa batas (unbounded width) ke anaknya. Akibatnya, widget Text melanggar aturan "sizes go up" dengan mengambil ukuran yang melebihi sisa ruang horizontal layar.

2. Mengapa Ukuran Lebar Kaku (Hardcoded Width) Itu Salah
Menambah width: 150 membuat tata letak kaku yang gagal beradaptasi saat dibuka di berbagai ukuran layar, skala font sistem yang berbeda, maupun panjang teks yang bervariasi. Cara ini hanya menyembunyikan garis strip overflow secara kasar tanpa benar-benar menyelesaikan masalah fleksibilitas layout.

3. Kegagalan Uji Coba dan Dampak pada API
Pengujian performa 500 items akan gagal karena shrinkWrap: true memaksa aplikasi merender seluruh item sekaligus di awal dan mematikan fungsi lazy loading. Saat data diambil dari API, hal ini akan memicu lag parah, lonjakan penggunaan memori, dan penurunan frame rate saat memuat data dalam jumlah besar.

4. Alasan Menggunakan LayoutBuilder dibanding MediaQuery
LayoutBuilder mengukur batasan ruang dari parent widget secara spesifik, sehingga sangat pas untuk membuat komponen responsif seperti tata letak multi-pane tablet di dalam split-screen atau sidebar. Sebaliknya, MediaQuery.sizeOf(context) hanya membaca ukuran total layar perangkat, yang bisa merusak responsivitas di tingkat komponen.

5. Mengapa Masalah Data Kosong Ada di Lab Layout
Tampilan saat data kosong (empty state) adalah bagian tak terpisahkan dari siklus tata letak UI/UX untuk memastikan struktur aplikasi tidak hancur saat data belum dimuat. Mengujinya di lab layout melatih kita menangani kondisi edge case, menempatkan widget fallback dengan presisi, dan menjaga struktur key tetap konsisten untuk pengujian otomatis.