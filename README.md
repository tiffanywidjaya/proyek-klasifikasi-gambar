# Proyek Klasifikasi Gambar: Sampah

## Deskripsi
Proyek ini bertujuan untuk membangun model klasifikasi gambar yang dapat mengenali **12 jenis sampah** menggunakan pendekatan *deep learning* dan *transfer learning* (MobileNetV2). Model ditargetkan dapat digunakan pada berbagai platform seperti web, mobile, atau aplikasi berbasis server.

## Dataset
- Dataset: [Garbage Classification by MostafaAbla (Kaggle)](https://www.kaggle.com/datasets/mostafaabla/garbage-classification)
- Jumlah kelas: **12**
- Folder lokal yang digunakan: `garbage_split/` dengan subfolder `train/`, `val/`, dan `test/`

Contoh label:
- `battery`, `biological`, `cardboard`, `clothes`, `green-glass`, `metal`, `paper`, `plastic`, `shoes`, `trash`, `white-glass`, `brown-glass`

---

## Arsitektur Model

Model menggunakan **MobileNetV2** sebagai backbone:

- `MobileNetV2 (include_top=False)`
- `GlobalAveragePooling2D`
- `Dropout(0.3)`
- `Dense(num_classes, activation='softmax')`

**Compiler:**
- Optimizer: `Adam(learning_rate=0.0001)`
- Loss: `categorical_crossentropy`
- Metrics: `accuracy`

**Callback:**
- `EarlyStopping`
- `ModelCheckpoint`

---

## Hasil Akurasi

| Dataset      | Accuracy | Loss    |
|--------------|----------|---------|
| Training     | 96.55%   | 0.1146  |
| Validation   | 95.53%   | 0.1358  |

Contoh hasil:
`Predicted class: plastic`

## Format Model yang Disimpan

| Format   | Lokasi           | Keterangan                           |
|----------|------------------|--------------------------------------|
| `.pb`    | `saved_model/`   | Format SavedModel untuk server       |
| `.h5`    | `best_model.h5`  | Format Keras standar                 |
| `.tflite`| `model.tflite`   | Untuk deployment ke Android          |
| `tfjs`   | `tfjs_model/`    | Untuk deployment ke web (JS)         |

---

## Inferensi
Model diuji terhadap 1 gambar acak dari dataset test.  
Contoh hasil prediksi: 
![image](https://github.com/user-attachments/assets/f0bafa0a-f70a-419f-843d-0b72a6dcd814)
`Predicted class: plastic`
