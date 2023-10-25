# Computer-Vision-Project
# **05_01_Earth_Muhammad Asri Alfajri.ipynb**
**Peningkatan Kualitas Gambar dengan CLAHE**
Proyek ini mengeksplorasi berbagai teknik pemrosesan gambar untuk meningkatkan kualitas gambar dengan pencahayaan rendah, dengan membandingkan max pooling, min pooling, average pooling, dan CLAHE (Contrast Limited Adaptive Histogram Equalization).

**Metode**
Metode berikut ini diimplementasikan:
1. OpenCV digunakan untuk mengkonversi antar ruang warna (RGB, grayscale, binary)
2. Fungsi block_reduce() dari Scikit-image menerapkan max pooling, min pooling, dan average pooling
3. Lapisan MaxPool2d dari PyTorch menerapkan max pooling
4. Fungsi CLAHE kustom mengimplementasikan adaptive histogram equalization
   
**Hasil**
Temuan utama:
1. Max pooling memcerahkan gambar tetapi kehilangan detail
2. Min pooling berfokus pada fitur gelap seperti tepian
3. Average pooling menghasilkan representasi yang lebih halus
4. CLAHE meningkatkan kontras lokal sambil mempertahankan detail
5. CLAHE menghasilkan hasil visual terbaik untuk meningkatkan kualitas gambar uji. CLAHE sangat baik untuk tugas peningkatan kualitas gambar yang memprioritaskan kualitas dan pelestarian detail.

# **05_02_Earth_Muhammad Asri Alfajri**
**Transfer Learning untuk Klasifikasi Angka Tulisan Tangan MNIST**
Proyek ini menerapkan teknik transfer learning dengan beberapa model CNN pra-latih untuk melakukan klasifikasi 10 kelas angka tulisan tangan pada dataset MNIST.

**Latar Belakang**
MNIST adalah dataset standar untuk klasifikasi gambar yang berisi 60.000 gambar latih dan 10.000 gambar uji berukuran 28x28 piksel dari 10 digit angka tulisan tangan.

Transfer learning memanfaatkan model yang telah dilatih pada dataset besar sebelumnya, dan menyesuaikannya untuk tugas baru. Ini memungkinkan melatih model kompleks tanpa dataset besar.

**Metode**
Metode berikut diterapkan:
3 model CNN pra-latih digunakan:
1. ResNet18: 18 lapisan residual
2. DenseNet121: 121 lapisan densely connected
3. Vision Transformer (ViT): model transformer untuk visi

Lapisan input dan output dimodifikasi untuk menyesuaikan dengan MNIST
1. Input layer diubah untuk menerima input 1 channel bukan 3
2. Output layer diubah menjadi 10 neuron untuk 10 kelas
   
Beberapa lapisan dibekukan (bobotnya tidak diperbarui) saat pelatihan:
1. Hanya DenseBlock1 dibekukan
2. DenseBlock1 dan DenseBlock2 dibekukan

Model dilatih selama 5 epoch dengan batch size 6 dan learning rate 1e-5

Performa model dievaluasi dengan akurasi dan loss pada data latih dan validasi

**Hasil**

Membekukan lapisan menurunkan akurasi akhir karena adaptasi terbatas ke dataset baru. 
Semakin banyak lapisan dibekukan, semakin lambat akurasi awal karena keterbatasan pengetahuan awal. 
Lapisan beku mempercepat waktu pelatihan karena mengurangi parameter yang diperbarui
