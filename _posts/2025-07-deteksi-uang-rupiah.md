---
title: "Deteksi Objek Citra Uang Rupiah Menggunakan YOLOv11"
date: 2025-07-03
background: "https://learnlibre.com/wp-content/uploads/2022/04/1-Montessori-Science-Project-Ideas-Make-a-Diorama-624x351.jpg"

author: Muhammad Aldiansyah, Rendy Pernanda
#tags: [Shared tag, 👩‍🔬 Emoji tag, "Special /?{:å characters", " Whitespace before and after "]
tags: [Deep Learning, Computer Vision, YOLO, Object Detection]
comments: false
toc: true
---

# Deteksi Objek Citra Uang Rupiah Menggunakan YOLOv11

## 1.  Pendahuluan

Seiring pekembangan teknologi kecerdasan buatan dan algoritma deep lerning deteksi objek pada citra digital menjadi salah satu hal yang penting pada computer vision, Metode yang populer dan terkenal untuk melakukan deteksi objek secara cepat dan akurat salah sataunya adalah You Only Look Once atau lebih dikenal dengan YOLO, YOLO  dikenal dengan kegunaannya untuk mendeteksi berbagai objek dalam sekali proses pemindaian gambar, saat ini  versi terbaru  algoritma YOLO sudah mencapai YOLOv11 yang menawarkan  peningkatan dari sisi kecepatan dan akuras, hingga cocok digunakna pada aplikasi real-time, termasuk pda sistem pengenalan objek berbasis kamera.

Salah satu objek yang memiliki nilai penting yang bisa bisa dikenali secara otomatis  yaitu Uang kertas Rupiah dinegara ini uang Rupiah digunakan sebagai alat pembayaran utama dalam berbagai aktivitas ekonomi.Meskipun demikian, proses identifikasi uang secara manual oleh manusia masih kerap mengalami kesulitan, terutama dalam kondisi pencahayaan yang kurang, sudut pandang yang tidak optimal, atau kemiripan tampilan antar nominal. Tantangan ini semakin kompleks ketika pengenalan uang diterapkan dalam sistem elektronik seperti mesin kasir otomatis, aplikasi mobile, maupun perangkat validasi, yang membutuhkan proses deteksi yang cepat dan akurat.

Deteksi objek pada gambar uang rupiah bukan hanya soal teknis, tapi juga bisa jadi solusi untuk berbagai kebutuhan seperti edukasi, bantuan bagi penyandang disabilitas, dan pengembangan teknologi keuangan digital. Dengan menggunakan metode YOLOv11, sistem ini ditujukan untuk mengenali berbagai pecahan uang kertas rupiah dalam kondisi gambar yang beragam, seperti pencahayaan, warna, dan sudut pandang. Pendekatan ini diharapkan bisa membantu membangun sistem deteksi uang yang cepat, akurat, dan mudah diterapkan.

![Imgur](100k.jpg)

*Gambar 1: Ilustrasi sistem deteksi objek uang menggunakan YOLOv11*

---

## 2.  Deskripsi Metode

### 2.1 Deep Learning
Deep Learning adalah bagian dari kecerdasan buatan (AI) yang berkembang dari konsep jaringan saraf buatan, yaitu sistem yang meniru cara kerja otak manusia. Teknologi ini bekerja dengan banyak lapisan pemrosesan untuk mengenali pola atau ciri penting dari data secara otomatis. Karena kemampuannya ini, deep learning sangat efektif digunakan dalam berbagai tugas seperti mengenali gambar, suara, bahasa, atau menerjemahkan teks. Dengan pendekatan yang mendalam, deep learning mampu menyelesaikan masalah yang rumit dan berskala besar di berbagai bidang teknologi.(Raup et al., 2022)

Contoh rumus matematis sebagai berikut :

![Rumus sistematis](Rumus_sistematis.png)

Di mana:

`y`adalah output dari neuron.

`f` adalah fungsi aktivasi (misalnya, ReLU, Sigmoid, atau Tanh).

`wi`adalah bobot (weight) yang terhubung ke input x 

`b` adalah bias.

Proses deep learning untuk memodelkan pola-pola kompleks menjadikannya sangat efektif untuk berbagai tugas seperti pengenalan gambar, suara, dan pemrosesan bahasa alami.

### 2.2 Deteksi Objek dengan Convolutional Neural Network (CNN)
Deteksi objek adalah salah satu aplikasi utama dalam visi komputer yang bertujuan tidak hanya mengklasifikasikan tetapi juga melokalisasi objek dalam sebuah citra. Metode deep learning, khususnya Convolutional Neural Network (CNN), telah menjadi standar emas dalam tugas ini karena kemampuannya yang luar biasa dalam menangkap fitur visual kompleks seperti tekstur, bentuk, dan warna.

Operasi fundamental dalam CNN adalah konvolusi, di mana sebuah filter atau kernel digeser ke seluruh citra input untuk menghasilkan feature map. Operasi ini secara matematis didefinisikan sebagai:

![rumus sistematis](rumus_sistematis1.png)
Di mana:

`I`adalah matriks piksel dari citra input.

`K` adalah kernel (filter) konvolusi.

`S(i,j)` adalah elemen pada feature map yang dihasilkan.

Model-model seperti YOLO (You Only Look Once) dibangun di atas arsitektur CNN untuk melakukan deteksi objek secara efisien.


### 2.3  Pentingnya Labeling Dataset
labeling dataset merujuk pada proses penandaan atau pelabelan data yang akan digunakan untuk
melatih model Convolutional Neural Network (CNN) dalam pendeteksian nominal uang. Proses ini
sangat penting dalam machine learning dan deep learning, karena model hanya dapat belajar dan
mengidentifikasi pola atau fitur dalam data yang telah diberi label atau kategori yang jelas (Ibrahim et al.,
2023).

![Labeling data](labeling_data.png)

*Gambar 2: Gambar Labeling dataset*


### 2.4 YOLOv11
YOLO (You Only Look Once) secara luas dianggap sebagai salah satu algoritma utama untuk deteksi objek berdasarkan kerangka kerja pembelajaran mendalam. Algoritma ini memfasilitasi deteksi dan klasifikasi objek secara real-time baik dalam gambar maupun aliran video. YOLO beroperasi dengan mempartisi gambar input ke dalam grid dan secara bersamaan mengidentifikasi kotak pembatas dan kelas objek yang sesuai dalam setiap sel grid. Pemrosesan simultan ini memungkinkan YOLO untuk mencapai kecepatan dan efisiensi yang lebih unggul jika dibandingkan dengan metodologi deteksi objek konvensional (Redmon et al., 2016) . YOLOv11 adalah versi terbaru dari teknologi deteksi objek yang lebih cepat, lebih akurat, dan lebih ringan dibanding versi sebelumnya. Teknologi ini bisa digunakan di berbagai perangkat, mulai dari yang sederhana seperti kamera kecil hingga sistem besar berbasis cloud. Selain mendeteksi objek, YOLOv11 juga bisa mengenali posisi tubuh (pose), membedakan objek serupa (segmentasi), dan cocok untuk banyak bidang, seperti kesehatan dan deteksi emosi. Karena mudah diintegrasikan dan efisien, YOLOv11 menjadi pilihan yang baik untuk perusahaan atau pengembang yang ingin membangun sistem pengenalan gambar yang canggih dan praktis.
(Khanam et al., 2024)
![rsitektur yolo](architecture.png)

*Gambar 3: Gambar  Arsitekture YOLOv11*

*source: https://www.analyticsvidhya.com/blog/2024/10/yolov11-object-detection/*

Gambar diatas menunjukkan komponen utama dari YOLOv11, Arsitektur YOLOv11 dirancang untuk mengoptimalkan kecepatan dan akurasi, dengan mengembangkan kemajuan yang diperkenalkan pada versi YOLO sebelumnya seperti YOLOv8, YOLOv9, dan YOLOv10. Inovasi arsitektur utama pada YOLOv11 berkisar pada blok C3K2, modul SPFF, dan blok C2PSA, yang kesemuanya meningkatkan kemampuannya dalam memproses informasi spasial sembari mempertahankan kesimpulan berkecepatan tinggi.

### 2.5 Metrik Evaluasi Model
Untuk mengukur performa model deteksi objek secara kuantitatif, metrik standar industri digunakan. Tiga metrik yang paling umum adalah Precision, Recall, dan mean Average Precision (mAP).

- Precision: Mengukur akurasi prediksi positif. Dari semua objek yang diprediksi model, berapa persen yang benar?

![Precision](rumus_precision.png)

- Recall: Mengukur kelengkapan deteksi. Dari semua objek yang seharusnya terdeteksi, berapa persen yang berhasil ditemukan oleh model?

![Precision](rumus_Recall.png)

dimana:

`TP` (True Positive)

`FP` (False Positive)

`FN` (False Negative)
- mAP (mean Average Precision): Merupakan metrik utama untuk mengevaluasi performa model deteksi objek secara keseluruhan.
---

## 3.  Metodologi



---


### 3.1 Alur Pelatihan Model
Pelatihan ini bertujuan untuk menyediakan solusi yang akurat dan efisien dalam mendeteksi uang kertas rupiah menggunakan YOLOv11. Langkah-langkah Pelatihan ini terdiri dari:
 1. Pengumpulan Dataset: Mengumpulkan citra uang rupiah dari sumber terpercaya, termasuk pecahan-pecahan yang berbeda seperti 1000, 2000, 5000, 10000, 20000, 50000, dan 100000 rupiah. 
 2. Pelabelan Dataset: Memberikan label pada gambar uang secara manual untuk memastikan data siap digunakan untuk pelatihan model. 
 3. Pelatihan Model: Melatih YOLOv11 dengan dataset yang telah dilabeli, dengan pengaturan parameter yang dioptimalkan untuk mendeteksi uang rupiah dengan baik.
 4. Evaluasi Model: Menganalisis hasil model menggunakan metrik evaluasi standar, seperti akurasi dan kecepatan deteksi, untuk menilai performa dalam mengenali uang kertas rupiah secara real-time.
![alur penelitian](alur_penelitian.png)

*Gambar 4: Gambar Alur Pelatihan*

---

## 3.2  Pencarian Dataset

Dataset yang digunakan dalam Pelatihan ini berasal dari platform **Kaggle**, dengan judul:  
**"Indonesian Rupiah Currency Classification"**.

Dataset ini berisi **1.142 gambar uang Rupiah emisi tahun 2022**, yang mencakup tujuh jenis nominal pecahan uang kertas:
- Rp1.000
- Rp2.000
- Rp5.000
- Rp10.000
- Rp20.000
- Rp50.000
- Rp100.000

Setiap gambar dikelompokkan ke dalam folder berdasarkan nilai nominalnya. Struktur ini mempermudah proses pelabelan dan pelatihan model **deteksi atau klasifikasi visual**.

![data kaggle](data_kaggle.png)
*Gambar 5: Gambar dataset*

> Dataset ini sangat relevan untuk pengembangan sistem pengenalan uang otomatis berbasis **kecerdasan buatan (AI)**, 

> Berikut link Dataset Kaggle: https://www.kaggle.com/code/nasdevs/indonesian-rupiah-currency-classification/input 

---

## 3.3  Pelabelan Dataset

Proses pelabelan (labeling) dilakukan secara manual menggunakan platform **Roboflow**, yang menyediakan antarmuka visual untuk memberi anotasi pada setiap gambar uang Rupiah.

Masing-masing gambar diberi label sesuai **nominal pecahan uang**:
- 1.000 rupiah
- 2.000 rupiah
- 5.000 rupiah
- 10.000 rupiah
- 20.000 rupiah
- 50.000 rupiah
- 100.000 rupiah

![Pelabelan dataset](pelebelan_Dataset.png)
*Gambar 6: Gambar pelebelan dataset*

> Keakuratan dalam pelabelan sangat krusial. Label yang tepat memastikan model deteksi dapat membedakan setiap pecahan secara akurat, yang langsung berpengaruh terhadap performa model dalam mengenali uang di dunia nyata.

> Berikut Link Roboflow : https://app.roboflow.com/deeplearn-p4gr4/deteksi-uang-9obdk/browse?queryText=&pageSize=50&startingIndex=0&browseQuery=true 

---

## 3.4  Pelatihan Model

Model **YOLOv11** digunakan sebagai algoritma utama untuk mendeteksi objek dan mengklasifikasikan uang kertas berdasarkan nilai nominalnya. Pada pelatihan kali ini penting memperhatikan parameter-parameter agar proses training dapat terukur dan akurat.


### Parameter Eksperimen yang digunakan :

| Parameter                    | Nilai               | Keterangan                                                                 |
|-----------------------------|---------------------|----------------------------------------------------------------------------|
| Jumlah Epoch                | 100                 | Pelatihan dilakukan hingga 100 epoch; konvergen pada sekitar epoch 80–100 |
| Ukuran Batch (mini-batch)   | 16                  | Menyeimbangkan akurasi dan efisiensi memori GPU                           |
| Ukuran Gambar (imgsz)       | 640 x 640 piksel    | Resolusi input gambar yang konsisten dengan arsitektur YOLOv11            |
| Optimizer                   | Adam                | Adaptif terhadap learning rate dan cocok untuk data visual kompleks       |
| Learning Rate               | 0.001               | Default YOLOv11, stabil untuk tahap awal pelatihan                        |
| Device                      | GPU (device=0)      | Menggunakan GPU untuk mempercepat komputasi dan memanfaatkan paralelisme CUDA.                      |
| Pemilihan Model Terbaik     | Berdasarkan val_loss & mAP50 | Model disimpan otomatis (best.pt) saat metrik validasi optimal    |

Dengan pengaturan parameter tersebut, pelatihan model dilakukan secara optimal. Nilai mAP dievaluasi setiap epoch, dan checkpoint model terbaik disimpan secara otomatis oleh sistem YOLOv11

Berikut merupakan langkah awal untuk memulai kode pelatihan model **YOLOv11**, langkah pertama yang harus dilakukan adalah mengunduh dataset yang telah dilabeli sebagai berikut:

### 1. Download Dataset 
langkah awal pada pelatihan model adalah mendownload dataset yang telah diolah di roboflow dan telah dibagi menjadi dataset Train,valid,dan test untuk selanjutya di latih pada Yolov11

![download dataset roboflow](download_dataset_roboflow.png)
*Gambar 7: Gambar  dataset*


### 2. Instal Dependensi Yolov11

setelah dataset yang diolah di roboflow telah diinstal selanjutnya masuk dalam penginstallan depedensi Yolov11  yang diperlukan pada saat pelatihan model

**Install** library `ultralytics` untuk training, validasi, dan inference model YOLO:

```bash
pip install ultralytics --upgrade
```
**Install**  `OpenCV (untuk .show() image inference)` , yang berfungsi untuk Mengolah dan menampilkan gambar dan digunakan untuk deteksi objek gambar pada permodelan ini.
```bash
pip install opencv-python
```
**Install**   `PyTorch` , berfungsi untuk Menjalankan operasi neural network (training, inference).

```bash
pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118
```

 
**Install**   `matplotlib` ,`pandas` , `tqdm` , `scipy` berfungsi untuk Pengolahan data tabular dan menyimpan log hasil training/validasi, agar membantu menganalisis hasil model secara struktural.
```bash
pip install matplotlib tqdm seaborn pandas scipy


```

setelah menginstall depedensi yang akan digunakan untuk permodelan selanjutnya membuat Kode yang kamu berikan berfungsi untuk melatih dan mengevaluasi model deteksi objek YOLOv11s menggunakan dataset 

caranya dengan membuat folder train_yolo.py, berikut kodenya:



```python
from ultralytics import YOLO

if __name__ == '__main__':
    # Load a pretrained YOLOv11 model
    model = YOLO("yolov11s.pt") 

    # Train the model on your custom dataset
    results = model.train(
        data="data.yaml",  
        epochs=100,
        imgsz=640,
        batch=16,                
        device=0,                
        workers=4,               
        optimizer="Adam",         
        save=True,               
        project="runs/train",    
        name="exp_uang"          
    )

    # Evaluasi model
    metrics = model.val()
    
```
 
 Kode ini digunakan untuk melatih model deteksi objek YOLOv11 dengan data yang kita siapkan sendiri. Pertama, model pretrained (yang sudah pernah dilatih sebelumnya) dimuat supaya proses belajar jadi lebih cepat dan efisien. 
 
 Kemudian, model ini dilatih ulang menggunakan dataset khusus selama 100 epoch dengan parameter tertentu seperti ukuran gambar dan batch size. Setelah proses pelatihan selesai, model dievaluasi untuk mengetahui seberapa baik performanya dalam mengenali objek dari data baru. 
 
 Jadi, kode ini membantu kita membuat model deteksi objek yang lebih spesifik sesuai kebutuhan menggunakan teknik transfer learning.

setelah dibuat selanjutnya kita jalankan kode ini dengan cara:
```bash
python train_yolo.py
```
nantinya hasil model akan disimpan pada `runs/train/exp_uang/weights/best.pt`

setelah model dibuat  selanjutnya kita buat file baru `test.py` untuk melakukan deteksi objek menggunakan model YOLOv11s (yang sudah dilatih sebelumnya) dengan menggunakan dataset dari roboflow, berikut kodenya:


```python
from ultralytics import YOLO


if __name__ == '__main__':
    
    model = YOLO("runs/train/exp_uang/weights/best.pt")  

    # Coba infer ke 1 gambar
    results = model("tes3.jpg")  

    # Tampilkan hasil deteksi
    results[0].show()  

    # menyimpan hasil gambar deteksi
    results[0].save()  
 
```
Kode ini memuat model YOLO yang sudah dilatih, lalu digunakan untuk mendeteksi objek pada gambar tes3.jpg. Hasil deteksi ditampilkan dan disimpan sebagai file gambar baru dengan tanda objek yang terdeteksi.

setelah dibuat selanjutnya kita jalankan kode ini dengan cara:
```bash
python test.py
```






>Berikut merupakan LINK Github untuk program keseluruhan : Link Github	: https://github.com/Rendyzetx/Deep-Learning-Yolo




---

## 3.5  Evaluasi Model

Untuk Evaluasi pada model, kita menggunakan pengukuran seperti berikut:

- **Precision**  
  Mengukur seberapa banyak prediksi model yang benar dari semua prediksi yang dihasilkan.

- **Recall**  
  Mengukur sejauh mana model mampu mendeteksi semua objek yang sebenarnya ada di data.

- **mAP (mean Average Precision)**  
  Kombinasi precision dan recall. mAP digunakan sebagai indikator keseluruhan untuk menilai **ketepatan dan konsistensi prediksi** model terhadap berbagai kelas objek.






---
## 4.  Hasil dan Pembahasan

Hasil dan pembahasan dalam Pelatihan ini mencakup implementasi model **YOLOv11** dalam mendeteksi mata uang Rupiah dengan nominal mulai dari **Rp1.000 hingga Rp100.000**. Evaluasi dilakukan untuk melihat kemampuan sistem dalam mengenali pecahan uang, serta menganalisis performa model berdasarkan metrik evaluasi standar.

---

### 4.1  Hasil Deteksi Uang

Uji coba dilakukan menggunakan gambar uang sebagai input untuk mendeteksi nominal pecahannya.  


![pecahan uang RP.2000](2k.png)

*Gambar 8: pecahan uang RP.2000*

![pecahan uang RP.5000](5k.png)

*Gambar 9: pecahan uang RP.5000*

![pecahan uang RP.10000](10k.png)
*Gambar 10: pecahan uang RP.10000*


- **Gambar sebelah kiri**: citra asli uang Rupiah yang digunakan sebagai input.  
- **Gambar sebelah kanan**: hasil dari model **YOLOv11** setelah proses inferensi (**Output**).

Model mampu mengenali nominal dengan baik, ditandai oleh:
- Label kelas seperti `"2K"`, `"5K"`, `"10K"`.
- Nilai **confidence** yang tinggi, menandakan tingkat keyakinan model terhadap prediksi.

Hasil ini menunjukkan bahwa model tidak hanya mengenali warna, tetapi juga mempelajari bentuk dan ciri visual unik dari setiap nominal, dan berhasil mengenali nominal uang dengan confidance yang cukup tinggi.

---

### 4.2 Evaluasi Performa Model

Tahap selanjutnya pada evaluasi model, dilakukan menggunakan tiga metrik utama: **Precision**, **Recall**, dan **mAP (mean Average Precision)**.

---

#### 🔹 Precision

![Precision](precision.png)
*Gambar 11: Precision*

 **Grafik Precision-Confidence menunjukkan bahwa:**
- Precision sangat tinggi (mendekati 1.0) pada sebagian besar kelas, terutama saat confidence mendekati 1.
- Meskipun beberapa kelas seperti `5K` dan `2K` mengalami penurunan awal, precision meningkat tajam seiring confidence.
- Garis biru tebal mewakili rata-rata seluruh kelas dengan precision sempurna (1.00) pada confidence 1.000.

 **Kesimpulan**: Model sangat optimal dalam mengklasifikasi objek jika prediksi dilakukan dengan keyakinan tinggi.

---

#### 🔹 Recall


![ Recall](recall.png)
*Gambar 12:  Recall*

**Grafik Recall-Confidence menunjukkan:**
- Recall tetap tinggi (mendekati 1.0) pada confidence rendah hingga menengah.
- Namun, recall menurun tajam saat confidence tinggi, karena model mulai terlalu selektif.
- Hal ini menunjukkan adanya **trade-off**: jika hanya mengambil prediksi dengan confidence tinggi, maka potensi **false negative** meningkat.

 **Kesimpulan**: Model cenderung berhati-hati saat confidence di set  tertinggi, yang bisa membuat beberapa uang tidak terdeteksi. Karena itu, penting menyesuaikan nilai confidence agar seimbang antara jumlah objek yang terdeteksi dan ketepatan hasilnya.

---

#### 🔹 mAP (mean Average Precision)

![ mAP](map.png)
*Gambar 13:  mAP*


**Grafik mAP50 (IoU = 0.5) selama proses pelatihan menunjukkan:**
- sumbu X: jumlah **epoch** pelatihan
- sumbu Y: nilai **mAP50** (akurasi deteksi rata-rata)

Hasil:
- Nilai mAP50 meningkat secara konsisten dari awal hingga akhir pelatihan.
- Pada titik tertentu, mAP50 mencapai nilai mendekati **1.0**, yang menandakan **konvergensi model**.
- Artinya, model telah belajar cukup untuk mendeteksi objek dengan akurasi tinggi secara konsisten.

 **Kesimpulan**: Model menunjukkan pola konvergensi yang stabil, menandakan kemampuannya dalam memahami ciri khas dari tiap nominal uang secara konsisten. Hal ini juga mengindikasikan bahwa pengaturan parameter pelatihan seperti epoch, optimizer, dan batch size sudah sesuai. Meski begitu, nilai mAP50 masih berpotensi ditingkatkan lewat fine-tuning, seperti augmentasi data, pengujian arsitektur backbone lain, atau transfer learning dari domain sejenis. 

---



## 5.  Kesimpulan

Berdasarkan hasil dan implementasi model YOLOv11 untuk deteksi objek citra uang Rupiah, dapat disimpulkan beberapa hal berikut:

1.  Pelatihan ini berhasil membangun sistem deteksi otomatis untuk mengenali pecahan uang kertas Rupiah menggunakan algoritma **YOLOv11**, yang mampu mendeteksi objek dengan **akurasi tinggi** dan **respon cepat**.

2.  Dataset yang digunakan berasal dari **Kaggle**, terdiri dari 1.142 gambar uang Rupiah emisi tahun 2022 yang telah diklasifikasikan berdasarkan nominal, sehingga mendukung proses pelabelan dan pelatihan model secara optimal.

3.  Proses **pelabelan dataset** dilakukan menggunakan platform **Roboflow**, yang memungkinkan anotasi objek dilakukan secara manual dan akurat untuk setiap nominal uang.

4.  Hasil pelatihan model menunjukkan performa yang sangat baik, dengan nilai **precision dan recall mendekati 1.0**, serta nilai **mean Average Precision (mAP)** yang tinggi, yang menunjukkan **konsistensi model dalam mengenali objek dari berbagai kelas nominal**.


##   Daftar pustaka



1. Raup, A., Ridwan, W., Khoeriyah, Y., Supiana, & Zaqiah, Q. Y. (2022). Deep Learning dan Penerapannya dalam Pembelajaran. Jurnal Ilmiah Ilmu Pendidikan (JIIP), 5(9), 3258–3267

2. K. Simonyan and A. Zisserman, “Very Deep Convolutional Networks for Large-Scale Image Recognition,” Proc. Int. Conf. Learning Representations (ICLR), 2015. [Online]. Available: https://arxiv.org/abs/1409.1556 [9] J. Redmon, S. Divvala, R. Girshick, and A. Farhadi, “You Only Look


3. M. Ibrahim, R. Rahmadewi, dan L. Nurpulaela, "Pendeteksian Nominal Uang pada Gambar Menggunakan Convolutional Neural Network: Integrasi Metode Pra-pemrosesan Citra dan Klasifikasi Berbasis CNN," JATI (Jurnal Mahasiswa Teknik Informatika), vol. 7, no. 2, Apr. 2023

4. J. Redmon, S. Divvala, R. Girshick, and A. Farhadi, “You Only Look Once: Unified, Real-Time Object Detection,” in Proc. 2016 IEEE Conf. on Computer Vision and Pattern Recognition (CVPR), pp. 779–788, doi: 10.1109/CVPR.2016.91.

5. Khanam, Rahima & Hussain, Muhammad. (2024). YOLOv11: An Overview of the Key Architectural Enhancements. 10.48550/arXiv.2410.17725. 






