
# Laporan UTS Praktikum

1. Menganalisis citra
Citra 'nama.jpg' memiliki distribusi warna yang cukup merata di seluruh saluran warna, ditunjukkan oleh histogram yang memiliki distribusi yang relatif merata.

- Histogram merah menunjukkan bahwa intensitas piksel merah paling banyak terkonsentrasi di sekitar nilai 100-150.
- Histogram hijau menunjukkan intensitas piksel hijau yang cukup merata dengan sedikit puncak di sekitar nilai 100.
- Histogram biru menunjukkan intensitas piksel biru yang juga merata dengan sedikit puncak di sekitar nilai 100.
- Histogram warna gabungan menunjukkan kombinasi intensitas piksel dari semua saluran warna, dengan distribusi yang merata namun dengan beberapa puncak yang menunjukkan kemungkinan warna dominan dalam gambar.
Adapun beberapa proses analisis citra yang dilakukan

a. Pemisahan Saluran Warna, memisahkan citra asli menjadi saluran warna merah, hijau, dan biru dengan menggunakan slicing array numpy. Ini memungkinkan kita untuk melihat kontribusi masing-masing saluran warna terhadap citra secara terpisah.

b. Visualisasi Histogram, membuat histogram untuk setiap saluran warna (merah, hijau, biru) serta histogram gabungan dari seluruh citra. Dengan histogram, kita dapat memahami bagaimana intensitas piksel didistribusikan di seluruh saluran warna, membantu kita dalam menganalisis gambar dengan lebih baik.

c. Konversi Warna, karena OpenCV membaca gambar dalam format BGR, sedangkan matplotlib menampilkan dalam format RGB, kita perlu melakukan konversi warna menggunakan cv2.cvtColor(). Hal ini penting agar citra ditampilkan dengan benar.

d. Visualisasi, menggunakan subplot untuk menampilkan citra asli dan saluran warna terpisah, serta subplot terpisah untuk setiap histogram. Dengan cara ini, kita dapat membandingkan distribusi intensitas piksel antara saluran warna dan melihat hubungan antara mereka dengan lebih jelas.

Dengan demikian, proses analisis citra tersebut terfokus pada pemahaman tentang bagaimana distribusi intensitas piksel berbeda di setiap saluran warna, serta bagaimana distribusi keseluruhan warna dalam citra. Ini memberikan pemahaman yang lebih mendalam tentang komposisi warna dan informasi visual dalam citra.

2. Menganalisis Histogram
A. Histogram Merah, Hijau, dan Biru dihasilkan dengan menghitung histogram untuk setiap saluran warna merah, hijau, dan biru menggunakan metode cv2.calcHist(). Histogram-histogram ini menunjukkan bagaimana intensitas piksel didistribusikan dalam masing-masing saluran warna. Misalnya, puncak pada nilai intensitas tertentu dalam histogram merah menandakan adanya banyak piksel dengan intensitas merah yang serupa dalam gambar.

B.  Histogram Warna Gabungan dibuat dengan menghitung histogram untuk warna gabungan menggunakan ketiga saluran warna (merah, hijau, biru) setelah konversi gambar ke format RGB. Ini memperlihatkan bagaimana intensitas piksel terdistribusi secara keseluruhan dalam gambar, memberikan gambaran tentang variasi warna dan dominansi dalam gambar.

Dengan menganalisis histogram-histogram ini, kita bisa mendapatkan pemahaman yang lebih dalam tentang karakteristik warna dalam gambar 'uts.jpg'. Kita bisa melihat seberapa merata distribusi warna, apakah ada warna yang dominan, dan sejauh mana variasi warna dalam gambar. Informasi ini penting dalam berbagai aplikasi pengolahan citra, seperti segmentasi warna, deteksi objek, atau penyesuaian warna.

3. Kedua fungsi menggunakan konversi ruang warna HSV untuk mempermudah dalam mendeteksi warna tertentu, karena HSV memisahkan informasi warna (Hue), kecerahan (Value), dan saturasi (Saturation).

A. Deteksi Warna Biru
- Nilai ambang batas bawah : [100, 50, 50]
- Nilai ambang batas atas : [140, 255, 255]
B. Deteksi Warna Merah-Biru
> Merah
- Nilai ambang batas bawah: [0, 50, 50]
- Nilai ambang batas atas: [10, 255, 255]
- Nilai ambang batas tambahan bawah : [170, 50, 50]
- Nilai ambang batas tambahan atas : [180, 255, 255]
> Biru
- Nilai ambang batas bawah : [100, 50, 50]
- Nilai ambang batas atas: [130, 255, 255]
C. Deteksi Warna Merah-Hijau-biru

Merah

- Nilai ambang batas bawah: [0, 50, 50]
- Nilai ambang batas atas: [10, 255, 255]
- Nilai ambang batas tambahan bawah : [170, 50, 50]
- Nilai ambang batas tambahan atas : [180, 255, 255]

Hijau

- Nilai ambang batas bawah : [40, 50, 50]
- Nilai ambang batas atas : [80, 255, 255]

Merah
- Nilai ambang batas bawah : [100, 50, 50]
- Nilai ambang batas atas: [130, 255, 255]


Nilai-nilai ambang batas dipilih berdasarkan pertimbangan terhadap sifat warna dalam ruang warna HSV serta tujuan deteksi warna yang dilakukan. Alasan di balik pemilihan nilai-nilai ambang batas ini adalah sebagai berikut:

Hue (H): Rentang nilai Hue dipilih dalam rentang 0-180 (dalam OpenCV) karena merepresentasikan warna dalam lingkup 360 derajat. Pemilihan nilai ambang batas memperhitungkan bahwa warna merah memiliki nilai Hue mendekati 0 (atau mendekati 180 karena warna melintasi nilai 0 dalam lingkup warna), warna hijau berada di sekitar 60-120, dan warna biru berada di sekitar 100-150. Nilai-nilai ambang batas ini dipilih agar mencakup rentang Hue yang mewakili warna yang diinginkan.

Saturation (S) dan Value (V): Nilai-nilai ambang batas untuk S dan V dipilih untuk menentukan seberapa jenuh dan seberapa cerah warna yang ingin dideteksi. Rentang yang luas dipilih untuk memungkinkan deteksi warna yang cukup fleksibel terhadap variasi dalam gambar. Namun, pemilihan nilai ambang batas ini dapat bervariasi tergantung pada kondisi cahaya, karakteristik gambar, dan preferensi pengguna.

4. Penjelasan tahapan cara menyelesaikan projek
A. Tahapan Cara Deteksi warna biru, merah dan hijau pada gambar

Tahap 1: Membaca Gambar dan Membuat Plot

Membaca Gambar, gambar yang disimpan dengan nama 'nama.jpg' dibaca menggunakan fungsi imread dari library OpenCV dan disimpan dalam variabel color_image.
Membuat Plot, plot untuk gambar asli, warna merah, hijau, dan biru dibuat menggunakan fungsi subplots dan imshow dari matplotlib. Plot ini menampilkan gambar asli dan warna-warna yang terdiri dari gambar.

Tahap 2: Membuat Histogram

Membuat Histogram, histogram untuk warna merah, hijau, dan biru dibuat menggunakan fungsi calcHist dari OpenCV. Histogram ini menunjukkan distribusi intensitas warna dalam gambar.

Tahap 3: Membuat Fungsi untuk Meningkatkan Brightness dan Mendeteksi Warna

Untuk meningkatkan kecerahan gambar, kita membuat fungsi increase_brightness yang akan meningkatkan nilai kecerahan gambar. Fungsi ini akan menggunakan konversi warna dari BGR ke HSV, lalu meningkatkan nilai kecerahan, dan mengembalikan gambar dalam format BGR.

Selanjutnya, kita membuat fungsi detect_and_highlight_blue, detect_and_highlight_red_blue, dan detect_and_highlight_red_green_blue untuk mendeteksi warna biru, merah-biru, dan merah-hijau-biru secara terpisah. Fungsi-fungsi ini akan menggunakan konversi warna dari BGR ke HSV, lalu menerapkan mask untuk mendeteksi warna dan mengembalikan gambar yang sudah ditekan warna.

Tahap 4: Menerapkan Fungsi untuk Meningkatkan Brightness dan Mendeteksi Warna

Meningkatkan Brightness, fungsi increase_brightness diterapkan pada gambar yang dibaca awal untuk meningkatkan brightness.
Mendeteksi Warna, fungsi detect_and_highlight_blue, detect_and_highlight_red_blue, dan detect_and_highlight_red_green_blue diterapkan pada gambar yang telah ditingkatkan brightness untuk mendeteksi warna.

Tahap 5: Menampilkan Hasil

Menampilkan Hasil, hasil dari masing-masing fungsi diterapkan pada gambar ditampilkan menggunakan fungsi imshow dari matplotlib. Hasil ini menampilkan gambar yang telah ditingkatkan brightness dan ditekan warna.

B. Tahapan Cara Membuat dan Menampilkan Plot Histogram

Tahap 1: Membaca Gambar dan Konversi Warna

Membaca Gambar, gambar yang disimpan dengan nama 'nama.jpg' dibaca menggunakan fungsi imread dari OpenCV dan disimpan dalam variabel color_image.
Konversi Warna, Konversi warna dari BGR ke RGB dilakukan menggunakan fungsi cvtColor dari OpenCV. Fungsi ini digunakan untuk memastikan bahwa warna dalam gambar sesuai dengan format yang digunakan oleh matplotlib.

Tahap 2: Membuat Histogram

Membuat Histogram Biru, histogram untuk warna biru dibuat menggunakan fungsi calcHist dari OpenCV. Histogram ini menunjukkan distribusi intensitas warna biru dalam gambar.
Membuat Histogram Hijau, histogram untuk warna hijau dibuat menggunakan fungsi calcHist dari OpenCV. Histogram ini menunjukkan distribusi intensitas warna hijau dalam gambar.
Membuat Histogram Merah, histogram untuk warna merah dibuat menggunakan fungsi calcHist dari OpenCV. Histogram ini menunjukkan distribusi intensitas warna merah dalam gambar.
Membuat Histogram Warna, histogram untuk warna-warna dalam gambar dibuat menggunakan fungsi calcHist dari OpenCV. Histogram ini menunjukkan distribusi intensitas warna-warna dalam gambar.

Tahap 3: Membuat Plot Histogram

Membuat Plot Histogram Biru, plot histogram biru dibuat menggunakan fungsi plot dari matplotlib. Plot ini menampilkan histogram biru dengan warna biru.
Membuat Plot Histogram Hijau, plot histogram hijau dibuat menggunakan fungsi plot dari matplotlib. Plot ini menampilkan histogram hijau dengan warna hijau.
Membuat Plot Histogram Merah, plot histogram merah dibuat menggunakan fungsi plot dari matplotlib. Plot ini menampilkan histogram merah dengan warna merah.
Membuat Plot Histogram Warna, plot histogram warna dibuat menggunakan fungsi plot dari matplotlib. Plot ini menampilkan histogram warna dengan warna abu-abu.

Tahap 4: Menampilkan Plot Histogram

Menampilkan Plot Histogram, plot histogram untuk warna biru, hijau, merah, dan warna dibuat dan ditampilkan menggunakan fungsi figure dan subplot dari matplotlib. Plot ini menampilkan histogram untuk masing-masing warna dan warna dalam gambar.
C. Tahapan Cara Mencari Nilai Ambang atas yang Didapat

Tahap 1: Membuat Fungsi untuk Meningkatkan Brightness dan Mendeteksi Warna

Meningkatkan Brightness, fungsi increase_brightness dibuat untuk meningkatkan brightness dari gambar. Fungsi ini menggunakan konversi warna dari BGR ke HSV, lalu meningkatkan nilai brightness dan mengembalikan ke BGR.
Mendeteksi Warna, fungsi detect_and_highlight_blue, detect_and_highlight_red_blue, dan detect_and_highlight_red_green_blue dibuat untuk mendeteksi warna biru, merah-biru, dan merah-hijau-biru secara terpisah. Fungsi-fungsi ini menggunakan konversi warna dari BGR ke HSV, lalu menggunakan mask untuk mendeteksi warna dan mengembalikan gambar yang telah ditekan warna.

Tahap 2: Membaca Gambar dan Meningkatkan Brightness

Membaca Gambar, gambar yang disimpan dengan nama 'nama.jpg' dibaca menggunakan fungsi imread dari OpenCV dan disimpan dalam variabel image.
Meningkatkan Brightness, fungsi increase_brightness diterapkan pada gambar yang dibaca untuk meningkatkan brightness.

Tahap 3: Mendeteksi Warna

Mendeteksi Warna Biru, fungsi detect_and_highlight_blue diterapkan pada gambar yang telah ditingkatkan brightness untuk mendeteksi warna biru.
Mendeteksi Warna Merah-Biru, fungsi detect_and_highlight_red_blue diterapkan pada gambar yang telah ditingkatkan brightness untuk mendeteksi warna merah-biru.
Mendeteksi Warna Merah-Hijau-Biru, fungsi detect_and_highlight_red_green_blue diterapkan pada gambar yang telah ditingkatkan brightness untuk mendeteksi warna merah-hijau-biru.

Tahap 4: Menampilkan Hasil

Menampilkan Hasil, hasil dari masing-masing fungsi diterapkan pada gambar ditampilkan menggunakan fungsi imshow dari matplotlib. Hasil ini menampilkan gambar yang telah ditingkatkan brightness dan ditekan warna.

5. Teori yang mendukung mengenai projek
Teori yang Mendukung Proyek

Color Space Conversion: Konversi warna dari RGB ke HSV (Hue, Saturation, Value) digunakan untuk mendeteksi warna dengan lebih akurat. Ini karena nilai HSV memungkinkan pemisahan warna berdasarkan karakteristik yang lebih intuitif: hue untuk warna, saturation untuk intensitas warna, dan value untuk kecerahan. Penerapan HSV mempermudah deteksi warna karena hue dapat digunakan untuk membedakan warna yang berbeda dengan lebih jelas.

Histogram: Penggunaan histogram untuk menganalisis distribusi nilai warna dalam gambar didasarkan pada prinsip bahwa histogram adalah representasi visual dari distribusi nilai dalam suatu distribusi statistik. Dalam konteks warna, histogram membantu memahami bagaimana intensitas warna terdistribusi dalam gambar, sehingga memudahkan analisis dan deteksi warna.

Image Processing: Teknik pengolahan gambar seperti peningkatan kecerahan, deteksi warna, dan penggabungan masker digunakan berdasarkan teori bahwa setiap tugas pengolahan gambar dapat diselesaikan dengan algoritma yang spesifik. Misalnya, peningkatan kecerahan dilakukan dengan menyesuaikan nilai kecerahan dalam model warna HSV, sementara deteksi warna memanfaatkan masker warna untuk mengidentifikasi area yang sesuai.

Color Detection: Deteksi warna menggunakan masker warna untuk memisahkan area dalam gambar berdasarkan warnanya. Prinsipnya adalah bahwa warna dalam gambar dapat didefinisikan oleh nilai warna yang spesifik, sehingga dengan menggunakan masker warna, kita dapat dengan mudah mengisolasi warna yang diinginkan untuk analisis lebih lanjut.

Image Segmentation: Penggabungan masker warna digunakan untuk memisahkan gambar ke dalam bagian-bagian yang berbeda berdasarkan warna. Konsepnya adalah bahwa gambar dapat dipecah menjadi segmen berdasarkan karakteristik warna, yang memudahkan analisis dan manipulasi lebih lanjut terhadap bagian-bagian tersebut.

Secara keseluruhan, proyek ini menggabungkan berbagai teori dan teknik pengolahan gambar untuk mendeteksi warna dan mengolah gambar dengan lebih efektif. Penerapan prinsip-prinsip tersebut memungkinkan analisis warna yang akurat dan efisien dalam gambar.