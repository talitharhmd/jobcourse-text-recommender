# Job Recommendation System using Word Embeddings

## 📝 Deskripsi Singkat
Proyek ini bertujuan untuk membangun sistem rekomendasi pekerjaan berdasarkan kemiripan deskripsi teks. Sistem ini dirancang untuk membantu pengguna menemukan pekerjaan lain yang relevan dengan posisi yang sedang dilihat atau diminati. Pendekatan yang digunakan berfokus pada representasi teks (word embeddings) dan pengukuran kemiripan semantik antar dokumen.

## 🔍 Pendekatan & Vektorisasi
Untuk merepresentasikan deskripsi pekerjaan, disini menggunakan dua vektorisasi:
- **Word2Vec**
- **FastText**
Word2Vec dan FastText dipilih karena kemampuannya menangkap konteks semantik kata. FastText memiliki keunggulan tambahan karena dapat mengenali kata baru dengan melihat struktur sub-kata (n-grams), yang sangat berguna untuk teks pekerjaan yang bervariasi.

Kemiripan antar deskripsi pekerjaan dihitung menggunakan dua metode:
- **Cosine Similarity**: menghitung kemiripan berdasarkan arah vektor rata-rata.
- **Word Mover’s Distance (WMD)**: mengukur seberapa besar “jarak” antar kata dari dua dokumen secara kontekstual.

## 📈 Hasil Rekomendasi
Beberapa hasil rekomendasi yang diperoleh antara lain:
- `data scientist financial conglomerates supervision` cocok dengan:
  - `data analyst data scientist nus office of data and intelligence`
  - `data scientist project intern trust and safety`
  - `data analyst`

- `data annotator` cocok dengan:
  - `data engineering leader`
  - `data analyst`
  - `research and data analyst`

| Metode            | Rata-Rata Skor |
| ----------------- | -------------- |
| Cosine + Word2Vec | 0.9993         |
| Cosine + FastText | 0.9993         |
| WMD + Word2Vec    | 1.0456         |
| WMD + FastText    | 1.0453         |

Dari tabel di atas, pendekatan **WMD + FastText** menunjukkan hasil terbaik. Meskipun selisihnya tidak besar, metode ini lebih akurat dalam menangkap konteks dan makna yang tidak selalu identik secara kata.

## 💡 Refleksi & Kendala
Beberapa kendala yang ditemui selama pengembangan:
- Proses **preprocessing perlu direvisi** karena adanya perubahan pada tahap translasi dan penghapusan stopword.
- **Word Mover’s Distance membutuhkan waktu komputasi yang cukup tinggi**, terutama saat jumlah data bertambah. Untuk mengatasi hal ini, pencarian dibatasi pada top-5 hasil terdekat dan parameter model dibuat seefisien mungkin.

Secara keseluruhan, pendekatan ini sudah cukup berhasil dalam memberikan rekomendasi pekerjaan yang relevan. Namun, sistem akan lebih optimal jika diuji pada dataset yang lebih besar dan beragam.
