# Klasifikasi Pneumonia pada Citra Chest X-Ray menggunakan CNN & Grad-CAM

[![Framework](https://img.shields.io/badge/framework-PyTorch-%23EE4C2C.svg)](https://pytorch.org/)
[![Status](https://img.shields.io/badge/project--status-in--progress-orange.svg)]()

Repositori ini merupakan wadah publikasi dan *showcase* untuk **Tugas Pengganti UAS Mata Kuliah Kecerdasan Buatan (Semester Genap 2025/2026)**.

Proyek ini berfokus pada pengembangan model *Deep Learning* untuk mendeteksi penyakit pneumonia melalui citra rontgen dada (Chest X-Ray), sekaligus mengimplementasikan metode Grad-CAM guna memberikan transparansi visual pada keputusan yang diambil oleh model.

---

## Ringkasan Proyek

* **Studi Kasus:** Klasifikasi Biner Citra Medis (NORMAL vs PNEUMONIA).
* **Dataset:** Chest X-Ray Images (Pneumonia) dari Kaggle - 11.712 citra (3.166 Normal, 8.546 Pneumonia)
* **Pendekatan AI:**
  * *Baseline Model:* Custom Convolutional Neural Network (CNN) yang dibangun dari awal (*from scratch*).
  * *Main Model:* Transfer Learning menggunakan arsitektur *pretrained* ResNet50 untuk optimasi akurasi.
* **Interpretabilitas:** Grad-CAM (*Gradient-weighted Class Activation Mapping*) untuk menghasilkan visualisasi *heatmap* area infeksi pada paru-paru.

---

## Alur Kerja & Metodologi

Secara garis besar, proyek ini dikembangkan melalui beberapa tahapan utama:

1. **Pra-pemrosesan Data (Preprocessing):** Proses pemisahan data (*data splitting*) secara *stratified*, penyesuaian dimensi citra (resizing), normalisasi nilai piksel, serta penerapan augmentasi gambar untuk memperkaya variasi data latih.
2. **Pengembangan Model Baseline:** Membangun arsitektur CNN kustom sederhana sebagai titik acuan eksperimen awal.
3. **Penerapan Transfer Learning:** Melakukan *fine-tuning* pada arsitektur ResNet50 yang telah dilatih sebelumnya pada dataset ImageNet.
4. **Visualisasi Grad-CAM:** Mengintegrasikan peta aktivasi kelas berbasis gradien untuk menyoroti area spasial yang menjadi fokus utama model saat melakukan klasifikasi.

---

## Status & Progres Pengembangan

Proyek ini sedang berada dalam fase pengembangan aktif dengan ringkasan status per tahapan sebagai berikut:

| Tahapan Pekerjaan                     | Deskripsi                                                              |   Status   |
| :------------------------------------ | :--------------------------------------------------------------------- | :---------: |
| **Eksplorasi & Preprocessing**  | Analisis distribusi dataset, pembagian data, dan pipeline augmentasi   |   Selesai   |
| **Model Baseline (Custom CNN)** | Implementasi arsitektur dasar dan eksekusi*training loop* awal       |   Selesai   |
| **Model Utama (ResNet50)**      | Integrasi arsitektur*Transfer Learning* dan strategi *fine-tuning* | Berlangsung |
| **Evaluasi Akhir & Metrik**     | Pengujian performa komparatif antar-model pada data uji (*Test Set*) |    Belum    |
| **Implementasi Grad-CAM**       | Penayangan visualisasi*heatmap* untuk interpretabilitas model        |    Belum    |
