# Study Case_OmicsLite_Week 3

## `Concept Workflow`
<img width="1341" height="475" alt="image" src="https://github.com/user-attachments/assets/a40e1c3b-9c56-46bb-bd59-5fdab9a98130" />

## Topic Week 3: Vaccine HIV
### Tools: GEO, GEO2R, R (R/Rstudio), GO (g:profiler), KEGG 
Proyek Project-Based Learning (PBL) ini merupakan bagian dari mata kuliah OmicsLite yang bertujuan untuk melakukan eksplorasi dan analisis berbasis omics terhadap satu artikel jurnal yang membahas kasus HIV pada pasien dengan kondisi DF, DHF, dan ND.

Analisis difokuskan pada interpretasi data omics, mekanisme biologis yang terlibat, serta perbedaan respons molekuler antar kondisi pasien, guna memahami keterkaitan antara infeksi HIV dan dinamika penyakit yang menyertainya.
### Catatan: DF = Dengue Fever; DHF = Dengue Hemorrhagic Fever; ND: Non-Dengue (normal)

## Langkah-Langkah Analisis GEO / GEO2R
### Menelaah jurnal
Langkah awal adalah meninjau jurnal yang akan digunakan sebagai dasar eksplorasi. Pada sesi ini, fokus pembahasan diarahkan pada vaksin HIV, termasuk konteks biologis dan tujuan analisis omics yang dilakukan dalam studi tersebut.

### Memeriksa aksesibilitas dataset di GEO2R
Selanjutnya, dilakukan pengecekan apakah dataset yang digunakan dapat diakses secara publik melalui GEO2R. Perlu diperhatikan bahwa tidak semua dataset bersifat publik, sehingga pada beberapa kasus analisis tidak dapat dijalankan menggunakan R.
Akses GEO2R melalui: https://www.ncbi.nlm.nih.gov/geo/geo2r/

### Pemeriksaan dataset
Dataset yang digunakan dalam analisis ini adalah GSE18090. Dataset tersebut diakses melalui halaman GEO dan dianalisis menggunakan fitur GEO2R.
Pengelompokan sampel pada GEO2R
Pada halaman analisis GEO2R, dilakukan pengaturan dan penamaan kelompok sampel.
Sampel DF dan DHF dikelompokkan sebagai “Patient”
Sampel ND dikelompokkan sebagai “Normal”

### Pemeriksaan menu analisis
Setelah pengelompokan selesai, diperiksa menu analysis options yang tersedia pada taskbar di bagian bawah halaman GEO2R.

### Pengaturan opsi analisis
Pada menu Options, secara umum pengaturan default telah terpilih. Namun, dilakukan penyesuaian dengan:
Memilih “Submitter supplied” pada kategori platform annotation, karena anotasi dari NCBI dapat mengalami perubahan dibandingkan anotasi asli dari pengunggah dataset.
Memilih “Yes” untuk menerapkan analisis menggunakan limma.
<img width="1764" height="541" alt="image" src="https://github.com/user-attachments/assets/031a9105-07a1-46ad-94bb-e399d739c3ff" />

### Menjalankan analisis data
Setelah seluruh pengaturan selesai, analisis dijalankan dengan menekan tombol “Reanalyze” pada halaman GEO2R.

### Visualisasi hasil analisis
Hasil analisis dapat divisualisasikan menggunakan beberapa metode, seperti heatmap plot dan Venn diagram, untuk mengevaluasi pola Differentially Expressed Genes (DEGs) antar kelompok sampel.

### Mengunduh hasil analisis
Tabel hasil analisis DEGs diunduh dengan memilih opsi “Download the table”. File hasil unduhan akan tersimpan dalam format .tsv (tab-separated values).

### Konversi dan pengolahan data lanjutan
Sebagai tantangan lanjutan, file .tsv dapat dikonversi menjadi .csv untuk memudahkan pengolahan data. Konversi dan analisis selanjutnya dapat dilakukan menggunakan Microsoft Excel, basis data SQL, atau pendekatan lain yang relevan.
Untuk penyaringan gen yang mengalami upregulasi dan downregulasi, dipilih masing-masing 20 gen berdasarkan nilai statistik yang diperoleh dari hasil GEO2R.

### Penyederhanaan simbol gen
Setelah diperoleh 20 gen upregulated dan 20 gen downregulated, kolom Symbol Gene diekstraksi. Pada beberapa entri, satu baris dapat mengandung lebih dari satu simbol gen yang dipisahkan oleh tanda “//”. Oleh karena itu, dilakukan pemisahan simbol gen sehingga setiap gen ditampilkan dalam bentuk satu baris (vertikal) untuk memudahkan analisis lanjutan.

## Langkah-Langkah Analisis GO (Gene Ontology)
### Mengakses platform analisis Gene Ontology
Analisis Gene Ontology dilakukan menggunakan platform daring seperti g:Profiler atau DAVID untuk mengevaluasi fungsi biologis gen yang telah teridentifikasi sebagai DEGs.
(Contoh: https://biit.cs.ut.ee/gprofiler/gost
)

### Memasukkan daftar gen
Daftar gen hasil penyaringan (20 gen upregulated dan 20 gen downregulated) yang telah diformat secara vertikal dimasukkan ke dalam kolom input pada platform GO.

### Menjalankan analisis GO
Setelah daftar gen dimasukkan, analisis dijalankan untuk memperoleh hasil pengayaan (enrichment analysis) berdasarkan kategori Gene Ontology.

### Interpretasi kategori Gene Ontology
Hasil analisis difokuskan pada tiga kategori utama:
GO Biological Process (GO-BP)
GO Molecular Function (GO-MF)
GO Cellular Component (GO-CC)
Pada kategori GO-BP, dicari proses biologis yang relevan dengan konteks penelitian, seperti:
Innate immune response
Inflammatory response
Response to virus
Apoptotic process

### Eksplorasi lanjutan dan penarikan kesimpulan
Analisis lanjutan dilakukan dengan membandingkan pola pengayaan antar proses biologis untuk menarik kesimpulan mengenai mekanisme molekuler dan respons imun yang terlibat, khususnya dalam konteks respon terhadap vaksin atau infeksi HIV.

## Langkah-Langkah KEGG Pathway
### Identifikasi jalur biologis hasil enrichment
Jalur biologis diidentifikasi berdasarkan hasil enrichment analysis sebelumnya, khususnya dari Gene Ontology (GO), untuk menentukan pathway yang relevan dengan respons imun dan infeksi virus.

### Akses KEGG Mapper
Analisis pathway dilakukan menggunakan KEGG Mapper, dengan memilih organisme Homo sapiens sebagai basis pemetaan gen.
(https://www.genome.jp/kegg/mapper/search.html
)

### Pemetaan DEGs ke dalam pathway KEGG
Daftar Differentially Expressed Genes (DEGs) dimasukkan ke KEGG Mapper secara terpisah berdasarkan arah regulasinya:
Gen downregulated dianalisis terlebih dahulu
Gen upregulated dianalisis pada tahap berikutnya
Pemisahan ini bertujuan untuk membedakan kontribusi gen yang mengalami penurunan dan peningkatan ekspresi terhadap jalur biologis tertentu.

### Analisis dan integrasi hasil
Output KEGG dianalisis dengan memperhatikan jumlah gen yang terpetakan pada masing-masing jalur, misalnya:
Toll-like receptor signaling pathway – 5 gen terpetakan
Cytokine–cytokine receptor interaction – 7 gen terpetakan
Apoptosis – 3 gen terpetakan

Hasil ini kemudian dikombinasikan dengan temuan GO, terutama pada kategori Biological Process, untuk memperkuat interpretasi mengenai aktivasi respons imun bawaan, sinyal inflamasi, dan mekanisme kematian sel dalam konteks respons terhadap infeksi atau vaksin HIV.

## Langkah-Langkah Interpretasi
### Visualisasi hasil analisis GEO2R
Hasil analisis dari GEO2R divisualisasikan menggunakan R/RStudio, seperti volcano plot, heatmap, atau grafik ekspresi gen, untuk menunjukkan perbedaan pola ekspresi gen antara kelompok Patient (DF dan DHF) dan Normal (ND).

### Penyajian hasil Gene Ontology (GO)
Daftar hasil pengayaan Gene Ontology disajikan dalam bentuk visualisasi atau tabel terstruktur yang mencakup:
GO Biological Process (GO-BP)
GO Molecular Function (GO-MF)
GO Cellular Component (GO-CC)
Penyajian ini bertujuan untuk menegaskan proses biologis, fungsi molekuler, dan lokasi seluler yang dominan pada gen-gen terdiferensiasi.

### Visualisasi jalur biologis (pathway analysis)
Hasil analisis jalur biologis dari KEGG divisualisasikan untuk menunjukkan keterlibatan gen pada jalur utama, seperti Toll-like receptor signaling, cytokine–cytokine receptor interaction, dan apoptosis, sehingga hubungan antar gen dan jalur biologis dapat diamati secara sistematis.

### Penarikan kesimpulan berbasis visualisasi data
Kesimpulan disusun dengan mengintegrasikan seluruh visualisasi data (GEO2R, GO, dan KEGG) untuk menjelaskan keterkaitan antara perubahan ekspresi gen, proses biologis, dan jalur sinyal yang terlibat. Pendekatan ini memungkinkan interpretasi yang lebih komprehensif mengenai mekanisme respons imun dan inflamasi yang relevan dalam konteks infeksi atau vaksin HIV.

Kamu tinggal eksplorasi dan pakai analisis mu dalam PBL OmicsLite
