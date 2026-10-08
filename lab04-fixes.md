1. StoreHeader (Rating Overflow): Overflow horizontal pada rating teks di layar 320 dp. Aturan dilanggar: Row memberi Text lebar tanpa batas. Fix: Bungkus Text dengan Flexible + maxLines: 1 + ellipsis.

2. StoreHeader (Title Overflow): Overflow horizontal saat nama toko panjang. Aturan dilanggar: Column anak Row tanpa batasan lebar. Fix: Bungkus Column dengan Expanded + maxLines: 1 + ellipsis.

3. MenuTile (200-char Name): Teks nama menu 200 karakter terdorong keluar layar. Aturan dilanggar: Column di Row tidak membatasi baris teks. Fix: Bungkus Column dengan Expanded + maxLines: 2 + ellipsis.

4. MenuTile (Price & Badge): Teks harga terpotong saat font sistem diperbesar. Aturan dilanggar: Mengasumsikan tinggi baris teks bersifat tetap. Fix: Bungkus area harga dengan FittedBox.

5. MenuCard (Grid Cell Height): Overflow vertikal di bagian bawah kartu pada GridView. Aturan dilanggar: Tinggi kartu kaku (fixed height). Fix: Ubah childAspectRatio ke 0.65 di SliverGrid + Expanded pada judul.

6. PromoCard (Long Description): Overflow vertikal pada deskripsi promo yang panjang. Aturan dilanggar: Area teks kaku memicu pembengkakan konten. Fix: Bungkus teks dengan Expanded + maxLines: 3 + ellipsis.

7. MenuScreen (Landscape / Keyboard): Overflow vertikal saat keyboard terbuka atau mode landscape. Aturan dilanggar: Menggunakan Column non-scrollable pada ruang terbatas. Fix: Ganti ke CustomScrollView + SliverToBoxAdapter.

8. MenuScreen (500-Items Performance): Aplikasi lag berat saat memuat 500 item. Aturan dilanggar: Membuat semua widget sekaligus di awal (up-front rendering). Fix: Gunakan lazy loading dengan SliverList dan SliverGrid.

9. MenuScreen (Zero Items): Pengujian otomatis gagal menemukan key empty-state. Aturan dilanggar: Key berada di luar posisi hierarki yang benar. Fix: Pasang Key('empty-state') langsung di Column dalam SliverFillRemaining.

10. CartBar (Gesture Bar): Tombol order tertutup gesture bar navigasi bawah. Aturan dilanggar: Kontainer tidak memperhitungkan inset sistem. Fix: Bungkus CartBar dalam SafeArea.

11. CartBar (Dark Mode): Kontras warna tombol buruk saat mode gelap. Aturan dilanggar: Menggunakan warna manual (hardcoded). Fix: Gunakan warna dinamis Theme.of(context).colorScheme.

12. FilterChipBar (Small Screen): Deretan chip filter keluar dari batas kanan layar. Aturan dilanggar: Menaruh daftar chip di dalam Row biasa. Fix: Ganti pembungkus ke SingleChildScrollView horizontal.
