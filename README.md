# UJIAN TENGAH SEMESTER PENGOLAHAN CITRA DIGITAL

### NAMA : FAUZAN ARROYYAN  
### NIM  : 202231062    
### KELAS: B  

# TAHAPAN INISIALISASI PYTHON
## 1. IMPORT LIBRARY  
   import cv2    
   import numpy as np  
   from matplotlib import pyplot as plt  
   ### import cv2:  
  Baris ini mengimpor library OpenCV (cv2), yang merupakan library open-source yang kuat dan banyak digunakan untuk visi komputer real-time. OpenCV menyediakan serangkaian fungsi yang        lengkap untuk pemrosesan gambar dan video, deteksi objek, kalibrasi kamera, pengenalan wajah, dan banyak lagi.
   ### import numpy as np:  
  Baris ini mengimpor library NumPy (numpy), yang merupakan library fundamental untuk komputasi ilmiah dalam Python. NumPy menawarkan manipulasi array multidimensi yang efisien, operasi      aljabar linier, dan fungsi matematika. OpenCV sangat bergantung pada array NumPy untuk merepresentasikan dan memproses gambar.
  ## from matplotlib import pyplot as plt:  
  Baris ini mengimpor modul pyplot dari library Matplotlib, yang menyediakan fungsi untuk membuat berbagai visualisasi seperti plot, histogram, dan gambar. Meskipun tidak sepenuhnya          penting untuk pemrosesan citra, Matplotlib dapat membantu memvisualisasikan hasil operasi Anda, seperti menampilkan gambar yang telah diproses atau memplot data statistik.  

  ## 2. MEMBACA GAMBAR  
 img = cv2.imread("fauzan.png")  
 plt.imshow(img)
 
  ## img = cv2.imread("fauzan.png"):
  Baris ini menggunakan fungsi cv2.imread dari library OpenCV untuk memuat file gambar bernama "fauzan.png". Fungsi ini menerima path ke file gambar sebagai argumen dan mengembalikan       array yang mewakili data gambar. Dengan kata lain, baris ini membaca file gambar "fauzan.png" dari komputer Anda dan menyimpannya sebagai array pixel di dalam variable img.

  ## plt.imshow(img):
  Baris ini menggunakan fungsi imshow dari library Matplotlib untuk menampilkan gambar yang tersimpan di variable img. Fungsi imshow menerima array gambar sebagai argumen dan               menampilkannya pada plot. Singkatnya, baris ini menampilkan gambar yang dimuat ke dalam variable img di jendela baru.

  ## 3. MENGUBAH RGB  
  rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)  
  plt.imshow(rgb)  
    
  ## rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB):
  Baris ini menggunakan fungsi cv2.cvtColor dari library OpenCV untuk mengubah format warna gambar yang tersimpan di variable img.
  Fungsi cv2.cvtColor menerima dua argumen:
  img: Array yang mewakili gambar yang ingin diubah format warnanya.
  cv2.COLOR_BGR2RGB: Kode konversi warna yang menentukan konversi dari format BGR ke format RGB.
  Secara default, OpenCV menyimpan gambar dalam format BGR (Blue, Green, Red), sedangkan beberapa library lain seperti Matplotlib menggunakan format RGB. Konversi ini diperlukan agar       gambar ditampilkan dengan warna yang benar. Singkatnya, baris ini mengubah format warna gambar dari BGR ke RGB dan menyimpan hasil konversi tersebut di variable rgb.

  ## plt.imshow(rgb):  
  Baris ini sama seperti sebelumnya, menggunakan fungsi imshow dari Matplotlib untuk menampilkan gambar. Namun, kali ini yang ditampilkan adalah gambar yang sudah dikonversi ke format      RGB dan tersimpan di variable rgb.

  ## 5. MENINGKATKAN KONTRAS
  beta = 30 #bias untuk kecerahan  
citra_cerah = np.zeros((baris, kolom, 3)) #np zeros = mengubah semua elemen array menjadi 0  
   
for x in range(baris) :  
    for y in range(kolom) :  
        gyx = rgb[x,y] + beta  
        citra_cerah[x,y] = gyx  
citra_cerah = citra_cerah.astype(np.uint8)  
   
fig, axs = plt.subplots(2,2, figsize=(15,5))  
axs[0,0].imshow(rgb)  
axs[0,1].hist(img.ravel(),256,[0,256])  
axs[1,0].imshow(citra_cerah)  
axs[1,1].hist(citra_cerah.ravel(),256,[0,256])  
plt.show()  

### A. Mendefinisikan Variabel:
**beta**: Variabel ini mendefinisikan nilai bias yang akan ditambahkan ke setiap nilai piksel RGB. Nilai ini menentukan seberapa terang gambar yang dihasilkan. Semakin tinggi nilai beta, semakin terang gambarnya. Dalam kode, beta diatur ke 30.  
**citra_cerah**: Variabel ini akan menyimpan gambar yang telah diubah kontrasnya.  
**Baris**: Variabel ini menampung tinggi gambar.  
**kolom**: Variabel ini menampung lebar gambar.  
### B. Membuat Array Kosong:  
**Baris citra_cerah** = np.zeros((baris, kolom, 3)) menggunakan fungsi np.zeros dari NumPy untuk membuat array baru bernama citra_cerah dengan dimensi yang sama dengan gambar asli (baris x kolom x 3 saluran warna). Elemen-elemen array ini semua diinisialisasi dengan nilai 0.  
### C. Meningkatkan Kontras:  
Loop for ganda mengiterasi setiap piksel pada gambar asli (rgb).  
Di dalam loop, nilai intensitas RGB (merah, hijau, biru) pada piksel saat ini ditambahkan dengan nilai beta.  
Hasilnya disimpan di array citra_cerah pada posisi yang sesuai.  
### D. Konversi Tipe Data:  
**Baris citra_cerah** = citra_cerah.astype(np.uint8) mengubah tipe data array citra_cerah menjadi np.uint8. Hal ini diperlukan karena nilai intensitas piksel harus berada dalam rentang 0-255.    
### E. Menampilkan Hasil:  
Bagian terakhir menggunakan Matplotlib untuk membuat plot yang terdiri dari 4 sub-plot:  
Subplot 1,1: Menampilkan gambar asli (rgb).  
Subplot 1,2: Menampilkan histogram distribusi nilai piksel pada gambar asli.  
Subplot 2,1: Menampilkan gambar yang telah diubah kontrasnya (citra_cerah).  
Subplot 2,2: Menampilkan histogram distribusi nilai piksel pada gambar yang telah diubah kontrasnya.  

## 6. MENDETEKSI WARNA RGB
plt.subplot(2, 2, 1)  
plt.imshow(citra_cerah)  
plt.title('Original Image')  

plt.subplot(2, 2, 2)  
plt.imshow(citra_cerah[:,:,0], cmap="gray")  
plt.title('Red Channel')  

plt.subplot(2, 2, 3)  
plt.imshow(citra_cerah[:,:,1], cmap="gray")  
plt.title('Green Channel')  
  
plt.subplot(2, 2, 4)  
plt.imshow(citra_cerah[:,:,2], cmap="gray")  
plt.title('Blue Channel')  
  
plt.show()    

### A. Menampilkan Gambar Asli:
**plt.subplot(2, 2, 1)**: Baris ini membuat tata letak subplot dengan 2 baris dan 2 kolom. Angka 1 menunjukkan bahwa kita sedang bekerja dengan subplot pertama dalam tata letak ini.  
**plt.imshow(citra_cerah)**: Baris ini menampilkan gambar yang tersimpan di variabel citra_cerah menggunakan fungsi imshow.  
**plt.title('Gambar Asli')**: Baris ini menambahkan judul "Gambar Asli" ke subplot pertama.   

### B. Menampilkan Saluran Merah:  
**plt.subplot(2, 2, 2)**: Baris ini memilih subplot kedua dalam tata letak 2x2.  
**plt.imshow(citra_cerah[:,:,0], cmap="gray")**: Baris ini menampilkan saluran merah dari gambar. Berikut cara kerjanya:  
**citra_cerah[:,:,0]**: Bagian ini mengekstrak saluran pertama (mewakili merah) dari array 3 dimensi citra_cerah.  
**cmap="gray"**: Karena data saluran merah merepresentasikan nilai intensitas, maka colormap skala abu-abu ("gray") digunakan untuk visualisasi.  
**plt.title('Saluran Merah')**: Baris ini menambahkan judul "Saluran Merah" ke subplot kedua.    

### C. Menampilkan Saluran Hijau (Serupa dengan Saluran Merah):  
**plt.subplot(2, 2, 3)**: Memilih subplot ketiga.  
**plt.imshow(citra_cerah[:,:,1], cmap="gray")**: Mengekstrak saluran hijau (saluran kedua) dan menampilkannya menggunakan colormap skala abu-abu.  
**plt.title('Saluran Hijau')**: Menambahkan judul "Saluran Hijau".    

### D. Menampilkan Saluran Biru (Serupa dengan Saluran Merah):
**plt.subplot(2, 2, 4)**: Memilih subplot keempat.  
**plt.imshow(citra_cerah[:,:,2], cmap="gray")**: Mengekstrak saluran biru (saluran ketiga) dan menampilkannya menggunakan colormap skala abu-abu.  
**plt.title('Saluran Biru')**: Menambahkan judul "Saluran Biru".  

 ### E. Menampilkan Plot:  
**plt.show()**: Baris ini menampilkan semua subplot yang dibuat, termasuk gambar asli dan visualisasi saluran warna individual.  

## 7. HISTOGRAM MERAH  
merah=citra_cerah[:,:,0] #Merah  
fig, axs = plt.subplots(1,2, figsize = (15,5))  
hist = cv2.calcHist([merah],[0],None,[256],[0,256])  
axs[0].imshow(merah, cmap='gray')  
axs[1].plot(hist)  
plt.show()  

### A. Mengekstrak Saluran Merah:  
***merah=citra_cerah[:,:,0] #Merah**: Baris ini mengekstrak saluran merah dari array gambar citra_cerah dan menyimpannya di variable baru bernama merah. Pengindeksan [:,:,0] memilih   semua piksel dari semua baris dan kolom (: :) dan saluran pertama (indeks 0 yang sesuai dengan merah).
 ### B. Membuat Subplot:  
***fig, axs = plt.subplots(1,2, figsize = (15,5))***: Baris ini membuat figure (fig) dan dua subplot (axs) yang diatur dalam satu baris dengan dua kolom. Parameter figsize mengatur ukuran keseluruhan jendela figure.  
### C. Menampilkan Gambar Saluran Merah:    
***axs[0].imshow(merah, cmap='gray')***: Baris ini menampilkan gambar merah (yang hanya berisi data saluran merah) di subplot pertama (axs[0]). Parameter cmap='gray' menentukan bahwa colormap skala abu-abu harus digunakan untuk visualisasi.  
### D. Menghitung Histogram: 
***hist = cv2.calcHist([merah],[0],None,[256],[0,256])***: Baris ini menghitung histogram intensitas piksel merah pada gambar merah menggunakan fungsi cv2.calcHist dari OpenCV. Berikut rincian argumennya:  
[merah]: List berisi array gambar yang akan dianalisis (dalam kasus ini, gambar saluran merah).  
[0]: List yang menentukan saluran mana yang akan digunakan untuk histogram (dalam kasus ini, hanya saluran pertama, yaitu merah).  
None: Argumen ini tidak digunakan dalam konteks ini.  
[256]: Ini menentukan jumlah bin histogram (256 dalam kasus ini).  
[0,256]: Ini mendefinisikan rentang nilai intensitas yang akan dipertimbangkan (dari 0 hingga 255 untuk intensitas piksel).  
### E. Memplot Histogram:  
***axs[1].plot(hist)***: Baris ini memplot histogram yang dihitung di subplot kedua (axs[1]). Fungsi plot membuat plot garis dari data histogram.  
### F.Menampilkan Plot:  
***plt.show()***: Baris ini menampilkan seluruh figure, termasuk kedua subplot dengan gambar saluran merah dan histogram yang sesuai.  

# 8. HISTOGRAM HIJAU  
hijau=citra_cerah[:,:,1] #hijau  
fig, axs = plt.subplots(1,2, figsize = (15,5))  
hist = cv2.calcHist([hijau],[0],None,[256],[0,256])  
axs[0].imshow(hijau, cmap='gray')  
axs[1].plot(hist)  
plt.show()  

### A. Mengekstrak Saluran Merah:  
***merah=citra_cerah[:,:,1] #Hijau**: Baris ini mengekstrak saluran merah dari array gambar citra_cerah dan menyimpannya di variable baru bernama hijau. Pengindeksan [:,:,0] memilih   semua piksel dari semua baris dan kolom (: :) dan saluran pertama (indeks 0 yang sesuai dengan merah).
 ### B. Membuat Subplot:  
***fig, axs = plt.subplots(1,2, figsize = (15,5))***: Baris ini membuat figure (fig) dan dua subplot (axs) yang diatur dalam satu baris dengan dua kolom. Parameter figsize mengatur ukuran keseluruhan jendela figure.  
### C. Menampilkan Gambar Saluran Merah:    
***axs[0].imshow(hijau, cmap='gray')***: Baris ini menampilkan gambar merah (yang hanya berisi data saluran hijau) di subplot pertama (axs[0]). Parameter cmap='gray' menentukan bahwa colormap skala abu-abu harus digunakan untuk visualisasi.  
### D. Menghitung Histogram: 
***hist = cv2.calcHist([hijau],[0],None,[256],[0,256])***: Baris ini menghitung histogram intensitas piksel hijau pada gambar hijau menggunakan fungsi cv2.calcHist dari OpenCV. Berikut rincian argumennya:  
[hijau]: List berisi array gambar yang akan dianalisis (dalam kasus ini, gambar saluran hijau).  
[0]: List yang menentukan saluran mana yang akan digunakan untuk histogram (dalam kasus ini, hanya saluran pertama, yaitu hijau).  
None: Argumen ini tidak digunakan dalam konteks ini.  
[256]: Ini menentukan jumlah bin histogram (256 dalam kasus ini).  
[0,256]: Ini mendefinisikan rentang nilai intensitas yang akan dipertimbangkan (dari 0 hingga 255 untuk intensitas piksel).  
### E. Memplot Histogram:  
***axs[1].plot(hist)***: Baris ini memplot histogram yang dihitung di subplot kedua (axs[1]). Fungsi plot membuat plot garis dari data histogram.  
### F.Menampilkan Plot:  
***plt.show()***: Baris ini menampilkan seluruh figure, termasuk kedua subplot dengan gambar saluran hijau dan histogram yang sesuai.    

# 9. HISTOGRAM BIRU
biru=citra_cerah[:,:,2] #biru  
fig, axs = plt.subplots(1,2, figsize = (15,5))  
hist = cv2.calcHist([biru],[0],None,[256],[0,256])  
axs[0].imshow(biru, cmap='gray')  
axs[1].plot(hist)  
plt.show()  

### A. Mengekstrak Saluran BIRU:  
***merah=citra_cerah[:,:,2] #biru**: Baris ini mengekstrak saluran merah dari array gambar citra_cerah dan menyimpannya di variable baru bernama biru. Pengindeksan [:,:,0] memilih   semua piksel dari semua baris dan kolom (: :) dan saluran pertama (indeks 0 yang sesuai dengan merah).
 ### B. Membuat Subplot:  
***fig, axs = plt.subplots(1,2, figsize = (15,5))***: Baris ini membuat figure (fig) dan dua subplot (axs) yang diatur dalam satu baris dengan dua kolom. Parameter figsize mengatur ukuran keseluruhan jendela figure.  
### C. Menampilkan Gambar Saluran biru:    
***axs[0].imshow(biru, cmap='gray')***: Baris ini menampilkan gambar merah (yang hanya berisi data saluran biru) di subplot pertama (axs[0]). Parameter cmap='gray' menentukan bahwa colormap skala abu-abu harus digunakan untuk visualisasi.  
### D. Menghitung Histogram: 
***hist = cv2.calcHist([biru],[0],None,[256],[0,256])***: Baris ini menghitung histogram intensitas piksel hijau pada gambar biru menggunakan fungsi cv2.calcHist dari OpenCV. Berikut rincian argumennya:  
[hijau]: List berisi array gambar yang akan dianalisis (dalam kasus ini, gambar saluran hijau).  
[0]: List yang menentukan saluran mana yang akan digunakan untuk histogram (dalam kasus ini, hanya saluran pertama, yaitu biru).  
None: Argumen ini tidak digunakan dalam konteks ini.  
[256]: Ini menentukan jumlah bin histogram (256 dalam kasus ini).  
[0,256]: Ini mendefinisikan rentang nilai intensitas yang akan dipertimbangkan (dari 0 hingga 255 untuk intensitas piksel).  
### E. Memplot Histogram:  
***axs[1].plot(hist)***: Baris ini memplot histogram yang dihitung di subplot kedua (axs[1]). Fungsi plot membuat plot garis dari data histogram.  
### F.Menampilkan Plot:  
***plt.show()***: Baris ini menampilkan seluruh figure, termasuk kedua subplot dengan gambar saluran biru dan histogram yang sesuai.    

# 10. AMBANG BATAS  
gray = cv2.cvtColor(citra_cerah, cv2.COLOR_RGB2GRAY)  
fig, axs = plt.subplots (2, 2, figsize=(10,10))  

(thresh, binary1) = cv2.threshold(gray, 0, 0, cv2.THRESH_BINARY)  
axs[0,0].imshow(binary1, cmap = 'gray')  
axs[0,0].set_title('NONE')  

(thresh, binary2) = cv2.threshold(gray, 120, 255, cv2.THRESH_BINARY)  
axs[0,1].imshow(binary2, cmap = 'binary')  
axs[0,1].set_title('BLUE')  
  
(thresh, binary3) = cv2.threshold(gray, 145, 255, cv2.THRESH_BINARY)  
axs[1,0].imshow(binary3, cmap = 'binary')  
axs[1,0].set_title('RED-BLUE')  
  
(thresh, binary4) = cv2.threshold(gray, 180, 255, cv2.THRESH_BINARY)  
axs[1,1].imshow(binary4, cmap = 'binary')  
axs[1,1].set_title('RED-GREEN-BLUE')  

### A. Konversi ke Grayscale:  
**gray** = cv2.cvtColor(citra_cerah, cv2.COLOR_RGB2GRAY): Baris ini mengonversi gambar berwarna citra_cerah ke skala abu-abu dan menyimpannya di variable gray. Operasi thresholding umumnya lebih efektif diterapkan pada gambar grayscale.    
### B. Membuat Subplot:  
**fig, axs = plt.subplots (2, 2, figsize=(10,10))**: Baris ini membuat figure (fig) dan empat subplot (axs) yang diatur dalam format 2x2 grid. Parameter figsize mengatur ukuran keseluruhan figure.  
### C. Thresholding dengan Nilai Berbeda:  
Empat blok kode berikut melakukan operasi thresholding dengan nilai threshold yang berbeda:  
(thresh, binary1) = cv2.threshold(gray, 0, 0, cv2.THRESH_BINARY):  
Fungsi cv2.threshold digunakan untuk melakukan thresholding.  
Argumen pertama (gray) adalah gambar grayscale yang akan diproses.  
Argumen kedua (0) adalah nilai threshold. Seluruh piksel dengan intensitas kurang dari atau sama dengan 0 akan diubah menjadi hitam (0) di gambar output (binary1).  
Argumen ketiga (0) diabaikan dalam konteks THRESH_BINARY.  
Argumen keempat (cv2.THRESH_BINARY) menentukan tipe thresholding. Dalam hal ini, THRESH_BINARY digunakan, yang mengkategorikan piksel menjadi hitam (0) atau putih (255) berdasarkan   nilai threshold.
Blok kode serupa diterapkan untuk binary2, binary3, dan binary4, namun dengan nilai threshold yang berbeda:  
binary2: Threshold 120 (piksel di bawah 120 menjadi hitam).  
binary3: Threshold 145 (lebih ketat dari binary2).  
binary4: Threshold 180 (hanya piksel dengan intensitas sangat tinggi yang tetap putih). 
  
### D. Menampilkan Gambar Biner:  
Masing-masing blok kode thresholding di atas menghasilkan gambar biner yang disimpan di variable binary1, binary2, dst.  
Baris selanjutnya menampilkan gambar biner tersebut pada subplot yang sesuai:  
axs[0,0].imshow(binary1, cmap = 'gray'): Menampilkan binary1 di subplot kiri atas (axs[0,0]) menggunakan colormap 'gray' (sesuai karena gambar biner).  
axs[0,1].imshow(binary2, cmap = 'binary'): Menampilkan binary2 di subplot kanan atas (axs[0,1]) menggunakan colormap 'binary' (default hitam-putih).  
Baris serupa diterapkan untuk menampilkan binary3 dan binary4 pada subplot di baris ke-2.  

### E. Menambahkan Judul Subplot:  
**Baris axs[x,y].set_title('JUDUL')** menambahkan judul ke masing-masing subplot, menunjukkan nilai threshold yang digunakan.  

### F. Menampilkan Plot:  
**plt.show()**: Baris ini menampilkan figure yang berisi keempat subplot dengan gambar biner hasil thresholding dan judulnya.  

# 2. LANDASAN TEORI  

## LIBRARY  
Library (perpustakaan) dalam bahasa pemrograman adalah kumpulan kode yang telah ditulis sebelumnya dan dikemas menjadi satu unit yang dapat digunakan kembali untuk menyelesaikan berbagai tugas. Library ini umumnya dibagikan secara terbuka dan dapat diakses oleh programmer lain untuk menghemat waktu dan upaya dalam pengembangan program.  
## NUMPY  
NumPy adalah library Python fundamental yang digunakan untuk komputasi numerik tingkat lanjut. Ini menyediakan struktur data array multidimensi yang efisien dan performa tinggi, serta berbagai fungsi matematika, manipulasi array, operasi aljabar linear, dan lainnya. NumPy menjadi landasan bagi banyak library lain yang berfokus pada bidang seperti Machine Learning dan analisis data.  
## OPENCV  
OpenCV adalah library open-source yang populer untuk pemrosesan citra dan penglihatan komputer. Ini menyediakan berbagai fungsi dan algoritma untuk tugas-tugas seperti:  
- Deteksi objek dan wajah  
- Pelacakan gerakan  
- Segmentasi citra  
- Analisis struktur gambar  
- Kalibrasi kamera  
- Dan banyak lagi  
OpenCV mendukung berbagai bahasa pemrograman, termasuk Python, C++, dan Java, menjadikannya pilihan yang fleksibel untuk pengembangan aplikasi penglihatan komputer.  
## MATPLOTLIB  
Matplotlib adalah library Python yang banyak digunakan untuk pembuatan plot dan visualisasi data. Ini menyediakan berbagai jenis plot, seperti scatter plot, line plot, histogram, dan bar chart. Matplotlib menawarkan kontrol yang baik terhadap tampilan plot, memungkinkan Anda untuk kustomisasi sumbu, label, warna, gaya garis, dan elemen lainnya.
## WARNA RGB  
RGB adalah singkatan dari Red, Green, Blue (Merah, Hijau, Biru). Ini merupakan model warna aditif yang digunakan untuk mewakili warna pada perangkat elektronik seperti monitor komputer, televisi, dan smartphone. Model ini bekerja berdasarkan prinsip bahwa warna-warna cahaya primer, yaitu merah, hijau, dan biru, dapat dicampurkan dengan berbagai proporsi untuk menghasilkan hampir semua warna yang terlihat oleh mata manusia.  
## KONTRAS IMAGE  
Kontras gambar mengacu pada perbedaan tingkat kecerahan (atau intensitas) antara bagian-bagian gambar. Perbedaan kontras yang tinggi menghasilkan gambar yang lebih jelas dan tajam, sedangkan kontras yang rendah menghasilkan gambar yang lebih datar dan kurang jelas.  
## HISTOGRAM  
Histogram adalah representasi grafis dari distribusi frekuensi data numerik. Dalam konteks gambar, histogram menunjukkan frekuensi kemunculan setiap nilai intensitas piksel pada gambar. ## GRAYSCALE  
Grayscale (skala abu-abu) mengacu pada representasi gambar yang hanya menggunakan tingkat keabuan untuk menampilkan detail, alih-alih menggunakan warna.  
Dalam dunia gambar digital, setiap piksel biasanya diwakili oleh kombinasi nilai merah (Red), hijau (Green), dan biru (Blue)  dengan skala intensitas dari 0 (hitam) hingga 255 (putih). Gambar berwarna terbentuk dari kombinasi intensitas ketiga warna ini pada setiap piksel.  
## AMBANG BATAS & THRESHOLD  
Ambang batas atau threshold adalah nilai kritis yang digunakan untuk membedakan antara dua kategori atau kondisi. Dalam berbagai bidang, ambang batas memiliki peran penting dalam pengambilan keputusan, analisis data, dan kontrol sistem 
