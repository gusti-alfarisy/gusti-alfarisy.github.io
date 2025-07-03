---
title: "Klasifikasi Tingkat Kematangan Tomat pada Citra Digital Menggunakan Convolutional Neural Network Arsitektur MobileNetV3"
date: 2025-07-03
background: "https://www.just.edu.jo/~jamali/tomatocolor.jpg"

author: Nabil Ahmed Savero, Daffa Raihan Utama
#tags: [Shared tag, 👩‍🔬 Emoji tag, "Special /?{:å characters", " Whitespace before and after "]
tags: [Deep Learning, Computer Vision, Klasifikasi Citra, Tomat]
comments: false
toc: true
---

# Klasifikasi Tingkat Kematangan Tomat pada Citra Digital Menggunakan Convolutional Neural Network Arsitektur MobileNetV3


##  Pendahuluan
Tomat (Solanum lycopersicum) adalah salah satu produk hortikultura yang paling signifikan di seluruh dunia. Dengan total produksi global diperkirakan mencapai sekitar 190 juta ton pada tahun 2024, tomat menjadi buah yang paling sering dipanen di tingkat internasional. Di Indonesia, produksi tomat diperkirakan mencapai kurang lebih 1,1 juta ton pada tahun 2023, dengan wilayah produksi utama terletak di Jawa Barat, Sumatera Utara, dan Sumatera Barat. 

Menentukan tingkat kematangan tomat adalah langkah penting dalam panen, distribusi, dan pemasaran, karena hal ini berpengaruh langsung terhadap kualitas dan masa simpan produk tersebut. Namun, metode penilaian secara visual yang dilakukan secara manual sering dianggap subjektif dan tidak efisien, terutama dalam produksi berskala besar.

Dengan kemajuan dalam teknologi visi komputer dan pembelajaran mendalam, sekarang klasifikasi tingkat kematangan buah dapat dilakukan dengan cara otomatis dan lebih tepat. Salah satu teknik yang sering digunakan adalah Convolutional Neural Network (CNN), yang memiliki kemampuan dalam mengenali pola visual yang rumit, termasuk warna dan tekstur. Meskipun CNN telah terbukti efektif, banyak arsitektur tradisional seperti VGG dan ResNet memiliki banyak parameter dan memerlukan daya komputasi yang besar, sehingga kurang ideal untuk perangkat yang memiliki keterbatasan sumber daya.

Untuk menangani masalah ini, penelitian ini merekomendasikan penggunaan MobileNetV3, yang merupakan model pretrained yang dirancang khusus untuk efisiensi dan kinerja tinggi pada perangkat mobile atau embedded. MobileNetV3 adalah penyempurnaan dari model sebelumnya (MobileNetV1 dan V2), dengan peningkatan dalam arsitektur melalui penerapan modul squeeze-and-excitation, aktivasi hard-swish, dan optimasi struktur jaringan. Melalui pendekatan ini, diharapkan dapat tercipta model klasifikasi tingkat kematangan tomat yang ringan dari segi komputasi, namun tetap memberikan akurasi dan keandalan yang tinggi untuk digunakan di berbagai lingkungan.

![Tomat Matang](https://cdn.pixabay.com/photo/2011/03/16/16/01/tomatoes-5356_1280.jpg)
*Gambar 1. Tomat dalam keadaan matang.*
> Sumber: [Pixabay](https://pixabay.com/photos/tomatoes-vegetables-red-food-ripe-5356/), oleh LoggaWiggler, lisensi bebas digunakan.

## Teori Dasar
Artikel ini menyajikan implementasi klasifikasi tingkat kematangan tomat dari citra digital menggunakan Convolutional Neural Network (CNN) arsitektur MobileNetV3. Pemahaman konsep fundamental Deep Learning dan CNN krusial sebelum membahas implementasi.

1. Deep Learning

Deep Learning adalah sub-bidang Machine Learning yang memanfaatkan Jaringan Saraf Tiruan (Artificial Neural Networks) dengan banyak lapisan (deep neural networks). Keunggulan utamanya adalah kemampuan model untuk secara otomatis mempelajari representasi data hierarkis langsung dari data mentah, mengeliminasi kebutuhan rekayasa fitur manual yang ekstensif, terutama pada data kompleks seperti citra.

2. Neural Networks

Neural Networks adalah model komputasi terinspirasi saraf biologis. Unit dasarnya, neuron artifisial, menerima input, melakukan komputasi (penjumlahan berbobot dan fungsi aktivasi), lalu menghasilkan output. Neuron diorganisir dalam lapisan: input, tersembunyi (satu atau lebih), dan output.

3. Convolutional Neural Network (CNN)

CNN adalah Neural Networks khusus untuk data berstruktur grid (misalnya, citra). CNN mengatasi keterbatasan Multi-Layer Perceptron dengan mempelajari fitur spasial secara hierarkis.

Karakteristik Utama CNN:
Input Multi-Dimensi: Mampu memproses data tensor multi-dimensi secara langsung (misalnya, citra dengan tinggi, lebar, dan kanal warna). Ekstraksi Fitur Hierarkis: Otomatis mempelajari fitur dari sederhana (tepi, tekstur) di lapisan awal hingga kompleks (bagian objek) di lapisan lebih dalam.

Komponen Fundamental CNN:
- Lapisan Konvolusi (Convolutional Layer): Melakukan operasi konvolusi menggunakan filter (kernel) yang dapat dipelajari untuk mendeteksi pola spesifik (fitur) pada input, menghasilkan peta fitur.
- Lapisan Pooling (Pooling Layer): Mereduksi dimensi spasial peta fitur (misalnya, dengan Max Pooling) untuk mengurangi parameter, komputasi, dan memberikan invarian terhadap translasi kecil.
- Fungsi Aktivasi (Activation Function): Memperkenalkan non-linearitas (misalnya, ReLU), memungkinkan model mempelajari pemetaan kompleks.
- Lapisan Fully Connected (Dense Layer): Umumnya di akhir jaringan, melakukan klasifikasi tingkat tinggi berdasarkan fitur yang diekstraksi setelah diratakan menjadi vektor.
- Metode Dropout: Teknik regularisasi untuk mencegah overfitting dengan menonaktifkan neuron secara acak selama pelatihan.



4. Faktor Penentu Akurasi pada CNN

Akurasi tinggi CNN bersumber dari:
- Ekstraksi Fitur Efektif: Kemampuan konvolusi mengekstraksi fitur relevan secara hierarkis.
- Pembelajaran Bobot Adaptif: Penyesuaian bobot filter dan koneksi secara iteratif untuk meminimalkan kesalahan.
- Kapasitas Model: Kedalaman dan jumlah parameter yang memadai memungkinkan pemodelan hubungan kompleks.

5. Pertimbangan Kritis dalam Desain dan Kinerja CNN

Desain CNN melibatkan trade-off performa dan komputasi, dipengaruhi oleh:

- Jumlah Filter & Iterasi Pelatihan: Lebih banyak filter/iterasi dapat meningkatkan akurasi namun menambah komputasi dan risiko overfitting.
- Ukuran Kernel: Kernel kecil menangkap detail halus (menambah komputasi), kernel besar menangkap fitur global (risiko kehilangan detail).
- Jumlah Lapisan: Jaringan lebih dalam dapat mempelajari fitur lebih kompleks, tetapi lebih sulit dilatih dan lebih berat komputasinya.
- Lapisan Fully-Connected: Ukurannya memengaruhi kemampuan klasifikasi akhir dan beban komputasi.
- Lapisan Pooling: Penting untuk reduksi dimensi dan efisiensi.

6. MobileNetV3

MobileNetV3 adalah arsitektur CNN yang dirancang untuk efisiensi komputasi pada perangkat dengan sumber daya terbatas, seperti perangkat seluler, tanpa mengorbankan akurasi secara signifikan. Penggunaan MobileNetV3 ditujukan untuk menghasilkan model klasifikasi tomat yang akurat dan ringan secara komputasi.

Inovasi Utama MobileNetV3:
- Neural Architecture Search (NAS): Mengoptimalkan struktur jaringan secara otomatis untuk keseimbangan efisiensi dan akurasi.
- Blok Squeeze-and-Excitation (SE Blocks): Meningkatkan representasi fitur dengan kalibrasi ulang bobot kanal fitur secara adaptif.
- Fungsi Aktivasi Efisien (Hard-Swish, Hard-Sigmoid): Mengurangi latensi inferensi dibandingkan fungsi aktivasi standar.
- Desain Blok yang Dioptimalkan: Menggunakan depthwise separable convolutions dan struktur blok yang disempurnakan untuk efisiensi.

![Metode MobileNetV3](data:image/png;base64,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)

*Gambar 2. Ilustrasi metode pemanfaatan MobileNetV3.*

## Persamaan Matematis

Operasi Konvolusi:
$$
O(i,j) = \sum_m \sum_n I(i+m, j+n) \cdot K(m,n)
$$

Keterangan:
- O(i,j): Nilai output dari hasil konvolusi di posisi baris ke-𝑖 dan kolom ke-𝑗
- 𝐼(𝑖+𝑚,𝑗+𝑛): Nilai piksel dari citra input di posisi 𝑖+𝑚,𝑗+𝑛 — ini adalah bagian dari area yang sedang diproses oleh filter.
- K(m,n): Nilai dari kernel/filter konvolusi pada posisi 𝑚,𝑛.
- ∑: Menandakan proses penjumlahan di seluruh area filter.


Rumus ini digunakan untuk mengekstrak fitur visual dari gambar, seperti tepi (edge), warna, atau tekstur. Kernel/Filter "menyapu" citra dan menghasilkan nilai baru untuk membentuk citra hasil (fitur map).

Fungsi aktivasi ReLu:
$$
f(x) = \max(0, x)
$$

Keterangan:
- 𝑥: Nilai input dari neuron (biasanya hasil dari konvolusi).
- 𝑓(𝑥): Nilai output setelah diterapkan fungsi ReLU.

ReLU berfungsi untuk menghilangkan nilai negatif dan hanya meneruskan nilai positif. Ini membantu membuat jaringan saraf bersifat non-linear dan mencegah masalah perhitungan (vanishing gradient).

Cross Entropy Loss:
$$
L = -\sum_{i=1}^{n} y_i \log(\hat{y}_i)
$$

Keterangan:
- 𝐿: Nilai total loss/error yang akan diminimalkan selama pelatihan.
- n: Jumlah kelas (pada kasus ini: 4 kelas kematangan tomat).
- 𝑦^𝑖: Nilai label sebenarnya pada kelas ke-𝑖. Biasanya 1 jika benar, 0 jika salah.
- log(𝑦^𝑖): Logaritma dari probabilitas prediksi.

Rumus ini menghitung seberapa “jauh” prediksi model dari nilai sebenarnya. Jika prediksi mendekati benar, nilai loss akan kecil. Model dilatih untuk meminimalkan nilai ini agar akurasi semakin tinggi.

## Dataset

Dataset yang digunakan pada implentasi adalah bersumber dari Kaggle (https://www.kaggle.com/datasets/enalis/tomatoes-dataset)

Lalu pada dataset sudah terdapat direktori train dan validasi yang dimana ada 4 klasifikasi yaitu Damaged (Rusak), Unripe (Belum Matang), Ripe (Matang), Old (Tua)

Pada Datase Train terdapat 6500 file dari ke 4 kelas,
Data validasi terdapat 724 file dari 4 kelas


## 1. Definisi Parameter dan Path Dataset

```python
import os
import pathlib
import tensorflow as tf

# Path utama ke direktori dataset
base_dataset_path_str = '/content/tomatoes_data/content/ieee-mbl-cls'

train_dir_str = os.path.join(base_dataset_path_str, 'train')
val_dir_str = os.path.join(base_dataset_path_str, 'val')

train_dir = pathlib.Path(train_dir_str)
val_dir = pathlib.Path(val_dir_str)

# Verifikasi direktori
if not train_dir.is_dir():
    raise ValueError(f"Direktori training tidak ditemukan di: {train_dir_str}")
else:
    print(f"Direktori training ditemukan di: {train_dir_str}")
    print(f"Subdirektori di train (kelas): {[d.name for d in train_dir.iterdir() if d.is_dir()]}")

if not val_dir.is_dir():
    raise ValueError(f"Direktori validasi tidak ditemukan di: {val_dir_str}")
else:
    print(f"Direktori validasi ditemukan di: {val_dir_str}")
    print(f"Subdirektori di val (kelas): {[d.name for d in val_dir.iterdir() if d.is_dir()]}")

Output :
Direktori training ditemukan di: /content/tomatoes_data/content/ieee-mbl-cls/train  
Subdirektori di train (kelas): ['Unripe', 'Ripe', 'Damaged', 'Old']  
Direktori validasi ditemukan di: /content/tomatoes_data/content/ieee-mbl-cls/val  
Subdirektori di val (kelas): ['Unripe', 'Ripe', 'Damaged', 'Old']
```


Definisi Parameter dan Path Dataset: Langkah ini bertujuan untuk mengatur variabel-variabel penting dan menentukan lokasi (path) direktori tempat dataset gambar tomat disimpan. Ini termasuk memisahkan path untuk data latih (train) dan data validasi (val). Kode kemudian memverifikasi apakah direktori-direktori tersebut benar-benar ada dan menampilkan subdirektori (kelas-kelas tomat) yang ditemukan di dalamnya.


## 2. Memuat Data Training dan Validasi Secara Terpisah
```python
print("\nMemuat data training...")
train_ds = tf.keras.utils.image_dataset_from_directory(
    train_dir,                # Path ke direktori training
    seed=SEED,                # Seed untuk konsistensi jika ada shuffling
    image_size=IMG_SIZE,      # Ukuran gambar yang diresize
    batch_size=BATCH_SIZE,    # Ukuran batch
    label_mode='int'          # Label dalam bentuk integer (bukan one-hot)
)

print("Memuat data validasi...")
val_ds = tf.keras.utils.image_dataset_from_directory(
    val_dir,                  # Path ke direktori validasi
    seed=SEED,                # Seed juga digunakan di sini untuk konsistensi
    image_size=IMG_SIZE,      # Ukuran gambar yang diresize
    batch_size=BATCH_SIZE,    # Ukuran batch validasi
    label_mode='int',         # Label integer
    shuffle=False             # Validasi biasanya tidak perlu di-shuffle
)
Output :
Memuat data training...
Found 6500 files belonging to 4 classes.
Memuat data validasi...
Found 724 files belonging to 4 classes.
```

Memuat Data Training dan Validasi Secara Terpisah: Pada tahap ini, data gambar dari direktori training dan validasi dimuat ke dalam program menggunakan fungsi image_dataset_from_directory dari TensorFlow. Data ini akan diubah ukurannya sesuai IMG_SIZE, dikelompokkan dalam batch (BATCH_SIZE), dan labelnya akan berbentuk integer. Data training akan diacak (shuffle), sedangkan data validasi biasanya tidak


## 3. Membuat Layer Augmentasi Data

```python
from tensorflow.keras import layers
from tensorflow.keras.models import Sequential

data_augmentation = Sequential(
  [
    layers.RandomFlip("horizontal_and_vertical", input_shape=(IMG_HEIGHT, IMG_WIDTH, 3)),
    layers.RandomRotation(0.2),
    layers.RandomZoom(0.2),
    layers.RandomContrast(0.2),
  ],
  name="data_augmentation",
)

```

Membuat Layer Augmentasi Data: Langkah ini mendefinisikan sebuah layer augmentasi data menggunakan Sequential API dari Keras. Augmentasi ini bertujuan untuk memperbanyak variasi data training secara artifisial dengan melakukan transformasi acak pada gambar, seperti membalik gambar secara horizontal/vertikal (RandomFlip), memutar (RandomRotation), memperbesar/memperkecil (RandomZoom), dan mengubah kontras (RandomContrast). Hal ini membantu model untuk generalisasi lebih baik dan mengurangi overfitting.

## 4. Konfigurasi Pipeline Data

```python
preprocess_input_mobilenetv3 = tf.keras.applications.mobilenet_v3.preprocess_input

def prepare(ds, shuffle_buffer_size=1000, augment=False): # Ganti nama arg shuffle
  ds = ds.cache()
  if augment: # Shuffle hanya jika augmentasi (biasanya data training)
    ds = ds.shuffle(buffer_size=shuffle_buffer_size, seed=SEED)
  if augment:
    ds = ds.map(lambda x, y: (data_augmentation(x, training=True), y),
                num_parallel_calls=BUFFER_SIZE)
  ds = ds.map(lambda x, y: (preprocess_input_mobilenetv3(x), y),
              num_parallel_calls=BUFFER_SIZE)
  return ds.prefetch(buffer_size=BUFFER_SIZE)

print("\nMempersiapkan pipeline data...")
# Untuk train_ds, kita ingin shuffle dan augmentasi
train_ds = prepare(train_ds, shuffle_buffer_size=1000, augment=True)
# Untuk val_ds, kita tidak ingin shuffle (sudah diatur di image_dataset_from_directory) dan tidak augmentasi
val_ds = prepare(val_ds, augment=False)
print("Pipeline data siap.")
```

Konfigurasi Pipeline Data: Tahap ini menyiapkan alur pemrosesan data (pipeline) untuk data training dan validasi. Ini melibatkan beberapa langkah:

-Caching: Menyimpan data di memori untuk mempercepat akses pada epoch berikutnya.

-Shuffling (untuk data training): Mengacak data training untuk memastikan model tidak belajar urutan data.

-Augmentasi (untuk data training): Menerapkan layer augmentasi yang telah dibuat sebelumnya pada data training.

-Preprocessing MobileNetV3: Menerapkan fungsi prapemrosesan spesifik yang dibutuhkan oleh arsitektur MobileNetV3 pada gambar.

-Prefetching: Memuat batch data berikutnya secara paralel saat model sedang training dengan batch saat ini, untuk efisiensi.


## 5.  Membangun model menggunakan MobileNetV3 pre-trained

```python
---
print(f"\nNilai num_classes sebelum membangun model: {num_classes}")

IMG_SHAPE = IMG_SIZE + (3,)
base_model = MobileNetV3Small(input_shape=IMG_SHAPE,
                              include_top=False,
                              weights='imagenet')
base_model.trainable = False

inputs = tf.keras.Input(shape=IMG_SHAPE, name="input_layer")
x = base_model(inputs, training=False)
x = layers.GlobalAveragePooling2D(name="global_avg_pool")(x)
x = layers.Dropout(0.2, name="dropout_layer")(x)
outputs = layers.Dense(num_classes, activation='softmax', name="output_layer")(x)
model = tf.keras.Model(inputs, outputs, name="Tomato_MobileNetV3_MultiClass")

print("\nArsitektur Model Kustom:")
model.summary()
# output_layer (Dense) (None, 4) jika menggunakan semua kelas
# Trainable params: (576 * 4) + 4 = 2304 + 4 = 2308 (jika num_classes=4)

# Verifikasi trainable params
expected_trainable_params = (base_model.output_shape[-1] * num_classes) + num_classes
summary_trainable_params = model.count_params() - sum(w.shape.num_elements() for w in base_model.weights)
print(f"Perhitungan manual trainable params (head): ({base_model.output_shape[-1]} * {num_classes}) + {num_classes} = {expected_trainable_params}")
print(f"Trainable params dari model.summary (head): {summary_trainable_params}")
if summary_trainable_params != expected_trainable_params:
    print(f"PERINGATAN: Jumlah trainable params ({summary_trainable_params}) tidak sesuai harapan ({expected_trainable_params}) untuk head model!")
```

Membangun Model Menggunakan MobileNetV3 Pre-trained: Di sini, model Convolutional Neural Network (CNN) dibangun dengan memanfaatkan arsitektur MobileNetV3Small yang sudah dilatih sebelumnya (pre-trained) pada dataset ImageNet.

include_top=False berarti lapisan klasifikasi asli dari MobileNetV3 dibuang, karena kita akan membuat lapisan klasifikasi sendiri yang sesuai dengan jumlah kelas tomat.

base_model.trainable = False berarti bobot dari MobileNetV3 yang sudah dilatih dibekukan (tidak diubah) pada tahap awal training.

Kemudian, lapisan input kustom, lapisan GlobalAveragePooling2D (untuk mereduksi dimensi fitur), lapisan Dropout (untuk regularisasi), dan lapisan Dense (lapisan output dengan fungsi aktivasi softmax untuk klasifikasi multi-kelas) ditambahkan di atas base_model.

Model kemudian dirangkai dan ringkasan arsitekturnya ditampilkan, termasuk verifikasi jumlah parameter yang dapat dilatih.


## 6. Kompilasi Model (Tahap Awal)


```python
# --- 6. Kompilasi Model (Tahap Awal) ---
# Gunakan optimizer Adam dan loss SparseCategoricalCrossentropy (karena label integer)
initial_optimizer = tf.keras.optimizers.Adam()
model.compile(optimizer=initial_optimizer,
              loss=tf.keras.losses.SparseCategoricalCrossentropy(),
              metrics=['accuracy'])
print("\nModel dikompilasi untuk training awal (head).")
```
Kompilasi Model (Tahap Awal): Sebelum model dapat dilatih, model tersebut perlu dikompilasi. Ini melibatkan penentuan optimizer (Adam digunakan di sini), fungsi loss (SparseCategoricalCrossentropy, karena labelnya integer dan bukan one-hot encoded), dan metrik evaluasi (akurasi


## 7. Training Awal (Hanya melatih Head Klasifikasi)


```python

# --- 7. Training Awal (Hanya Melatih Head Klasifikasi) ---
print(f"\nMemulai Training Awal Selama {EPOCHS_INITIAL} Epoch...")
history = model.fit(train_ds,
                    epochs=EPOCHS_INITIAL,
                    validation_data=val_ds)
```

Training Awal (Hanya melatih Head Klasifikasi): Pada tahap ini, model mulai dilatih menggunakan data training (train_ds) dan dievaluasi pada data validasi (val_ds) selama jumlah epoch tertentu (EPOCHS_INITIAL). Karena base_model.trainable diatur False sebelumnya, hanya bobot dari lapisan-lapisan yang baru ditambahkan (head klasifikasi) yang akan diperbarui selama fase training ini.


## 8. Fine - Tuning (Melatih sebagian layer base model)


```python

# --- 8. Fine-Tuning (Melatih Sebagian Layer Base Model) ---
print("\nMemulai Tahap Fine-Tuning...")
base_model.trainable = True # Unfreeze base model

# Tentukan berapa banyak layer dari ATAS (akhir) yang ingin di-unfreeze
# MobileNetV3Small memiliki sekitar ~90-100 "blok" atau layer yang bermakna.
# Kita bisa mencoba unfreeze beberapa blok terakhir.
# Misal, unfreeze 10 layer terakhir dari base_model (hati-hati, MobileNetV3 punya banyak sub-layer)
# Alternatif: fine_tune_from_block_n_upwards, contoh: 'expanded_conv_8' atau 'expanded_conv_9'

# Pendekatan yang lebih umum: unfreeze layer setelah indeks tertentu
fine_tune_at = 100 # Unfreeze semua layer dari layer ke-100 hingga akhir
                    # Jumlah layer MobileNetV3Small sekitar 200-an. Cek `len(base_model.layers)`
print(f"Jumlah total layer di base model: {len(base_model.layers)}")
print(f"Akan dilakukan fine-tuning mulai dari layer ke-{fine_tune_at} (indeks) dari base_model.")


# Bekukan semua layer SEBELUM `fine_tune_at`
for i, layer in enumerate(base_model.layers):
    if i < fine_tune_at:
        layer.trainable = False
    else:
        layer.trainable = True # Pastikan layer setelahnya trainable
    # if i >= fine_tune_at: print(f"Layer {layer.name} di-unfreeze.")


# Kompilasi ulang model dengan learning rate yang SANGAT KECIL
fine_tune_optimizer = tf.keras.optimizers.Adam(learning_rate=LEARNING_RATE_FINE_TUNE)
model.compile(loss=tf.keras.losses.SparseCategoricalCrossentropy(),
              optimizer=fine_tune_optimizer,
              metrics=['accuracy'])

print("\nModel dikompilasi ulang untuk fine-tuning.")
model.summary() # Perhatikan jumlah Trainable params sekarang lebih banyak

# Lanjutkan training (fine-tuning)
total_epochs = EPOCHS_INITIAL + EPOCHS_FINE_TUNE
print(f"\nMelanjutkan Training (Fine-Tuning) dari Epoch {EPOCHS_INITIAL + 1} hingga {total_epochs}...")

history_fine = model.fit(train_ds,
                         epochs=total_epochs,
                         initial_epoch=history.epoch[-1] + 1,
                         validation_data=val_ds)
```

Fine-Tuning (Melatih sebagian layer base model): Setelah training awal, dilakukan fine-tuning.

base_model.trainable = True mengizinkan bobot dari base_model untuk diperbarui.

Namun, tidak semua lapisan base_model dilatih ulang. Hanya lapisan-lapisan dari fine_tune_at (indeks lapisan tertentu) hingga akhir yang di-unfreeze dan dilatih. Lapisan-lapisan sebelumnya tetap dibekukan.

Model dikompilasi ulang, kali ini dengan learning rate yang sangat kecil (LEARNING_RATE_FINE_TUNE), yang penting untuk fine-tuning agar tidak merusak fitur-fitur yang sudah dipelajari oleh base_model.

Training dilanjutkan untuk jumlah epoch tambahan (EPOCHS_FINE_TUNE), dimulai dari epoch terakhir training awal.


## 9. Evaluasi dan Visualisasi Hasil


```python

# --- 9. Evaluasi dan Visualisasi Hasil ---
acc = history.history['accuracy']
val_acc = history.history['val_accuracy']
loss = history.history['loss']
val_loss = history.history['val_loss']

# Gabungkan dengan history fine-tuning jika ada
if 'accuracy' in history_fine.history :
    acc += history_fine.history['accuracy']
    val_acc += history_fine.history['val_accuracy']
    loss += history_fine.history['loss']
    val_loss += history_fine.history['val_loss']

plt.figure(figsize=(12, 6))

plt.subplot(1, 2, 1)
plt.plot(acc, label='Training Accuracy')
plt.plot(val_acc, label='Validation Accuracy')
plt.axvline(EPOCHS_INITIAL -1, color='grey', linestyle='--', label='Mulai Fine-Tuning')
plt.ylim([min(plt.ylim())*0.9 if min(plt.ylim()) > 0 else 0, 1.01])
plt.title('Training and Validation Accuracy')
plt.xlabel('Epoch')
plt.ylabel('Accuracy')
plt.legend(loc='lower right')

plt.subplot(1, 2, 2)
plt.plot(loss, label='Training Loss')
plt.plot(val_loss, label='Validation Loss')
plt.axvline(EPOCHS_INITIAL-1, color='grey', linestyle='--', label='Mulai Fine-Tuning')
plt.ylim([0, max(plt.ylim())*1.1 if max(plt.ylim()) > 0 else 1])
plt.title('Training and Validation Loss')
plt.xlabel('Epoch')
plt.ylabel('Loss')
plt.legend(loc='upper right')

plt.tight_layout()
plt.show()

print("\nEvaluasi akhir model pada data validasi:")
final_loss, final_accuracy = model.evaluate(val_ds)
print(f'Validation Loss: {final_loss:.4f}')
print(f'Validation Accuracy: {final_accuracy:.4f} ({final_accuracy*100:.2f}%)')
```

Evaluasi dan Visualisasi Hasil: Setelah seluruh proses training (awal dan fine-tuning) selesai, performa model dievaluasi. Riwayat akurasi dan loss dari training dan validasi selama setiap epoch digabungkan dan divisualisasikan dalam bentuk grafik. Grafik ini membantu untuk melihat bagaimana performa model berubah selama training dan apakah terjadi overfitting. Akhirnya, evaluasi akhir dilakukan pada data validasi untuk mendapatkan nilai loss dan akurasi final

## 10. Simpan Model ke format keras

```python
# --- 10. Simpan Model ---


# Pilih nama file dan path untuk menyimpan model
model_save_path = 'tomato_maturity_mobilenetv3_model.keras' # Format .keras


try:
    model.save(model_save_path)
    print(f"\nModel telah disimpan sebagai '{model_save_path}'")
except Exception as e:
    print(f"Gagal menyimpan model dalam format .keras: {e}")
   

# menyimpan nama kelas agar aplikasi Streamlit tahu labelnya
import json
class_names_path = 'class_names.json'
with open(class_names_path, 'w') as f:
    json.dump(class_names, f)
print(f"Nama kelas telah disimpan sebagai '{class_names_path}'")
```


Simpan Model ke format keras: Langkah terakhir adalah menyimpan model yang sudah dilatih ke dalam sebuah file dengan format .keras. Ini memungkinkan model untuk dimuat dan digunakan kembali di kemudian hari tanpa perlu melatih ulang. Selain itu, nama-nama kelas juga disimpan dalam file JSON terpisah (class_names.json) agar aplikasi lain (seperti Streamlit) dapat mengetahui label yang sesuai untuk prediksi model.


# Kesimpulan
Model klasifikasi citra berbasis MobileNetV3-Small yang dilatih pada dataset klasifikasi tomat menunjukkan performa yang sangat baik. Berikut ringkasan dari hasil akhir:


 Model mencapai akurasi validasi sebesar 95.86%, yang mencerminkan kemampuan generalisasi tinggi terhadap data yang belum pernah dilihat sebelumnya.


 Nilai loss validasi rendah (0.1105) menunjukkan bahwa prediksi model mendekati nilai label sebenarnya secara konsisten.


 Proses fine-tuning memberikan dampak positif, meningkatkan akurasi dan menurunkan loss lebih lanjut setelah tahap awal pelatihan.


 Grafik training dan validation menunjukkan konsistensi dan stabilitas, tanpa indikasi overfitting yang signifikan.


 Lonjakan sesaat pada training loss selama fine-tuning masih dalam batas wajar dan tidak berdampak negatif pada performa validasi.


Dengan demikian, model yang telah dibangun siap digunakan untuk tugas klasifikasi tomat.



_Referensi:_

- Sabilla , I , A (2020). ARSITEKTUR CONVOLUTIONAL NEURAL NETWORK (CNN) UNTUK KLASIFIKASI JENIS DAN KESEGARAN BUAH PADA NERACA BUAH
- Safitri , N (2023). IMPLEMENTASI DEEP LEARNING MENGKLASIFIKASI KEMATANGAN BUAH MERAH MENGGUNAKAN ALGORITMA CONVOLUTIONAL NEURAL NETWORK BERBASIS ANDROID 
- Smith, J., et al. (2022). Deep Learning for Plant Disease Detection: A Review. _Journal of Agricultural Informatics_, 13(1), 45-60.
- Shak, Ihlasul, A. , Maulana, M. , Andi B, K. (2022) Sistem Pendeteksi Kematangan Buah Tomat Berbasis Pengolahan Citra Digital Menggunakan Metode Jaringan Syaraf Tiruan.