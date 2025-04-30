# Proyek Klasifikasi Gambar: Bunga 

## Deskripsi Proyek
Proyek ini bertujuan untuk membangun model klasifikasi gambar menggunakan Convolutional Neural Network (CNN) untuk mengenali lima jenis bunga dari gambar: **daisy, dandelion, rose, sunflower**, dan **tulip**. Model ini dibangun dengan pendekatan deep learning menggunakan TensorFlow dan Keras, dan ditargetkan untuk dapat di-deploy ke berbagai platform seperti web, mobile, maupun server.

## Dataset
- Dataset berasal dari: [Kaggle Flowers Dataset by Imsparsh](https://www.kaggle.com/datasets/imsparsh/flowers-dataset)
- Jumlah total gambar: ± 4000+  
- Jumlah kelas: 5  
- Dataset sudah disertakan di folder `flowers/` untuk memastikan notebook dapat berjalan tanpa koneksi ke Google Drive.

## Arsitektur Model
Model dibangun menggunakan arsitektur `Sequential` dengan layer:
- `Conv2D` → untuk mengekstraksi fitur spasial
- `MaxPooling2D` → untuk mengurangi dimensi dan overfitting
- `Flatten` → untuk mengubah ke vektor
- `Dense` + `Dropout` → untuk klasifikasi akhir

Augmentasi digunakan untuk memperkaya data latih:
- Random flip
- Rotation
- Zoom

Callback:
- `EarlyStopping` untuk menghentikan training saat val_loss stagnan
- `ModelCheckpoint` untuk menyimpan model terbaik

## Target Akurasi
Hasil training terakhir menunjukkan:
- **Training Accuracy:** 81.38%
- **Validation Accuracy:** 71.84%

## Format Model yang Disimpan
| Format | Lokasi | Keterangan |
|--------|--------|------------|
| `.pb` (SavedModel) | `saved_model/` | Untuk deployment di server |
| `.tflite` | `tflite/model.tflite` | Untuk mobile |
| `.json + .bin` | `tfjs_model/` | Untuk browser (TensorFlow.js) |

## Inferensi
Model diuji terhadap 1 gambar acak dari dataset test.  
Contoh hasil prediksi:\n
![image](https://github.com/user-attachments/assets/9259ace6-3810-4fe2-99a4-7628769f11fc)\n
  `Predicted class: dandelion`

## Dependensi
tensorflow>=2.x matplotlib sklearn tensorflowjs
Semua dependensi sudah dicantumkan dalam `requirements.txt`.
