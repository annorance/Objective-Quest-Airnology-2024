# Objective-Quest-Airnology-2024
## Description
Di era digital saat ini, keamanan siber menjadi salah satu prioritas utama bagi perusahaan yang mengelola situs web dengan lalu lintas tinggi. Semakin meningkatnya jumlah pengguna dan perangkat yang terhubung ke internet, serta kompleksitas serangan siber yang terus berkembang, kebutuhan untuk memantau dan melindungi jaringan menjadi semakin krusial. Setiap hari, perusahaan-perusahaan besar harus menghadapi berbagai macam jenis traffic yang masuk dan keluar dari server mereka, mulai dari aktivitas pengguna yang sah hingga potensi ancaman seperti serangan dan aktivitas berbahaya lainnya.

Untuk menjaga integritas dan keamanan jaringan, tim keamanan siber harus secara efektif mengidentifikasi dan mengklasifikasikan jenis-jenis traffic yang ada dalam jaringan. Namun, dengan volume data yang sangat besar dan variasi yang tinggi dalam pola traffic, diperlukan sistem untuk mendeteksi dan menganalisis aktivitas mencurigakan secara real-time. Pembentukan model yang efektif akan membuat perusahaan dapat secara proaktif mendeteksi dan merespons potensi ancaman.

## Task
Peserta diharapkan untuk membangun dan mengembangkan model prediktif yang dapat mengklasifikasikan jenis traffic dalam jaringan. Model ini harus mampu menganalisis data traffic yang besar dan bervariasi, mengidentifikasi pola-pola yang mencurigakan, dan memprediksi kategori traffic secara akurat.

Jenis-jenis Traffic yang Harus Diprediksi:

- Background - Lalu lintas rutin atau latar belakang yang biasanya tidak menimbulkan ancaman.
- Benign - Traffic yang tidak menunjukkan tanda-tanda aktivitas berbahaya atau anomali.
- Probing - Aktivitas pemindaian atau penjelajahan untuk menemukan kerentanan atau target.
- Bruteforce - Upaya penyerangan dengan mencoba berbagai kombinasi kata sandi untuk mendapatkan akses.
- XMRIGCC CryptoMiner - Aktivitas terkait dengan penambangan cryptocurrency secara tersembunyi.
- Bruteforce-XML - Serangan brute force yang menargetkan aplikasi berbasis XML.

## Evaluation Metric
Pada kompetisi ini, performa model akan dievaluasi menggunakan nilai rata-rata metrik dari Balanced Accuracy Score dan Accuracy Score.
```
from sklearn.metrics import accuracy_score, balanced_accuracy_score

bal_acc = balanced_accuracy_score(solution, submission)
acc = accuracy_score(solution, submission)
score = (bal_acc+acc)/2
```
Nilai akhir 100% berdasarkan leaderboard dengan ketentuan kesesuaian antara akurasi yang didapatkan panitia saat validasi notebook dengan akurasi yang didapatkan peserta di Kaggle, yang akan ditentukan berdasarkan rata-rata terbobot antara nilai public dan private sebagai berikut:
```
nilai akhir = 30% public + 70% private
```

## Dataset
### Daftar File
train.csv - data log aktivitas dan traffic untuk training model.
test.csv - data log aktivitas dan traffic untuk dilakukan prediksi.
sample_submission.csv - contoh submisi.
### Features
- id - ID untuk setiap aliran jaringan
- origin_host - Alamat IP client
- origin_port - Nomor port yang digunakan oleh client
- response_host - Alamat IP server
- response_port - Nomor port yang digunakan oleh server
- flow_duration - Durasi aliran jaringan
- forward_packets_per_sec - Laju pengiriman paket dari client ke server per detik
- backward_packets_per_sec - Laju pengiriman paket dari server kembali ke client per detik
- flow_packets_per_sec - Laju keseluruhan paket yang dikirim per detik dalam seluruh aliran
- down_up_ratio - Rasio antara jumlah paket atau byte yang diunduh dan diunggah
- flow_FIN_flags - Jumlah bendera FIN yang menandakan akhir dari koneksi TCP.
- flow_SYN_flags - Jumlah bendera SYN yang digunakan untuk memulai koneksi TCP.
- flow_RST_flags - Jumlah bendera RST yang menandakan reset koneksi TCP.
- forward_PSH_flags - Jumlah bendera PSH yang menandakan data harus segera diproses oleh server.
- backward_PSH_flags - Jumlah bendera PSH yang menandakan data harus segera diproses oleh client.
- flow_ACK_flags - Jumlah bendera ACK yang digunakan untuk mengonfirmasi penerimaan paket.
- forward_URG_flags - Jumlah bendera URG yang menandakan data mendesak dari client.
- backward_URG_flags - Jumlah bendera URG yang menandakan data mendesak dari server.
- flow_CWR_flags - Jumlah bendera CWR yang menandakan pengurangan ukuran jendela kongesti.
- flow_ECE_flags - Jumlah bendera ECE yang menunjukkan adanya kemacetan jaringan.
- forward_pkts_payload - Ukuran rata-rata payload dalam paket dari client ke server
- backward_pkts_payload - Ukuran rata-rata payload dalam paket dari server ke client
- flow_pkts_payload - Ukuran rata-rata payload dalam seluruh aliran, mencakup paket dari client dan server
- forward_iat - Rata-rata waktu antar kedatangan (Inter Arrival Time, IAT) antara paket dari client ke server
- backward_iat - Rata-rata waktu antar kedatangan (IAT) antara paket dari server ke client
- flow_iat - Rata-rata waktu antar kedatangan (IAT) dalam seluruh aliran, mencakup paket dari client dan server
- payload_bytes_per_sec - Laju transfer byte payload per detik dalam aliran jaringan
- forward_subflow_packets - Jumlah paket dalam subflow dari client ke server
- backward_subflow_packets - Jumlah paket dalam subflow dari server ke client
- forward_subflow_bytes - Jumlah byte dalam subflow dari client ke server
- backward_subflow_bytes - Jumlah byte dalam subflow dari server ke client
- forward_bulk_bytes - Jumlah byte bulk dalam aliran dari client ke server
- backward_bulk_bytes - Jumlah byte bulk dalam aliran dari server ke client
- forward_bulk_packets - Jumlah paket bulk dalam aliran dari client ke server
- backward_bulk_packets - Jumlah paket bulk dalam aliran dari server ke client
- forward_bulk_rate - Laju lalu lintas bulk dalam aliran dari client ke server
- backward_bulk_rate - Laju lalu lintas bulk dalam aliran dari server ke client
- active - Rata-rata waktu aktif dalam aliran, menggambarkan periode ketika data sedang ditransmisikan
- idle - Rata-rata waktu idle dalam aliran, menggambarkan periode ketika tidak ada data yang ditransmisikan
- forward_initial_window_size - Ukuran Window Flow Control yang tersedia dari client ke server pada awal koneksi, menentukan jumlah data yang dapat dikirim tanpa memerlukan konfirmasi.
- backward_initial_window_size - Ukuran Window Flow Control yang tersedia dari server ke client pada awal koneksi, menentukan jumlah data yang dapat dikirim tanpa memerlukan konfirmasi.
- forward_last_window_size - Ukuran Window Flow Control dari client ke server pada akhir koneksi, menentukan jumlah data terakhir yang dapat dikirim sebelum koneksi ditutup.
### Target
traffic :
- Background
- Benign
- Probing
- Bruteforce
- XMRIGCC CryptoMinerBruteforce-XML

## Hasil dan Pembahasann
Untuk mengatasi permasalahan ketidakseimbangan kelas pada data, digunakan teknik BorderlineSMOTE, yaitu metode oversampling yang memfokuskan penambahan data sintetis pada area sekitar batas keputusan antar kelas. Model yang digunakan adalah Multilayer Perceptron Classifier (MLPClassifier) dengan arsitektur tiga lapis tersembunyi berjumlah 150, 100, dan 50 neuron. Model dikonfigurasi dengan fungsi aktivasi ReLU, optimisasi menggunakan Adam, nilai alpha sebesar 0.01 sebagai regularisasi ridge penalty, batch size sebesar 400, learning rate awal 0.001, dan maksimum iterasi sebanyak 5000. Toleransi konvergensi diatur pada 1e-6 untuk mencapai optimasi yang lebih stabil. 

Hasil evaluasi menunjukkan performa yang cukup baik, dengan public score sebesar 0.73250 dan private score sebesar 0.73547. Selisih skor yang relatif kecil antara data public dan private mengindikasikan bahwa model memiliki kemampuan generalisasi yang baik terhadap data baru. Selain itu, penerapan BorderlineSMOTE terbukti efektif dalam meningkatkan performa model pada dataset yang imbalanced.

## Citation 
Arkan Attaqy, Elzandi Irfan Zikra, GATOT, Lemuel Horas, miaw🐟, and Zys. Objective Quest Dataquest 2024. https://kaggle.com/competitions/objective-quest-dataquest, 2024. Kaggle.

## Competition Link
https://www.kaggle.com/competitions/objective-quest-dataquest
