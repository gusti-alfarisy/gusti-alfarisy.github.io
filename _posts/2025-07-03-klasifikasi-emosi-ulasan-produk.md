---
title: "Klasifikasi Emosi Ulasan Produk pada Platform Shopee Menggunakan Model IndoBERT"
date: 2025-07-03
background: "http://thedevfeed.com/uploads/images/202401/image_870x_65ba709fe7777.jpg"

author: Alifah Nur Aisyah, Arifia Dyah Sulistyani
#tags: [Shared tag, 👩‍🔬 Emoji tag, "Special /?{:å characters", " Whitespace before and after "]
tags: [Deep Learning, NLP, Sentimen Analisis]
comments: false
toc: true
---

# Klasifikasi Emosi Ulasan Produk pada Platform Shopee Menggunakan Model IndoBERT

**PENDAHULUAN**

Seperti yang dapat kita amati dalam beberapa tahun terakhir, e-commerce telah menjadi salah satu sektor ekonomi dengan pertumbuhan yang sangat signifikan. Menurut laporan Simon Kemp dalam DataReportal, pada tahun 2025 diperkirakan orang dewasa semakin memilih berbelanja secara online, dengan lebih dari 1,7 miliar transaksi terjadi setiap minggunya, dimana kategori fashion menjadi yang paling dominan. Di Indonesia sendiri, Kementerian Perdagangan mencatat adanya peningkatan pengguna platform belanja online sebesar 11,9% dari tahun 2023 ke 2024. Fakta-fakta ini menunjukkan bahwa e-commerce kini bukan sekadar alternatif, melainkan telah menjadi kebutuhan utama dalam kegiatan berbelanja.

Di Indonesia e-commerce yang berkembang cukup pesat saat ini adalah aplikasi Shopee. Aplikasi ini menduduki peringkat kedua menurut Simon Kemp setelah Amazon. Aplikasi ini berisi kegiatan jual beli barang dan jasa secara online yang cukup populer dan berkembang (Sihombing et al., 2021). Hal ini dibuktikan juga dengan laporan oleh GoodStats bahwa Indonesia menjadi negara yang paling sering mengunjungi aplikasi Shopee dengan rata-rata 124,9 juta kunjungan perbulannya yang menunjukkan besarnya pola konsumsi masyarakat Indonesia untuk melakukan pembelian secara online. Dengan adanya perubahan pola konsumsi konsumen dapat meningkatkan aktivitas belanja secara online sehingga akan menaikkan juga volume ulasan produk yang dibeli.

Pernahkah terbayangkan bahwa kalimat ulasan ini dapat memuat lebih dari satu jenis emosi, tidak hanya sebatas bersifat positif atau negatif, tetapi juga dapat mencerminkan ekspresi emosi yang lebih spesifik seperti marah, senang, sedih, kecewa, maupun netral. Misalnya, seseorang membeli barang dan menuliskan sebuah ulasan terkait produk yang dibeli seperti,

“Barangnya sangat bagus dan menarik, tapi barangnya datang terlambat.”

Ulasan tersebut mengandung dua jenis emosi yaitu senang dan kecewa. Emosi tersebut ditandai senang karena produk yang diterima bagus dan menarik, tetapi kecewa karena keterlambatan dalam pengiriman. Atau mungkin dalam kasus ulasan-ulasan lainnya seperti,

“Produk yang dikirimkan tidak sesuai dengan yang dipesan.”, emosi kecewa dan marah.
“Biasa saja barangnya.”, emosi netral.
“Seller tidak amanah! Barang rusak parah, saya sangat marah”, emosi marah dan kecewa.


Kalimat-kalimat tersebut menjadi bukti bahwa setiap ulasan pasti menggambarkan ekspresi emosional dari persepsi dan pengalaman konsumen yang cukup kompleks. Oleh karena itu, kita perlu mengklasifikasikan dengan tepat secara otomatis supaya bisa dijadikan masukan berharga bagi penjual, bahan pertimbangan bagi calon konsumen, serta acuan untuk peningkatan untuk peningkatan kualitas platform e-commerce itu sendiri.


![Perbandingan antara analisis sentimen dan analisis emosi](https://www.mentionlytics.com/wp-content/uploads/2024/12/Sentiment-Analysis-vs-Emotion-Analysis-The-Key-Differences.jpg "Sumber: ResearchGate")  
**Gambar 1.** Perbandingan antara analisis sentimen dan analisis emosi
Sumber: [Mentionlytics](https://www.mentionlytics.com/blog/emotion-analysis/)


Sebenarnya analisis sentimen dan klasifikasi emosi dalam konteks ini sangat berbeda. Seperti pada gambar diatas, analisis sentimen lebih fokus pada klasifikasi yang umum seperti apakah ulasan itu bersifat positif atau negatif atau pendekatan yang sederhana. Sementara klasifikasi emosi lebih detail dan menggunakan pendekatan yang lebih kompleks untuk memahami emosi manusia lebih dalam seperti marah, senang, dan sebagainya


Untuk itu kita dapat melakukan analisis atau klasifikasi emosi untuk mengetahui emosi-emosi yang tertuang dalam teks ulasan. Meskipun sekilas tampak seperti ulasan bersifat positif atau negatif, emosi-emosi tersebut tidak selalu tersampaikan secara eksplisit dan sering kali tersembunyi di balik narasi yang terlihat netral atau positif yang membuat kita harus membaca ulasan berulang kali dan memahami emosi sebenarnya di ulasan.


Untuk memahami emosi yang tersembunyi itu kita memerlukan teknologi yang bisa memproses, membaca, dan memahami teks secara penuh pada ulasan. Teknologi yang sering digunakan untuk kasus seperti ini adalah teknologi dengan pendekatan Natural Language Processing (NLP). NLP atau pemrosesan bahasa alami adalah cabang dari kecerdasan buatan (AI) yang bikin komputer bisa mengerti bahasa manusia. Dengan NLP, mesin bisa membaca, memahami bahkan merespons teks atau ucapan manusia. Dalam konteks eksperimen ini, NLP dipakai untuk membantu sistem mengenali emosi yang terkandung dalam ulasan konsumen secara otomatis.


Untuk melakukan penelitian ini diperlukan sebuah pendekatan yang dapat memahami bahasa dengan baik untuk mengetahui kelola isi emosi di ulasan. Salah satu model NLP yang cukup terkenal adalah Bidirectional Encoder Representations from Transformers (BERT). Model BERT adalah model yang cukup terkenal di bidang NLP karena memiliki kemampuan untuk memahami konteks dan makna kata lebih dalam di sebuah teks kalimat. Pemahaman konteks ini dilakukan secara dua arah, berbeda dengan model tradisional lainnya. Keunggulan ini bisa memberikan hasil analisis yang lebih akurat dalam pemahaman emosi. Model BERT sendiri dapat membantu sebuah sistem dalam memahami bahasa manusia dengan melakukan pencarian hasil yang sangat relevan (Hidayat & Pramudita, 2024). Penggunaan model BERT ini bertujuan untuk mengukur bagaimana performa suatu model dalam menangani permasalahan klasifikasi emosi yang ada pada sebuah teks ulasan. Dengan harapan, hasil menggunakan model ini dapat memberikan data pengklasifikasian yang lebih akurat dibandingkan dengan model lainnya dan dapat membantu dalam meningkatkan kualitas analisis sentimen dalam platform e-commerce.


Pada kasus penelitian ini, teks ulasan berasal dari e-commerce Shopee yang ulasannya sebagian besar berbahasa Indonesia, kita memerlukan variasi BERT yang mampu memahami konteks bahasa Indonesia lebih dalam. BERT sendiri sebenarnya memiliki variasi yang cukup berkembang dan berbagai macam sesuai dengan kebutuhan penggunaan model seperti IndoBERT, BERT BASE, BERT LARGE, dan lainnya. Karena kita memerlukan model yang bisa menangani kompleksitas bahasa Indonesia atau berbagai tugas NLP berbasis Indonesia, maka model yang tepat adalah IndoBERT.


Meskipun jika kita menggunakan BERT sudah cukup bagus untuk melakukan penelitian ini, namun model IndoBERT akan lebih efektif dalam digunakan untuk ulasan yang berbahasa Indonesia dibandingkan dengan model BERT lainnya yang berbahasa Inggris sehingga kurang optimal jika digunakan untuk melakukan penelitian ini. Selain itu, IndoBERT juga itu sudah dilatih dengan korpus bahasa Indonesia.


Sebelum melakukan uji coba menggunakan model IndoBERT ini, kita perlu mencari tahu bagaimana cara model ini bekerja dan bagaimana performa model ini dalam melakukan analisis sentimen dan klasifikasi emosi terhadap teks ulasan secara otomatis menggunakan NLP. Berbeda dengan penelitian lainnya yang lebih umum menggunakan analisis sentimen sederhana seperti positif dan netral, kasus ini memiliki pendekatan sentimen yang lebih spesifik dengan memperhatikan klasifikasi emosi pada setiap ulasan.


Oleh karena itu, beberapa penelitian sudah membuktikan seberapa besar efektif model IndoBERT. Pada kasus penelitian pertama menggunakan ulasan terhadap aplikasi DANA yang diklasifikasikan menjadi 5 kategori emosi yaitu senang, puas, netral, kecewa, dan marah. Hasilnya menunjukkan model IndoBERT murni memiliki nilai akurasi 70% dan IndoBERT CNN 67% (Hakim, 2025). Sementara itu, Penelitian lain yang dilakukan oleh Wirayudha et al. (2025) pada aplikasi Acces By KAI menggunakan 6000 komentar pengguna menggunakan pendekatan IndoBERT. Hasilnya model ini berhasil mengklasifikasikan komentar dalam sentimen dengan akurasi 76%. Kedua penelitian ini saja sudah cukup menunjukkan kalau model IndoBERT dapat digunakan secara efektif dalam menganalisis opini dan emosi pengguna. Namun, penelitian yang dilakukan pada e-commerce Indonesia (menggunakan bahasa Indonesia) masih cukup terbatas khususnya pada penggunaan model IndoBERT dalam klasifikasi emosi pada ulasan pembeli. Padahal setiap ulasan saja bisa mengandung berbagai emosi yang beragam jika kita bisa memahami konteks dengan baik.


Mengingat pertumbuhan jumlah ulasan pengguna yang terus meningkat serta besarnya pengaruh ulasan terhadap perilaku konsumen dalam berbelanja dan eksplorasi terhadap klasifikasi emosi dalam konteks ulasan berbahasa Indonesia, khususnya dengan pendekatan IndoBERT, masih sangat terbatas. Harapannya penelitian ini dapat meningkatkan akurasi dalam menganalisa emosi pengguna sekaligus memberikan gambaran yang lebih mendalam tentang persepsi dan perasaan konsumen terhadap produk yang mereka beli.


Melalui penelitian ini, kita ikut serta berkontribusi dalam merancang sistem yang mampu mengklasifikasikan emosi otomatis dari teks ulasan di platform e-commerce menggunakan model IndoBERT. Dengan menggunakan lima emosi utama yaitu senang, kecewa, sedih, marah dan netral. Hasil klasifikasi pada penelitian ini bisa dimanfaatkan oleh pelaku bisnis, baik itu penjual maupun pemilik platform untuk lebih memahami perasaan konsumen, memperbaiki layanan, dan menyesuaikan strategi bisnis secara lebih personal dan tepat.

Selain itu, pendekatan yang digunakan pada penelitian ini diharapkan juga menjadi sebuah landasan dasar untuk terus mengembangkan Natural Language Processing dengan nuansa dataset lokal dan mendorong lebih banyak penelitian untuk mengenali lebih banyak jenis klasifikasi label emosi yang sering digunakan pada teks ulasan berbasis bahasa Indonesia, terutama di e-commerce Indonesia seperti, Tokopedia, Lazada, dan sebagainya.


**ARSITEKTUR INDOBERT**  


Arsitektur IndoBERT sama dengan BERT yang terdiri dari tumpukan Transformer encoder dengan lapisan-lapisan yang dapat memahami hubungan antar kata dalam sebuah kalimat. IndoBERT memiliki dua varian arsitektur: IndoBERT-base dan IndoBERT-large. IndoBERT-base memiliki 12 lapisan transformer, sedangkan IndoBERT-large memiliki 24 lapisan.


Dengan catatan pada penelitian ini menggunakan model IndoBERT BASE karena model ini sering digunakan untuk penelitian berskala kecil atau dataset yang digunakan tidak terlalu kompleks. Arsitektur IndoBERT BASE sendiri memiliki 12 lapisan encoder, 768 hidden layer , 12 attention head, dan total 110 juta parameter.


Secara rinci begini gambaran bagaimana arsitektur model IndoBERT yang digunakan:

![Arsitektur IndoBERT](https://www.researchgate.net/profile/Evi-Yulianti/publication/384510112/figure/fig1/AS:1293797678825475@1698053689446/Fine-tuned-IndoBERT-model-using-single-sentence-classification-approach.png "Sumber: ResearchGate")  
**Gambar 2.** Arsitektur IndoBERT yang telah di-fine-tune untuk klasifikasi satu kalimat.  
Sumber: [ResearchGate](https://www.researchgate.net/figure/Fine-tuned-IndoBERT-model-using-single-sentence-classification-approach_fig1_384510112)


Secara umum, model BERT (termasuk IndoBERT) dilatih menggunakan tugas MLM (Masked Language Modeling) dan NSP (Next Sentence Prediction) untuk menangkap representasi teks secara dua arah dengan menebak kata dalam kalimat dan memahami apakah kalimat tersebut saling terhubung. Setelah pra latih, IndoBERT dapat menyesuaikan dengan menambahkan lapisan keluaran untuk tugas spesifik. Dalam proses penyesuaian, bobot yang dipelajari selama pra-latih akan diperbarui berdasarkan dataset spesifik.


Misalnya ada teks ulasan seperti, “Aku senang barangnya sangat bagus”, maka model akan mengeluarkan hasil klasifikasi emosi berupa kategori “senang”.

Untuk bisa sampai pada hasil klasifikasi seperti itu, model IndoBERT perlu belajar dari data yang sudah dilabeli. Selama proses pelatihan, digunakan sebuah fungsi loss yang akan membantu model belajar dengan lebih baik. Saat proses pelatihan sedang berlangsung, model perlu tahu seberapa jauh prediksi yang dihasilkannya dari label yang sebenarnya. Nah, di sinilah fungsi loss bekerja. Dalam penelitian ini, kita dapat menggunakan fungsi Cross Entropy Loss yang umum untuk kasus mengklasifikasikan multi-kelas seperti pada kasus ini.


Fungsi ini bertujuan menghasilkan nilai yang besar saat prediksi model jauh dari label yang benar dan nilai kecil saat prediksi mendekati label yang tepat. Tujuan dari pelatihan adalah meminimalkan nilai loss ini agar model makin akurat dalam memprediksi emosi.


Persamaan matematisnya sebagai berikut:

L = - ∑(i=1 to N) ∑(j=1 to C) y_ij \* log(ŷ_ij)

Keterangan:
L : total nilai loss
N : jumlah data ulasan
C : jumlah kelas emosi (senang, kecewa, sedih, marah, netral)
y_ij: label sebenarnya (1 jika benar, 0 jika tidak)
ŷ_ij: probabilitas prediksi model untuk kelas ke-j pada data ke-i
Fungsi ini dijalankan otomatis oleh IndoBERT menggunakan pustaka Transformers selama proses fine-tuning. Semakin kecil nilai loss, berarti model semakin memahami pola data dengan baik.


**FLOWCHART**

```
flowchart

    Memulai program
        ↓
    Mengumpulkan data ulasan e-commerce (Shopee)
        ↓
    Pra-pemrosesan teks ulasan
         ↓
    Anotasi label emosi manual
        ↓
    Pembagian dataset menjadi data pelatihan dan pengujian
        ↓
    Fine tuning dan pelatihan IndoBERT dan label emosi
        ↓
    Klasifikasi emosi dan evaluasi performa model
        ↓
    Visualisasi Hasil & Kesimpulan
        ↓
    Selesai

```

- Memulai program


Tahapan awal yaitu memulai program dengan menyiapkan seluruh kebutuhan penelitian atau uji coba, dengan menyiapkan dataset yang akan dikumpulkan, platform pengujian seperti google colabs, perencanaan data dan pustaka yang akan digunakan.


- Mengumpulkan data ulasan e-commerce (Shopee)


Tahapan kedua ini melakukan pengambilan data ulasan secara manual pada ulasan produk di e-commerce Shopee dari berbagai kategori produk dan rating ulasan. Pengambilan teks ulasan tidak boleh mengambil ulasan produk hanya dari 1 rating saja supaya tidak terjadi emosi dominan, melainkan nilai emosi akan lebih beragam dan sesuai dengan label emosi. Kemudian, data yang dikumpulkan tersebut masih berupa data mentah yang perlu proses cleaning untuk menjadi data yang siap.

- Pra-pemrosesan teks ulasan

Pra-pemrosesan atau pre-processing adalah proses dimana data mentah yang telah dikumpulkan akan diproses menjadi data bersih yang siap untuk pelatihan dan pengujian model IndoBERT. Adapun proses pembersihan data dengan menghapus emoji, mengubah teks menjadi lowercase, penghapusan tanda baca, normalisasi, dan stopwords (menghapus kata tidak bermakna).


- Anotasi label emosi manual


Ketika data sudah bersih dan siap untuk diberikan label emosi secara manual. Setiap 1 ulasan akan diberikan 1 label emosi yang sesuai dengan ekspresi emosinya. Ada 5 kategori jenis emosi yaitu, marah, senang, sedih, kecewa, dan netral. Labelisasi emosi ini harus dibaca berulang kali dan memperhatikan dengan baik ekspresi emosi konsumen dalam menulis ulasan tersebut agar tidak salah dalam memberi label.


- Pembagian dataset dan fine-tuning


Saat dataset telah dibagi, selanjutnya melatih ulang model Indobert dengan data ulasan yang telah dilabelisasi secara manual agar dapat mengidentifikasi dan mengklasifikasikan setiap emosi yang terkandung dalam teks ulasan.


- Klasifikasi emosi dan evaluasi performa model


Tahap ketujuh yaitu memprediksi setiap ulasan untuk setiap emosi yang terkandung didalamnya dan mengevaluasi performa model dalam memprediksi emosi pada setiap ulasan. Pada tahapan ini juga, akan mengukur seberapa besar model mampu memprediksi secara akurat pada label emosi yang dilakukan secara manual dengan model yang sudah dilatih secara umum untuk memahami konteks bahasa Indonesia.


- Persamaan evaluasi kinerja model


Setelah model IndoBERT memprediksi emosi dari setiap ulasan produk si Shopee, langkah berikutnya adalah mengevaluasi seberapa baik performa model tersebut. Evaluasi ini tidak hanya berdasarkan hasil prediksi saja, tetapi juga dihitung menggunakan beberapa metrik klasifikasi yang umum digunakan, yaitu accuracy, precision,recall,dan F1-score.


Melalui metrik-metrik ini, kita bisa melihat sejauh mana model mampu mengenali emosi seperti senang, kecewa, marah, sedih dan netral secara akurat dari teks ulasan konsumen. Rumus matematis berikut digunakan untuk membantu mengukur performa tersebut secara kuantitatif.


**Accuracy**
Accuracy menunjukkan seberapa besar proporsi prediksi emosi yang benar dari seluruh data ulasan yang diuji


Accuracy = (TP + TN) / (TP + TN + FP + FN)


**Precision**
Precision digunakan untuk mengukur seberapa tepat model saat memprediksi suatu emosi tertentu. Misalnya, ketika model memprediksi emosi “kecewa”, precision menunjukkan berapa banyak dari prediksi tersebut yang memang benar-benar termasuk emosi “kecewa”


Precision = TP / (TP + FP)


**Recall**
Recall menunjukan seberapa baik model dalam menemukan semua ulasan yang seharusnya masuk ke dalam kategori emosi tertentu. Misalnya, seberapa banyak ulasan yang benar-benar menunjukan emosi berupa “marah” berhasil ditangkap oleh model.


Recall = TP / (TP + FN)


**F1-Score**
F1-score adalah kombinasi dari presisi dan recall. Dalam konteks ulasan Shopee, F1-score membantu kita memahami keseimbangan antara kemampuan model dalam menemukan emosi yang benar dan ketepatan model dalam menemukan emosi yang benar dan ketepatan model dalam membuat prediksi tersebut.


F1-Score = 2 _ Precision _ Recall / (Precision + Recall)


Keterangan:
TP (True Positive): Model berhasil memprediksi emosi dengan tepat
TN (True Negative): Model berhasil mengenali bahwa ulasan bukan dari emosi tertentu
FP (False Positive): Model salah mengira sebuah emosi padahal bukan
FN (False Negative): Model gagal mengenali emosi yang sebenarnya ada dalam ulasan


Persamaan-persamaan ini digunakan selama evaluasi model IndoBERT menggunakan data ulasan Shopee untuk menilai seberapa efektif model dalam mengenali emosi-emosi seperti senang, marah, kecewa dsb.


- Visualisasi hasil & kesimpulan


Terakhir, menampilkan keseluruhan hasil evaluasi model, baik dalam bentuk akurasi, recall, precision, dan F-1 Score di confusion matriks dan menampilkan juga hasil evaluasi model pada setiap label emosi dalam tugas model melakukan klasifikasi emosi pada teks ulasan produk.


**DATASET**


Dataset yang dikumpulkan diperoleh secara manual atau copy paste dengan mengumpulkan ulasan produk dari platform e-commerce Shopee. Data-data ini diambil dari produk yang memiliki ulasan produk lebih dari 1000 untuk memudahkan proses pengumpulan data. Data ulasan diambil dari berbagai kategori produk secara acak, seperti elektronik, fashion, makanan, peralatan rumah, kosmetik, dan lainnya. Ulasan tersebut kemudian dipilih berdasarkan rating bintang secara acak, dimulai dari rating 1 hingga 5. Hal ini dikarenakan untuk menghasilkan dataset yang memiliki emosi berbagai macam dan tidak mendominasi ulasan-ulasan positif dari pengguna saja. Jumlah ulasan yang terkumpul sebanyak 7000 data ulasan mentah yang belum di preprocessing dan belum siap untuk dijadikan sebagai data latih model. Data yang diambil hanya mempertimbangkan rating dan ulasan. Setelah itu, data kan diberikan label emosi secara manual dengan mempertimbangkan emosi dominan yang terkandung didalam setiap ulasan. Adapun label emosi yang digunakan yaitu senang, kecewa, marah, sedih, dan netral. Kemudian, dataset yang sudah dilabelisasi telah siap untuk ke tahap processing dengan pembagian menjadi data pelatihan dan data pengujian.


**DESAIN EKSPERIMEN**


Sebelum melakukan sebuah eksperimen, kita perlu merancang terlebih dahulu bagaimana desain eksperimen yang akan digunakan. Desain eksperimen ini dapat membantu kita dalam menjalankan proses pelatihan model secara maksimal. Pada eksperimen kali ini kita menggunakan model IndoBERT variasi IndoBERT-BASE yang perlu dipanggil kita panggil dengan kata kunci "indobenchmark/indobert-base-p1" dari pustaka Hugging Face Transformers. Setelah menentukan jenis model, kita perlu menetapkan jumlah label emosi dan epoch yang akan kita dijalankan. Model ini akan melakukan lima kali epoch dengan lima parameter label emosi, yaitu marah, senang, kecewa, sedih, dan netral. Sedangkan jumlah epoch sebenarnya bebas ditentukan sesuai dengan kebutuhan eksperimen, tetapi kali ini memutuskan untuk melakukan lima epoch saja agar tidak terjadinya overfitting.


Misalnya, kalau seseorang belajar terus menerus pada satu hal dalam waktu yang sangat lama maka dia akan terlalu fokus dan kesulitan dalam memahami hal lainnya. Model juga mengalami hal yang sama terus menerus belajar pada data yang sama maka model akan terlalu pintar menebak data yang ada dan mengurangi ke akuratan model.


Selama proses training dilakukan, kita menggunakan “per_device_train_batch_size=16, per_device_eval_batch_size=64 “ untuk memproses model belajar dalam 16 data sekaligus dalam satu kali batch training dan menggunakan batch yang lebih besar yaitu 64 agar evaluasi berjalan dengan cepat dengan panjang maksimal tokenisasi (max_length=128) pada pelatihan dan pengujian. Kita juga perlu memerlukan “save_steps=500, save_total_limit=3“, bertujuan gua mencetak setiap 500 step proses pelatihan agar dapat memantau hasil metrik hingga proses tersebut berakhir. Namun, kita hanya akan menyimpan 3 versi proses pelatihan terakhir saja. Nilai learning rate yang digunakan hanya nilai default dari Hugging Face yaitu (5e-5). Desain eksperimen terakhir, “do_eval=True“ berfungsi untuk memantau perkembangan performa model setelah proses pelatihan selesai dengan memberikan hasil nilai akurasi, precision, recall, dan F-1 Score sejak epoch pertama hingga epoch terakhir. Berikut tabel ringkas desain eksperimen :


| **Parameter desain eksperimen** | **Nilai**        |
| ------------------------------- | ---------------- |
| Model                           | IndoBERT-BASE    |
| Jumlah epoch                    | 5                |
| Batch size (Pelatihan)          | 16               |
| Batch size (Pengujian)          | 64               |
| Learning rate                   | Default : (5e-5) |
| Max length tokenisasi           | 128              |
| Save steps                      | 500              |
| Save total limit                | 3                |


**HASIL DAN PEMBAHASAN**


Pada tahap ini, proses pertama kali dilakukan dengan pengumpulan manual data ulasan produk dari platform Shopee. Proses pengambilan data difokuskan pada produk dengan berbagai kategori dan rating yang memiliki jumlah ulasan yang cukup untuk dilatih sebagai data machine learning. Dari proses tersebut, kami berhasil memperoleh sekitar 7000 data ulasan mentah.


**_Data Awal_**

Data yang diperoleh dari hasil pengumpulan data masih belum terstruktur dan mengandung sejumlah _noise_, seperti ulasan duplikat, entri kosong, serta karakter non-alfabet. Selain itu, data belum terstruktur dalam bentuk kategori atau label tertentu. Berikut ini adalah contoh data awal yang berhasil diambil:


| No  | Ulasan                                                                                                                                                                                                                                            |
| :-: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|  1  | Bahan:tipis Desain:kurang rapi Kualitas barang tidak sesuai yg di foto yg di pesan apa yg sampai apa,kecewa banget sama barangnya 😔 yg GK sesuai dgn realita.yg di pesan model tali samping yg sampai model serut mna kekecilan lgi ukuran nya🙄 |

Sangat berantakan dan tidak dapat digunakan dalam proses pre-trained model kan? Oleh karena itu diperlukan beberapa tahapan untuk memastikan bahwa ulasan tersebut siap digunakan dalam prose train model IndoBERT.


**_Pre-processing data (data cleaning)_**


Langkah ini melakukan preprocessing data terhadap data mentah guna meningkatkan kualitas data dan mengurangi potensi kesalahan saat pelatihan model. Pada tahap ini, masing-masing ulasan akan dibersihkan melalui beberapa tahap yiatu:


- Melakukan tahapan penghapusan emoji pada teks ulasan seperti 😔 🙄 😊 ⭐ dan sebagainya


| No  | Ulasan tanpa emoji                                                                                                                                                                                                                           |
| :-: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|  1  | Bahan:tipis Desain:kurang rapi Kualitas barang tidak sesuai yg di foto yg di pesan apa yg sampai apa,kecewa banget sama barangnya yg GK sesuai dgn realita.yg di pesan model tali samping yg sampai model serut mna kekecilan lgi ukuran nya |


- Melakukan lowercase (mengubah teks yang mengandung huruf besar menjadi huruf kecil semua)dan menghapus URL


| No  | Ulasan                                                                                                                                                                                                                                       |
| :-: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|  1  | bahan:tipis desain:kurang rapi kualitas barang tidak sesuai yg di foto yg di pesan apa yg sampai apa,kecewa banget sama barangnya yg gk sesuai dgn realita.yg di pesan model tali samping yg sampai model serut mna kekecilan lgi ukuran nya |


- Menghapus tanda baca “ :” , “,”, dan simbol lainnya


| No  | Ulasan                                                                                                                                                                                                                                       |
| :-: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|  1  | bahan tipis desain kurang rapi kualitas barang tidak sesuai yg di foto yg di pesan apa yg sampai apa kecewa banget sama barangnya yg gk sesuai dgn realita yg di pesan model tali samping yg sampai model serut mna kekecilan lgi ukuran nya |


- Melakukan normalisasi pada teks ulasan


| No  | Ulasan                                                                                                                                                                                                                                                          |
| :-: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|  1  | bahan tipis desain kurang rapi kualitas barang tidak sesuai yang di foto yang di pesan apa yang sampai apa kecewa banget sama barangnya yang tidak sesuai dengan realita yang di pesan model tali samping yang sampai model serut mana kekecilan lgi ukuran nya |


- Melakukan stopwords pada teks ulasan


| No  | Ulasan                                                                                                                                                                |
| :-: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|  1  | bahan tipis desain kurang rapi kualitas barang sesuai foto pesan kecewa banget barangnya sesuai realita pesan model tali samping model serut mna kekecilan lgi ukuran |

Setelah proses pembersihan, jumlah data yang tersisa dan valid untuk dianalisis adalah **7000 ulasan**. Contoh 10 baris data yang sudah melalui proses _cleaning_ disajikan pada tabel berikut :

| No  | Ulasan                                                                                                                                                                 |
| :-: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|  1  | bahan tipis desain kurang rapi kualitas barang sesuai foto pesan kecewa banget barangnya sesuai realita pesan model tali samping model serut mana kekecilan lgi ukuran |


**_Proses Labelisasi_**


Data ulasan yang telah bersih akan melalui tahapan dianotasi (labelisasi) secara manual berdasarkan ekspresi emosi yang terkandung dalam setiap ulasan. Hal ini dilakukan agar data ulasan memiliki labelisasi emosi yang lebih sesuai dan akurat. Kategori emosi yang digunakan merujuk pada skema emosi dasar seperti:

- **Senang** (Joy)
- **Kecewa** (Disappointed)
- **Sedih** (Sad)
- **Marah** (Angry)
- **Netral**

Proses labelisasi ini dilakukan dengan mempertimbangkan konteks kalimat dan kata-kata kunci yang muncul. Contoh hasil data setelah pelabelan emosi:

| No  | Ulasan                                                                                                                                                                 | Label Emosi |
| :-: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---------: |
|  1  | bahan tipis desain kurang rapi kualitas barang sesuai foto pesan kecewa banget barangnya sesuai realita pesan model tali samping model serut mana kekecilan lgi ukuran |   kecewa    |

Data ulasan yang telah dilabelisasi selanjutnya bisa masuk ke tahap model IndoBERT, pada tahap ini akan melakukan training dan validasi data berdasarkan ulasan yang telah dilakukan pembersihan. Pada tahapan selanjutnya juga akan menguji model dalam membaca teks.

Pastikan bahwa dataset yang disediakan sudah benar-benar siap masuk ke dalam proses pelatihan model ya! Jangan sampai ada dataset yang belum optimal dan dapat menganggu hasil akurasi model.


**IMPLEMENTASI DAN KODING**


Untuk melakukan klasifikasi emosi pada ulasan produk di e-commerce menggunakan model pralatih IndoBERT yang diimpor melalui Hugging Face Transformers. Implementasi ini menggunakan Google Colab dengan bahasa pemrograman Python.

**1. Persiapan data**

Langkah awal adalah mempersiapkan dan memuat file CSV berisi ulasan produk yang telah melalui tahap preprocessing. File ini akan di upload ke Google Collab menggunakan fungsi files.upload() dari pustaka google colab. Selain itu, file csv akan dibaca datanya dan mengatur pemanggilan tokenizer untuk model pelatihan


```python
#upload file yang berisi dataset
from google.colab import files
uploaded = files.upload()

import pandas as pd # library mengolah data CSV yang telah diupload
import numpy as np # library untuk melakukan operasi matriks
import torch # framework yang digunakan untuk model training IndoBERT

# membagi sebuah data dan evaluasi model matrik
from sklearn.model_selection import train_test_split
from sklearn.metrics import accuracy_score, precision_score, recall_score, f1_score

from transformers import (
    AutoTokenizer, # untuk melakukan pemanggilan tokenizer pada IndoBERT
    AutoModelForSequenceClassification, # untuk pemanggilan pada model yang digunakan
    # melatih model
    TrainingArguments,
    Trainer,
    BertTokenizer,
    BertForSequenceClassification
)

# membaca dataset yang telah diupload
df_ready = pd.read_csv('dataset_emosi_acak.csv')

```

**2. Pembagian data**


Selanjutnya melakukan tokenisasi dan split data. Pada tahapan ini. Data akan dibagi menjadi dua subset yaitu data validasi dan data pelatihan dengan masing-masing besaran 80: 20. Pemisahan ini dilakukan menggunakan train_test_split dari pustaka sklearn. Selain itu, data labelisasi akan diganti dari string menjadi angka agar bisa diproses oleh model. Model indoBERT memerlukan inputan dalam bentuk sebuah token sehingga dilakukan proses tokenizer yang mengubah teks ke dala token memggunakan tokenizer dari Transformer dan encoding hasil tokenisasi akan dikonversi ke format dataset Trainer dari Transformer dalam bentuk PyTorch (pustaka Torch).


```phyton
# menamai ulang untuk menyesuaikan model dan dataset
# menandai bahwa ulasan bersih dan labelisasi emosi sama dengan
# text dan label
df_ready = df_ready.rename(columns={
    'ulasan_bersih': 'text',
    'Labelisasi Emosi': 'label'
})

# Melabeli emosi dgn angka
label2id = {
    'senang': 0,
    'kecewa': 1,
    'sedih': 2,
    'marah': 3,
    'netral': 4
}
df_ready['label'] = df_ready['label'].map(label2id)

# melakukan pengahapusan pada data kosong
df_ready = df_ready.dropna(subset=['text', 'label'])
# memastikan data teks bersifat string
df_ready['text'] = df_ready['text'].astype(str)

# membagi data untuk di training dengan 80% training dan 20% validasi
train_texts, val_texts, train_labels, val_labels = train_test_split(
    df_ready['text'],
    df_ready['label'],
    test_size=0.2,
    random_state=42,
    stratify=df_ready['label']
)

# Tokenisasi dari model IndoBERT
tokenizer = AutoTokenizer.from_pretrained("indobenchmark/indobert-base-p1")
# memotong sebuah teks dan menambahkan token kosong
# untuk memiliki maximal dan panjang input yang sama
train_encodings = tokenizer(list(train_texts), truncation=True, padding=True, max_length=128)
val_encodings = tokenizer(list(val_texts), truncation=True, padding=True, max_length=128)

# membentuk kelas emosi
class EmotionDataset(torch.utils.data.Dataset):
  # fungsi untuk menyimpan tokenisasi dan label
    def __init__(self, encodings, labels):
        self.encodings = encodings
        self.labels = labels
  # fungsi untuk mengambil sampel data dan mengubah item dalam bentuk tensor
    def __getitem__(self, idx):
        item = {key: torch.tensor(val[idx]) for key, val in self.encodings.items()}
        item['labels'] = torch.tensor(self.labels[idx])
        return item
  # fungsi untuk memberikan jumlah data dalam dataset
    def __len__(self):
        return len(self.labels)

# bagian untuk membagi dataset training dan validasi
train_dataset = EmotionDataset(train_encodings, list(train_labels))
val_dataset = EmotionDataset(val_encodings, list(val_labels))

```


**3. Inisialisasi model dan training**


Model akan dimuat dan disesuaikan dengan 5 kategori atau labelisasi yang telah ditentukan sebelumnya dan diberikan parameter untuk menggunakan Training Arguments yang meliputi jumlah epoch , batch size, dan tempat penyimpanan data. Training data juga dilakukan melalui 5 epoch.

Untuk epoch yang diinginkan dapat disesuaikan, misalnya untuk uji coba pertama kali dan ingin mengetahui akurasi sebuah model dapat menggunakan satu kali epoch saja.

```python
# memanggil model IndoBERT untuk melakukan klasifikasi 5 labelisasi yang telah ditentukan
model = AutoModelForSequenceClassification.from_pretrained(
    "indobenchmark/indobert-base-p1",
    num_labels=5
)

# argumen training
training_args = TrainingArguments(
    output_dir='./model_checkpoints', # tempat untuk menyimpan model training
    num_train_epochs=5, # jumlah model akan melakukan training
    # jumlah data yang akan ditraining dalam 1 batch
    per_device_train_batch_size=16,
    per_device_eval_batch_size=64,
    logging_dir='./logs',
    logging_steps=50, # mencetak log setiap 50 langkah
    save_steps=500, # menyimpan model setiap sebanyak 500 langkah
    save_total_limit=3, # menyimpan 3 model terbaik
    do_eval=True, # evaluasi model selama training
    report_to='none' # untuk tidak mengaktifkan penggunaan WandB
)

```

**4. Evaluasi model**

Model akan terus dilatih menggunakan Trainer yang secara tidak langsung akan menangi pelatihan dan evaluasi. Pada tahap ini akan menghitung akurasi, precision, recall, dan F1-Score menggunakan compute_metrics dengan sklearn.

```python
# fungsi metrik evaluasi
def compute_metrics(eval_pred):
    logits, labels = eval_pred # mengambil nilai mtariks berdasarkan log dan label
    predictions = np.argmax(logits, axis=1) # memilih kelas yang memiliki nilai tertinggi
    return {
        'accuracy': accuracy_score(labels, predictions), # menghitung nilai akurasi
        'precision': precision_score(labels, predictions, average='weighted', zero_division=0), # menghitung nilai presisi
        'recall': recall_score(labels, predictions, average='weighted'), # menghitung nilai recall
        'f1': f1_score(labels, predictions, average='weighted') # menghitung kombinasi presisi dan recall
    }

# Trainer
trainer = Trainer(
    model=model,
    args=training_args,
    train_dataset=train_dataset,
    eval_dataset=val_dataset,
    compute_metrics=compute_metrics
)
```


**5. Pelatihan dan evaluasi akhir model**


Pelatihan model memanfaatkan Trainer dan setelah pelatihan model selesai dijalankan, hasilnya akan menunjukkan bahwa model memiliki akurasi, recall, precision, dan F-1 Score yang tinggi sehingga menandakan bahwa model IndoBERT mampu memahami emosi pada ulasan produk dengan baik. Evaluasi ini akan disimpan dan dapat digunakan kembali.


```python
# kode untuk menjalankan pelatihan model (melatih model)
trainer.train()

# untuk menyimpan hasil pelatihan model IndoBERT
model.save_pretrained("./model-indoBERT-emotion")
tokenizer.save_pretrained("./model-indoBERT-emotion")

import numpy as np
from sklearn.metrics import confusion_matrix, ConfusionMatrixDisplay, classification_report
import matplotlib.pyplot as plt
from sklearn.metrics import accuracy_score, f1_score, precision_score, recall_score

# untuk menghitung prediksi dari validation set
predictions = trainer.predict(val_dataset)
y_true = predictions.label_ids
y_pred = np.argmax(predictions.predictions, axis=1)

# list label emosi yang telah ditentukan dari awal
# harus memiliki urutan yang sama
label_list = ["senang", "kecewa", "sedih", "marah", "netral"]

# untuk menghitumh confusion matrix
cm = confusion_matrix(y_true, y_pred)
print("Confusion Matrix:")
print(cm)

# Tampilkan dalam bentuk gambar
disp = ConfusionMatrixDisplay(confusion_matrix=cm, display_labels=label_list)
disp.plot(cmap=plt.cm.Oranges)
plt.title("Confusion Matrix Model IndoBERT")
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()

# melakukan evaluasi model
eval_result = trainer.evaluate()
print(eval_result)

from sklearn.metrics import classification_report

report = classification_report(y_true, y_pred, target_names=label_list)
print("Classification Report:")
print(report)

```


**_PEMBAHASAN DAN RANGKUMAN_**


Setelah melewati tahapan awal dengan proses pengumpulan data dan _pre-processing_ untuk melakukan pemodelan menggunakan model IndoBERT. Data yang berupa ulasan-ulasan dikumpulkan dari berbagai produk di e-commerce Shopee yang diperoleh secara manual. Hasil data ulasan yang telah dikumpulkan merupakan data mentah yang memiliki berbagai noise seperti, emoji, tanda baca berlebihan, teks tidak bermakna, dan singkatan atau bahasa slang yang digunakan. Oleh karena itu, pada tahap _pre-processing_ dilakukan digunakan untuk memaksimalkan data agar bisa diproses oleh model berbasis IndoBERT. Setelah itu dilakukan analisis distribusi awal label emosi yang tersedia yaitu marah, sedih, kecewa, senang, dan netral. Pelatihan model ini dilakukan menggunakan model IndoBERT dengan menetapkan 5 label emosi yaitu senang, kecewa, marah, sedih, dan netral. Model ini memanfaatkan Trainer dari Hugging Face Transformers dengan melalui dua tahap epoch. Setiap epoch menggunakan konfigurasi batch_size \= 16 dan max_length \= 64\.


Selanjutnya mari kita bahas bagaimana performa model IndoBERT bekerja dengan memhami teks ulasan e-commerce.


Berdasarkan hasil training ketika menggunakan IndoBERT dalam 5 epoch, diketahui bawah nilai-nilai confusion matrixnya memberikan hasil yang sangat baik secara berturut-turut. Berikut adalah hasil dari menjalankan kode implementasi selama 5 epoch.


| Epoch | Accuracy | Precision | Recall | F1-Score |
| :---: | :------: | :-------: | :----: | :------: |
|   1   |  86,30%  |  86,41%   | 86,30% |  86,08%  |
|   2   |  88,26%  |  88,26%   | 88,26% |  89,21%  |
|   3   |  89,51%  |  89,49%   | 89,51% |  89,47%  |
|   4   |  89,90%  |  89,85%   | 89,90% |  89,85%  |
|   5   |  90,62%  |  90,62%   | 90,62% |  90,58%  |


Hasilnya sangat baik dan sangat sesuai bukan dengan ekspetasi bahwa model ini berkerja dengan akurat.


Berdasarkan tabel diatas, model ini sudah menunjukkan hasil yang sangat baik pada epoch pertama hingga epoch kelima dengan nilai akurasi sebesar 86,30% hingga nilai akurasi sebesar 90,62%. Hal ini menyatakan bahwa model IndoBERT mampu menangkap pola emosi dari ulasan produk dengan sangat baik meskipun baru melalui tahap pertama epoch. Setiap nilai epoch memiliki nilai akurasi yang semakin baik, bisa dilihat kenaikannya dari epoch pertama memiliki nilai akurasi sebesar 86,30%, epoch kedua 88,26%, nilai epoch ketiga sebesar 89,51%, nilai epoch keempat sebesar 89,51%, dan nilai epoch kelima sebesar 90,62%. Nilai akurasi meningkat sebesar 2,28% dari epoch pertama hingga epoch kelima. Selain itu, dapat dilihat juga dari nilai precision dan recall yang memiliki nilai cukup seimbang yang menyatakan bahwa model IndoBERT mampu memahami label kelas kategori emosi secara keseluruhan, tidak hanya pada satu kelas label saja.


Pada nilai recall mengalami peningkatan dari epoch pertama sebesar 86,30% sampai epoch kelima sebesar 90,62% yang mengartikan bahwa nilai recall mengalami peningkatan sebesar 4,32% sehingga model berhasil mengenali semua data positif yang memiliki nilai benar. Kemudian, nilai precision juga mengalami peningkatan dari epoch pertama sebesar 86,41% sampai epoch kelima sebesar 90,62% sehingga menunjukkan bahwa model dapat bekerja dengan baik dan mampu menentukan banyak yang benar dari semua prediksi kelas tertentu. Untuk nilai f1-score yang cukup naik dari nilai epoch pertama sebesar 86,08% sampai nilai epoch kelima sebesar 90,58% dan nilai yang cukup seimbang dengan nilai recall dan precision menunjukkan bawah model dapat menyeimbangkan nilai keduanya. Keseimbangan nilai recall dan precision membuktikan bahwa performa model tidak mengalami kelas yang terlalu mendominasi (mayoritas) sehingga model dapat membaca setiap emosi secara tepat.


Selain itu, terdapat juga data nilai akurasi, precision, recall, dan F1-Score pada setiap masing-masing emosi.


|         | Precision | Recall | F-1 Score |
| ------- | :-------: | :----: | :-------: |
| Senang  |    88%    |  84%   |    86%    |
| Kecewa  |    91%    |  85%   |    88%    |
| Sedih   |    99%    |  100%  |    99%    |
| Marah   |    95%    |  100%  |    97%    |
| Netral  |    81%    |  86%   |    83%    |
| Akurasi |    90%    |        |           |


Setelah kita memperhatikan nilai matriks pada setiap epoch, kita juga perlu mengerti bagaimana model memiliki nilai yang cukup baik pada setiap masing-masing kelas melalui nilai recall, precision, dan F-1 Score. Nilai rata-rata precision 90,8% artinya model mampu dalam menebak berapa banyak model yang benar. Sedangkan untuk nilai rata-rata recall 91% menunjukkan bahwa model mampu menemukan model yang sesuai dengan kategori kelas tersebut. Untuk nilai rata-rata F1-Score 90,6 didapatkan dari kemampuan model dalam menyeimbangkan antara prediksi dan recall. Meskipun pada kategori kelas emosi netral nilai F1-Score nya sedikit lebih rendah dibandingkan dengan emosi lainnya, nilai tersebut bisa saja disebabkan oleh emosi netral yang tidak memiliki kata kunci secara spesifik sehingga model akan lebih sedikit sulit untuk membandingkan dengan emosi lainnya. Secara keseluruhan, nilai akurasi pada setiap kategori kelas yaitu 90% yang menunjukkan model dapat menebak dengan benar dari semua data uji yang diberikan dengan akurasi yang cukup tinggi.


Dengan demikian, kita mengetahui model IndoBERT mampu melakukan klasifikasi emosi terhadap ulasan produk di e-commerce shopee menggunakan pustaka Transformers dari Hugging Face di Google Collab. Melalui lima tahap epoch sebelumnya, model sudah memberikan hasil performa yang sangat tinggi dengan nilai akurasi mencapai 90,62% dan F1-Score mencapai 90,58%. Oleh karena itu, Model IndoBERT terbukti sangat efektif kita gunakan dalam melakukan klasifikasi emosi ulasan produk di e-commerce Shopee untuk teks yang menggunakan bahasa Indonesia, terutama pada artikel ilmiah ini. Model sangat berpotensi untuk digunakan dalam analisis sentimen produk, klasifikasi emosi, mendeteksi emosi dan pemantauan opini secara mendalam.


**SIMPULAN**  


Berdasarkan hasil eksperimen yang telah kita lakukan, model IndoBERT cukup baik dalam melakukan klasifikasi emosi pada ulasan produk berbahasa Indonesia di platform e-commerce seperti Shopee. Berbagai tahapan proses yang dilakukan mencangkup tahapan preprocessing sampai pelatihan. Meskipun terdapat data yang tidak sepenuhnya seimbang, model tetap memberikan hasil yang optimal dengan performa yang luar biasa setelah melakukan pelatihan sebanyak lima epoch. Evaluasi model menunjukkan bahwa nilai akurasi mencapai 90,62%, precision 90,62%, recall 90,62%, dan F1-Score 90,58%. Dengan adanya nilai yang cukup seimbang pada precision dan recall kita mengetahui jika model tidak mendominasi pada salah satu kelas emosi tertentu saja. Berdasarkan pencapaian dari model tersebut, kita dapat menyimpulkan model IndoBERT ini sangat efektif untuk diterapkan dalam tugas klasifikasi emosi berbasis teks Bahasa Indonesia yang dapat digunakan dalam melakukan sistem analisis opini, baik dalam sentimen maupun emosi konsumen pada platform e-commerce Indonesia.


**UCAPAN TERIMA KASIH**  


Penulis ingin menyampaikan ucapan terima kasih kepada Bapak Gusti Ahmad Fanshuri Alfarisy, S.Kom., M.Kom. selaku dosen pengampu mata kuliah Deep Learning B yang telah memberikan arahan, dukungan, dan kesempatan untuk mengembangkan penelitian ini sebagai bagian dari tugas akhir perkuliahan.


**DAFTAR PUSTAKA**


Alfando, A., & Hayami, R. (2023). Klasifikasi teks berita berbahasa Indonesia menggunakan  
 machine learning dan deep learning: studi literatur. _JATI (Jurnal Mahasiswa_  
 _Teknik Informatika)_, 7(1), 681–686.

Bagus, A. T., & Fudholi, D. H. (2021). Klasifikasi emosi pada teks dengan menggunakan  
 metode deep learning. _Syntax Literate: Jurnal Ilmiah Indonesia_, 6 (Special  
 Issue 1), 547–553.

Fadilah, G. T., Muflikhah, L., & Perdana, R. S. (2025). Analisis Sentimen Produk Hijab Pada  
 E-Commerce Tokopedia Menggunakan Algoritma Support Vector Machine  
 dan IndoBERT Embedding. _Jurnal Pengembangan Teknologi Informasi dan_  
 _Ilmu Komputer_, _9_(2).

Hidayat, M. N., & Pramudita, R. (2024). Analisis Sentimen Terhadap Pembelajaran Secara Daring  
 Pasca Pandemi Covid-19 Menggunakan Metode IndoBERT. _INFORMATION MANAGEMENT FOR EDUCATORS AND PROFESSIONALS: Journal of Information Management_, _8_(2), 161-170.

Idris, I. S. K., Mustofa, Y. A., & Salihi, I. A. (2023). Analisis sentimen terhadap penggunaan  
 aplikasi Shopee menggunakan algoritma Support Vector Machine (SVM).  
 _Jambura Journal of Electrical and Electronics Engineering_, 5(1), 32–35.

Merdiansah, R., Siska, S., & Ridha, A. A. (2024). Analisis sentimen pengguna X Indonesia terkait  
 kendaraan listrik menggunakan IndoBERT. _Jurnal Ilmu Komputer dan Sistem Informasi (JIKOMSI)_, _7_(1), 221-228.

Nayla, A., Setianingsih, C., & Dirgantoro, B. (2023). Deteksi Hate Speech Pada Twitter Menggunakan  
 Algoritma BERT. _eProceedings of Engineering_, _10_(1).

Prabuningrat, G. S. W., Hostiadi, D. P., & Srinadi, N. L. P. (2024). Klasifikasi deteksi anomali  
 menggunakan metode machine learning. _Prosiding Seminar Hasil Penelitian_  
 _Informatika dan Komputer SPINTER_, 1(2), 845–850.

Sihombing, L. O., Hannie, H., & Dermawan, B. A. (2021). Sentimen Analisis Customer  
 Review Produk Shopee Indonesia Menggunakan Algoritma Naïve Bayes  
 Classifier. _Edumatic: Jurnal Pendidikan Informatika_, _5_(2), 233-242.

Vaswani, A., Shazeer, N., Parmar, N., Uszkoreit, J., Jones, L., Gomez, A. N., ... & Polosukhin, I.  
 (2017). Attention is all you need. _Advances in neural information processing systems_,  
 30\.

Wang, X., & Tong, Y. (2021). Application of an emotional classification model in e-commerce text  
 based on an improved transformer model. _PLOS ONE_, 16(3), e0247984. [https://doi.org/10.1371/journal.pone.0247984](https://doi.org/10.1371/journal.pone.0247984)

Hakim, I. (2025). _PERBANDINGAN MODEL INDOBERT DAN MODEL HYBRID PADA KLASIFIKASI_  
_EMOSI PERSEPSI KUALITAS LAYANAN APLIKASI DANA_ (Doctoral dissertation, UIN Ar-Raniry Banda Aceh).

Wirayudha, A., Murniyati, M., & Rosdiana, R. (2025). Analisis Sentimen Terhadap Ulasan Access  
By KAI Pada Google Play Store Menggunakan Metode Indobert. _Portal Riset dan Inovasi Sistem Perangkat Lunak_, 3(1), 9-20.

Septian, L., Aljauza, T., & Juliane, C. (2023). Analisis sentimen putusan Mahkamah Konstitusi  
terhadap batas usia capres dan cawapres menggunakan IndoBERT. _Indonesian Journal of Computer Science_, _12_(6), 4428–4439. [httsps://](https://ijcs.stmikindonesia.ac.id)[ijcs.stmikindonesia.ac.id](http://ijcs.stmikindonesia.ac.id)
