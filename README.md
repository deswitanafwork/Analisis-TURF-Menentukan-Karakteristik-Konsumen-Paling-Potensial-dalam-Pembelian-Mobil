# Analisis-TURF-Menentukan-Karakteristik-Konsumen-Paling-Potensial-dalam-Pembelian-Mobil
End-to-end data Analisis TURF Menentukan Karakteristik Konsumen Paling Potensial dalam Pembelian Mobil


Industri otomotif saat ini menghadapi persaingan yang sangat ketat, sehingga perusahaan harus memahami siapa calon pembeli atau pihak pengaju kredit yang memiliki potensi pasar paling besar. Strategi pemasaran umum seringkali tidak berhasil karena tidak semua konsumen memiliki kebutuhan, preferensi, dan daya beli yang seragam. Oleh karena itu, perusahaan harus melakukan segmentasi pasar berdasarkan rekaman data pelanggan sebelumnya untuk mengidentifikasi karakteristik konsumen secara terperinci. Dengan memetakan karakteristik pembeli tersebut, perusahaan dapat menyesuaikan target promosinya sehingga angka penjualan dan pengajuan kredit mobil bisa meningkat secara efektif.

Maka saya melakukan percobaan analisis menggunakan metode TURF untuk mencari tahu kombinasi karakteristik konsumen mana yang paling potensial dalam konteks pembelian mobil. Mengapa saya menggunakan metode TURF dan bukan metode segmentasi pelanggan biasa, dikarenakan metode TURF dapat mengevaluasi jangkauan pasar dengan tingkat tumpang tindih pesan yang minimal. Selain itu, metode TURF mampu memberikan rekomendasi strategis tentang karakteristik audiens mana yang paling optimal untuk menjangkau kelompok konsumen baru secara menyeluruh. Melalui metode ini, keputusan yang dirumuskan terbukti berbasis data nyata, bukan sekadar asumsi, karena metrik seperti *reach* (jangkauan), *frequency* (frekuensi), dan *overlap* (tumpang tindih) dihitung secara eksplisit guna menciptakan dasar strategi pemasaran yang terukur dan tepat sasaran.

Asumsi utama dalam percobaan ini yaitu karakteristik konsumen terdahulu dapat dikombinasikan sedemikian rupa guna menghasilkan luasan jangkauan pasar yang maksimal, sehingga distribusi pemasaran bisa diarahkan dengan jauh lebih efektif. Diasumsikan pula bahwa perhitungan menggunakan metrik eksplisit dari TURF (*reach*, *frequency*, *overlap*) memiliki tingkat keakuratan yang lebih tinggi dalam mempresentasikan prospek potensi pembeli dibandingkan dengan model segmentasi tradisional.

**Import Library & Tech Stack**
Ekstraksi, transformasi, dan analisis pada projek ini dibangun menggunakan Tech Stack berikut:

* **Python (Pandas & NumPy)**: Digunakan untuk membaca dataset dari format CSV, menangani tipe data bernilai kosong, dan melakukan manipulasi *dataframe* hingga siap diproses.


* **Itertools**: Digunakan secara khusus pada fungsi TURF untuk menyusun pola kombinasi matematis dari berbagai fitur pelanggan dalam pencarian persentase jangkauan terbaik.


* **Matplotlib & Seaborn**: Digunakan untuk tahap visualisasi data eksploratif (EDA) guna memetakan profil data tabel dan menyajikan hasil analisis kombinasi ke dalam grafik *bar chart* horisontal.


* **Pingouin, SciPy, Scikit-Learn**: Digunakan sebagai pustaka komputasi pendukung dalam kalkulasi statistik tingkat lanjut, perhitungan jarak Mahalanobis, serta kovarians matrik.



**Pengumpulan Data**
Data dikumpulkan melalui dataset profil kepemilikan kendaraan ("Car Ownership.csv") yang mencakup 500 baris rekaman. Data mentah ini memuat informasi profesi, pendapatan bulanan, skor kredit konsumen, riwayat lamanya bekerja, status finansial, riwayat keuangan masa lalu, kepemilikan mobil, dan jumlah anak yang masih berupa format belum seragam.

**Preprocessing**
Pendekatan preprocessing dilakukan secara sistematis untuk memastikan model TURF menerima input angka biner dan kelompok data yang bersih:

* **Data Cleaning & Imputation**: Menghapus seluruh baris data yang kosong secara absolut (NaN pada semua sumbu), kemudian mengatasi *missing value* dengan mengubah input *string* kosong, elemen 'na', dan elemen NaN pada variabel jumlah anak dan durasi masa kerja menjadi nominal 0.


* **Text Normalization & Type Casting**: Mengeliminasi teks yang mengganggu seperti kata "years", "year", atau "y" pada rentang waktu bekerja dengan mengeksekusi ekspresi *regex*. Tahap ini diteruskan dengan mengonversi tipe data kolom pendapatan, skor kredit, durasi kerja, dan tanggungan anak menjadi tipe format bilangan *integer* (angka utuh) agar terukur secara kuantitatif.


* **Feature Categorization & One-Hot Encoding**: Memilah jenis profesi awal menjadi 15 blok industri besar (seperti kategori IT, Kesehatan, Bisnis, Desain, Pendidikan), merangkum jejak riwayat keuangan ke dalam 3 tingkatan (Baik, Cukup, Buruk), dan menggolongkan rentang pendapatan bulanan ke grup Rendah, Sedang, atau Tinggi. Data karakteristik yang sudah dikategorikan ini kemudian diekspansi menjadi variabel boolean (0 dan 1) lewat penerapan fungsi *One-Hot Encoding* untuk mendeteksi kecocokan kondisi.



**Key Insights (Hasil Temuan)**
Berdasarkan penerapan simulasi metode TURF pada matriks kombinasi karakteristik konsumen, diperoleh temuan strategis sebagai berikut:

* **Pencarian Skenario Penjangkauan Target (*Reach*)**: Sistem menguji kombinasi maksimal sebanyak 3 karakteristik pelanggan (*Maksimal Kombinasi Fitur*) dengan harapan skenario tersebut mampu menyentuh target penetrasi persentase pasar minimal di angka 90% audiens yang benar-benar melakukan pembelian mobil.


* **Rekomendasi Karakteristik Terbaik**: Logika program berhasil mengakumulasi dan memilah 10 kombinasi susunan profil konsumen yang memegang nilai persentase jangkauan kumulatif (reach) paling besar, yang siap diadopsi sebagai sasaran promosi.



**Visualisasi Data Eksploratif (EDA)**
Tahap ini memuat penggambaran grafik batang bar chart secara horisontal dengan warna hijau kustom menggunakan pustaka Matplotlib untuk memaparkan urutan "Top 10 Kombinasi Karakteristik Konsumen Berdasarkan Reach (TURF)". Grafik ini juga diintegrasikan dengan proyeksi garis batas (*axvline*) putus-putus berwarna merah yang berlabuh pada poros X untuk memberikan penanda yang jelas apakah persentase tersebut sudah melewati target KPI 90% atau belum.

Tertarik dengan proses dan penulisan kode analisis di balik layar?
Silakan telusuri langsung melalui Jupyter Notebook di repositori ini. Jika Anda memiliki feedback, masukan, atau ingin berdiskusi mengenai peluang kolaborasi dan karir di bidang data, mari terhubung melalui LinkedIn Saya atau jangkau saya melalui email di deswitanaf.work@gmail.com.
