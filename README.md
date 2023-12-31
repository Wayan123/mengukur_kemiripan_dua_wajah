# Mengukur kemiripan dua wajah 

# Note: Kode dijalankan pada GPU agar bisa mendapatkan hasil yang lebih cepat.

Cara penggunaan:

1. Jika hanya membandingkan hanya 1 per 1 foto saja, maka:

- Gunakan kode mengukur_kemiripan_2_wajah.py dan jika menggunakan jupyter atau google colab gunakan kode mengukur_kemiripan_2_wajah.ipynb. Untuk file mengukur_kemiripan_2_wajah_augmentasi.py dan mengukur_kemiripan_2_wajah_augmentasi.ipynb ditambahkan metode augmentasi.
- Taruh foto1 dan foto2 pada directory yang sama dengan program, atau bisa juga menggunakan foto yang ada di dalam directory wajah_1 dan wajah_2, dengan cara ubah baris sebagai berikut
- a. foto_1 = "wajah_1/ariel.jpg"
- b. foto_2 = "awajah_2/riel_kw1.jpg"

2. Jika ingin menggunakan banyak foto pada masing-masing wajah:
- Gunakan kode mengukur_kemiripan_2_wajah_GPU.py dan jika menggunakan jupyter atau google colab gunakan kode mengukur_kemiripan_2_wajah_GPU.ipynb
- Buat  2 buah directory berupa wajah_1 dan wajah_2.
- Kumpulkan gambar lebih dari 1, lalu taruh pada masing-masing directory.

Kode ini hanya sebagai contoh saja dan mungkin masih bisa dikembangkan agar mendapatkan hasil yang jauh lebih baik. Metode yang digunakan adalah mengukur kemiripan menggunakan Euclidean Distance atau normal L2.

### Metode yang digunakan pada kode di atas untuk mengukur kemiripan dua wajah seseorang pada kode adalah sebagai berikut:

1. Deteksi Wajah: Pertama, gambar wajah dari kedua direktori dimuat menggunakan `dlib.load_rgb_image` dan deteksi wajah dilakukan menggunakan model-detektor wajah HOG dari `dlib`. Deteksi wajah ini membantu dalam menemukan lokasi dan ukuran wajah pada gambar.

2. Ekstraksi Fitur: Setelah deteksi wajah dilakukan, model pengenal wajah dari `dlib` (yang dilatih menggunakan model ResNet) digunakan untuk mengekstraksi fitur wajah dari setiap wajah yang terdeteksi. Proses ini mengubah wajah menjadi vektor fitur numerik yang merepresentasikan ciri-ciri unik dari wajah tersebut.

3. Pengukuran Kemiripan: Setelah fitur wajah dari kedua direktori dihasilkan, kemiripan antara kedua wajah diukur dengan metode jarak terdekat. Jarak Euclidean atau norma L2 digunakan untuk menghitung jarak antara setiap pasangan fitur wajah. Jarak terdekat kemudian diambil sebagai nilai kemiripan antara kedua wajah, dengan semakin kecil nilai jaraknya, semakin mirip kedua wajahnya. Untuk bacaan singkat mengenai Euclidean Distance dapat dibaca di link berikut: https://machinelearningmastery.com/distance-measures-for-machine-learning/

4. Skala Kemiripan: Nilai kemiripan yang dihasilkan dari langkah sebelumnya berada dalam rentang 0 hingga 1. Nilai 0 menunjukkan kemiripan maksimum (wajah yang sama), sementara nilai 1 menunjukkan ketidakmiripan total (wajah yang sangat berbeda). Untuk memberikan representasi yang lebih intuitif, nilai kemiripan dikalikan dengan 100 sehingga dapat dinyatakan dalam persentase kemiripan.

Dengan menggunakan langkah-langkah di atas, kita dapat mengukur kemiripan antara dua wajah orang dengan menghitung jarak antara vektor fitur wajah yang diekstraksi. Semakin kecil jaraknya, semakin mirip kedua wajahnya.
