# Analisis Dampak AI terhadap Pelajar

## Daftar Isi
- [Tentang Proyek](#tentang-proyek)
- [Struktur Dataset](#struktur-dataset)
- [Alur Kerja (Workflow)](#alur-kerja-workflow)
- [Kesimpulan](#kesimpulan)

## Tentang Proyek

Proyek ini menganalisis hubungan antara penggunaan kecerdasan buatan (*Artificial Intelligence* atau AI) dan hasil akademik pelajar. Saya memilih dataset ini karena ingin mengetahui bagaimana penggunaan AI berkaitan dengan performa akademik, khususnya perubahan IPK sebelum dan setelah semester.

Analisis dilakukan menggunakan Python dalam Jupyter Notebook. Proyek mencakup pemeriksaan dan prapemrosesan data, analisis data eksploratif (*Exploratory Data Analysis/EDA*), serta model regresi linear untuk memprediksi IPK setelah semester berdasarkan sejumlah fitur akademik dan penggunaan AI.

> **Catatan:** Analisis korelasi dan prediksi pada dataset ini tidak dengan sendirinya membuktikan hubungan sebab-akibat antara penggunaan AI dan perubahan hasil akademik.

## Struktur Dataset

Dataset yang digunakan bernama `ai_student_impact_dataset (1).csv`. Notebook memuat data tersebut sebagai tabel menggunakan `pandas`.

Berikut kolom numerik yang teridentifikasi dalam notebook:

| Kolom | Keterangan |
|---|---|
| `Student_ID` | Identitas pelajar pada dataset |
| `Pre_Semester_GPA` | IPK sebelum semester |
| `Weekly_GenAI_Hours` | Jumlah jam penggunaan AI generatif per minggu |
| `Tool_Diversity` | Keragaman alat AI yang digunakan |
| `Traditional_Study_Hours` | Jumlah jam belajar konvensional |
| `Perceived_AI_Dependency` | Tingkat ketergantungan pada AI yang dirasakan |
| `Anxiety_Level_During_Exams` | Tingkat kecemasan saat ujian |
| `Post_Semester_GPA` | IPK setelah semester |
| `Skill_Retention_Score` | Skor retensi atau daya ingat keterampilan |

Dataset juga dapat memiliki kolom kategoris atau boolean. Notebook memeriksa tipe data dan nilai yang hilang, lalu menyesuaikan tipe data yang relevan. Penjelasan di atas mengikuti nama kolom yang digunakan dalam dataset; makna rinci dan skala pengukuran setiap kolom sebaiknya merujuk pada dokumentasi sumber dataset.

### Fitur dan Target Model

Model regresi linear menggunakan fitur berikut:

- `Pre_Semester_GPA`
- `Weekly_GenAI_Hours`
- `Traditional_Study_Hours`
- `Anxiety_Level_During_Exams`

Variabel target yang diprediksi adalah `Post_Semester_GPA`.

## Alur Kerja (Workflow)

1. **Memuat dataset**  
   Menemukan file CSV, membaca dataset dengan `pandas`, dan melihat ukuran serta beberapa baris awal data.

2. **Pembersihan dan prapemrosesan data**  
   Memeriksa nilai yang hilang, tipe data, dan konsistensi data. Kolom boolean atau kolom lain disesuaikan ke tipe data yang sesuai bila diperlukan.

3. **Analisis data eksploratif (EDA)**  
   Mengeksplorasi distribusi data dan hubungan antarkolom melalui ringkasan numerik serta visualisasi. Analisis numerik diterapkan pada kolom numerik.

4. **Menentukan fitur dan target**  
   Memilih fitur akademik dan penggunaan AI yang akan menjadi masukan model, serta menetapkan `Post_Semester_GPA` sebagai target.

5. **Membagi data**  
   Memisahkan data menjadi data latih dan data uji dengan `train_test_split`, menggunakan ukuran data uji sebesar 20% dan `random_state=42`.

6. **Melatih model**  
   Membuat model Decision Tree dan Random Forest, melatih menggunakan data latih.

7. **Membuat prediksi**  
   Menggunakan model untuk memprediksi IPK setelah semester pada data uji.

8. **Mengevaluasi model**  
   Menghitung **RMSE** (*Root Mean Squared Error*) dan **R²** untuk menilai kesalahan prediksi serta kemampuan model menjelaskan variasi target. Notebook juga menampilkan grafik perbandingan nilai prediksi dengan nilai sebenarnya.

## Kesimpulan

Saya menggunakan dataset ini karena ingin mengetahui hubungan antara penggunaan AI dan hasil akademik pelajar. Melalui eksplorasi data dan model regresi linear, saya dapat meninjau pola pada data serta menguji apakah beberapa faktor akademik dan penggunaan AI berkaitan dengan IPK setelah semester.

Hasilnya perlu ditafsirkan secara hati-hati. Model prediksi menunjukkan pola berdasarkan data yang tersedia, bukan bukti bahwa AI secara langsung menyebabkan kenaikan atau penurunan prestasi pelajar. Kesimpulan yang lebih kuat memerlukan pemeriksaan kualitas dataset, konteks pengumpulan data, serta faktor lain yang mungkin memengaruhi hasil akademik.
