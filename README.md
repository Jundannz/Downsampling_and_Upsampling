# Tugas 1 PCD: Downsampling dan Rekonstruksi Citra

Eksperimen uniform spatial downsampling (sampai skala ekstrem 2x2) dan upsampling manual untuk mata kuliah Pengolahan Citra Digital.

## Struktur folder

```
.
├── images/
│   ├── armadillo-0018.jpg
│   ├── kangaroo-0008.jpg
│   └── polar_bear-0010.jpg
├── PCD_Assignment01.ipynb
├── Laporan_PCD_Sampling_Rekonstruksi.pdf
└── README.md
```

`images/` berisi tiga data sekunder yang dipakai sebagai input. Notebook berisi seluruh kode eksperimen, dan laporan PDF berisi hasil serta analisisnya.

## Isi eksperimen

Semua citra input diproses lewat `preprocess_image`: diubah ke grayscale, lalu di-center crop jadi 256x256 piksel (kalau ukuran aslinya kurang dari 256, di-resize dulu secara proporsional pakai interpolasi cubic).

Dua eksperimen utama dijalankan:

1. **Downsampling ekstrem**, citra diperkecil bertahap dari 256x256 sampai 2x2 piksel, memakai tiga cara pooling per blok: max, average, dan median.
2. **Rekonstruksi upsampling**, citra hasil downsampling di ukuran 64x64 dikembalikan lagi ke 256x256 memakai tiga metode interpolasi manual: nearest neighbor, bilinear, dan bicubic (bobot tetangga 0,7 dan 0,3).

Catatan cakupan pengujian: rangkaian downsampling skala ekstrem (128 sampai 2x2, tiga mode) hanya dijalankan pada `polar_bear-0010.jpg`. Untuk `kangaroo-0008.jpg` dan `armadillo-0018.jpg`, pengujian hanya sampai downsampling ke 64x64 dengan average pooling, lalu direkonstruksi dengan ketiga metode upsampling. Detail dan alasan pembagian ini ada di laporan.

Rincian lengkap desain eksperimen, hasil, dan analisis (termasuk nilai piksel aktual di tiap mode) ada di `Laporan_PCD_Sampling_Rekonstruksi.pdf`.

## Menjalankan notebook

Notebook ditulis untuk Google Colab dan memakai Google Drive sebagai sumber citra (lihat sel `drive.mount` dan `DRIVE_IMG_DIR`). Untuk menjalankan di luar Colab, ganti bagian mount drive dan `DRIVE_IMG_DIR` dengan path lokal ke folder `images/`.

Dependencies:

```
opencv-python
numpy
pandas
matplotlib
```

## Penulis

Jundan Saiful Haq
NIM 25/560768/PA/23633
