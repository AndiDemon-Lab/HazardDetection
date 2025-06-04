# Implementasi DETR (DEtection TRansformer) untuk Deteksi Objek

## Abstrak
Proyek ini merupakan implementasi model DETR (DEtection TRansformer) untuk tugas deteksi objek. DETR adalah arsitektur end-to-end yang menggabungkan Transformer dengan CNN untuk tugas deteksi objek, menghilangkan kebutuhan akan komponen khusus seperti non-maximum suppression (NMS) dan anchor generation. Proyek ini juga mengeksplorasi penggunaan dilation layer pada backbone ResNet untuk meningkatkan performa deteksi.

## Struktur Proyek
```
.
├── data/               # Direktori untuk dataset dan preprocessing
├── utils/             # Utilitas dan helper functions
├── config.py          # Konfigurasi model dan training
├── train.py           # Script training utama
├── train_r50.py       # Training dengan ResNet-50 backbone (tanpa dilation)
├── train_r50_1_4.py   # Training dengan ResNet-50 + DC Layer 1-4
├── train_r50_3_4.py   # Training dengan ResNet-50 + DC Layer 3-4
├── train_r50_4.py     # Training dengan ResNet-50 + DC Layer 4
├── train_r101.py      # Training dengan ResNet-101 backbone (tanpa dilation)
├── train_r101_1_4.py  # Training dengan ResNet-101 + DC Layer 1-4
├── train_r101_3_4.py  # Training dengan ResNet-101 + DC Layer 3-4
├── train_r101_4.py    # Training dengan ResNet-101 + DC Layer 4
├── testing.py         # Script untuk evaluasi model
└── requirements.txt   # Dependensi proyek
```

## Prasyarat
- Python 3.8+
- CUDA-compatible GPU (direkomendasikan)
- Dependensi yang tercantum dalam `requirements.txt`

## Instalasi
1. Clone repositori ini:
```bash
git clone [URL_REPOSITORI]
cd [NAMA_DIR]
```

2. Buat virtual environment (direkomendasikan):
```bash
python -m venv venv
source venv/bin/activate  # Linux/Mac
# atau
.\venv\Scripts\activate  # Windows
```

3. Install dependensi:
```bash
pip install -r requirements.txt
```

## Penggunaan

### Training Model
Proyek ini menyediakan beberapa variasi model dengan konfigurasi dilation layer yang berbeda:

#### ResNet-50 Backbone
- Model dasar (tanpa dilation):
```bash
python train_r50.py
```
- Model dengan DC Layer 1-4:
```bash
python train_r50_1_4.py
```
- Model dengan DC Layer 3-4:
```bash
python train_r50_3_4.py
```
- Model dengan DC Layer 4:
```bash
python train_r50_4.py
```

#### ResNet-101 Backbone
- Model dasar (tanpa dilation):
```bash
python train_r101.py
```
- Model dengan DC Layer 1-4:
```bash
python train_r101_1_4.py
```
- Model dengan DC Layer 3-4:
```bash
python train_r101_3_4.py
```
- Model dengan DC Layer 4:
```bash
python train_r101_4.py
```

### Evaluasi Model
Untuk mengevaluasi model yang telah dilatih:
```bash
python testing.py
```

## Konfigurasi
Parameter training dan model dapat dikonfigurasi dalam file `config.py`. Beberapa parameter penting:
- `BATCH_SIZE`: Ukuran batch untuk training
- `MAX_EPOCHS`: Jumlah epoch maksimum
- `LEARNING_RATE`: Learning rate untuk optimizer
- `NUM_WORKERS`: Jumlah worker untuk data loading

## Variasi Model
Proyek ini mengeksplorasi beberapa variasi model dengan konfigurasi dilation layer yang berbeda:

1. **ResNet-50 Backbone**:
   - Model dasar tanpa dilation layer
   - Model dengan DC Layer 1-4 (dilation pada layer 1 sampai 4)
   - Model dengan DC Layer 3-4 (dilation pada layer 3 dan 4)
   - Model dengan DC Layer 4 (dilation hanya pada layer 4)

2. **ResNet-101 Backbone**:
   - Model dasar tanpa dilation layer
   - Model dengan DC Layer 1-4 (dilation pada layer 1 sampai 4)
   - Model dengan DC Layer 3-4 (dilation pada layer 3 dan 4)
   - Model dengan DC Layer 4 (dilation hanya pada layer 4)

Penggunaan dilation layer bertujuan untuk meningkatkan receptive field model tanpa meningkatkan jumlah parameter, sehingga dapat menangkap konteks yang lebih luas dalam gambar.

## Hasil
Model ini menghasilkan output berupa bounding box dan class predictions untuk setiap objek dalam gambar. Metrik evaluasi yang digunakan:
- Mean Average Precision (mAP)
- Intersection over Union (IoU)
- Classification accuracy

## Referensi
1. Carion, N., Massa, F., Synnaeve, G., Usunier, N., Kirillov, A., & Zagoruyko, S. (2020). End-to-End Object Detection with Transformers. In European Conference on Computer Vision (pp. 213-229).
2. Yu, F., & Koltun, V. (2015). Multi-scale context aggregation by dilated convolutions. arXiv preprint arXiv:1511.07122.

## Lisensi
[]

## Kontak
[Hulwanul Azka Putra Pratama] - [hulwanulazkap@gmail.com] 
