# Diverse-Indonesia-ASR
Fine-tuned Automatic Speech Recognition for Bahasa Indonesia that is good for informals, slangs, accents, and code switching and mixing.

# Latar Belakang  
Teknologi Pengenalan Ucapan Otomatis (ASR) adalah teknologi yang mengubah ucapan dari audio menjadi teks yang dapat dibaca. Bentuk awal ASR adalah mengenali angka dari seorang pembicara tunggal, yang kemudian berkembang untuk memahami beberapa vokal dan konsonan, dan akhirnya kata-kata[1] (Juang et al. 2005). Secara teknis, penggunaan awalnya adalah untuk subtitle, dan hingga saat ini hal itu masih relevan untuk banyak aplikasi, seperti untuk orang dengan gangguan pendengaran, pembelajar bahasa, atau bagi mereka yang ingin memahami melalui kebisingan atau saat suara dimatikan.  

Banyak perusahaan dan perangkat lunak yang memanfaatkan ASR untuk aksesibilitas (menjangkau lebih banyak audiens, atau untuk kenyamanan)[2] (Taubenheim, 2022). Misalnya, di YouTube, ASR digunakan sebagai cara bagi pengguna untuk mencari video menggunakan suara (tombol mikrofon di samping kotak pencarian) atau untuk menghasilkan teks terjemahan untuk video. Di beberapa perangkat lunak untuk rapat, seperti Zoom atau Microsoft Teams, ASR digunakan untuk menampilkan teks terjemahan suara secara real-time.  

Namun, baik aplikasi maupun ASR secara keseluruhan sebagian besar dikembangkan di Barat, khususnya Amerika Serikat, dan difokuskan terutama untuk bahasa Inggris. Oleh karena itu, ASR bekerja paling baik untuk bahasa Inggris dengan akurasi yang tinggi daripada Bahasa Indonesia. Ini berarti siapa pun yang ingin menggunakan ASR untuk Bahasa Indonesia perlu menggunakan bahasa formal dan suara yang jelas tanpa gangguan atau jarak yang jauh (bahasa informal bisa tetapi harus yang paling terkenal).  

Meskipun mendapatkan suara yang jelas mungkin dapat diperbaiki secara langsung dalam kehidupan nyata, kamus katanya itu menjadi masalah yang kompleks, karena di Indonesia hal ini tidak hanya berkaitan dengan aksen atau kata-kata informal, tetapi paling terutama yaitu campuran dan pengalihan kode, yaitu perilaku orang untuk menyisipkan bahasa lain dalam percakapan Bahasa Indonesia, terutama Bahasa Daerah seperti Jawa, Sunda, atau Batak Toba, dan lain-lainnya, atau bahkan bahasa Inggris jika kata tersebut tidak dikenal secara umum di Indonesia.

| **Konten**                          | **Contoh Kalimat/Percakapan**                                                                                                                                                                                                                                                                                               |
|------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Formal                             | Maaf saya batalkan dulu untuk ikut berkumpul, tadi saya sudah dalam perjalanan, tetapi Ibu beri kabar dan mengatakan, 'tidak perlu pergi, teman-teman saya sudah datang ke sini terlebih dahulu.' Dan karena itu, saya akan tetap di rumah, sudah ada tamu                                                               |
| Formal, Informal                   | Maaf aku batalkan dulu untuk ikut berkumpul, tadi gua udah dalem perjalanan, tapi Ibu gua kabarin dan bilang, 'ga usah jadi pergi, temen-temen aku sudah dateng dari dulu.' Makanya aku balik lagi ke rumah, udah ada tamu                                                                                                 |
| Formal, Informal, Alih Kode       | Maaf gua batalkan dulu untuk ikut berkumpul, tadi gua udah dalem perjalanan, tapi Ibu gua kabarin dan bilang, 'ga usah jadi pergi, temen-temen aku sudah dateng dari dulu.' Makanya gua balik lagi ke rumah, soalnya udah ada tamu                                                                                        |
| Formal, Informal, Campur Kode     | Maaf gua cancel dulu untuk gatheringnya, tadi gua udah dalem perjalanan, tapi Ibu gua kabarin dan bilang, 'ga usah jadi pergi, temen-temen aku sudah dateng dari dulu.' So I’m going back home, udah ada guest                                                                                                            |
| Formal, Informal, Alih Kode, Campur Kode | Eh gua skip dulu ya nongkrongnya, tadi udah di jalan sih tapi si mamah ngasih kabar katanya ‘teu jadi indit, batur geus kadieu heula’ Jadi ya udahlah, I’m going back home, rumah penuh                                                                                             |

Penelitian ini bertujuan untuk menunjukkan cara meningkatkan kamus kata dan akurasi untuk percakapan atau pidato di Indonesia dengan memasukkan data kustom (audio yang belum pernah diinterpretasikan sebelumnya) ke dalam model ASR (Whisper dari OpenAI) dan kemudian melakukan fine-tuning pada model tersebut. Hasil yang diharapkan adalah model dapat memahami ucapan yang mengandung kata-kata baru, yang sebelumnya tidak dapat dilakukannya.  

# Rumusan Masalah
a. Bagaimana membuat model mengenali kalimat yang tidak dipahaminya?  
b. Bagaimana kinerja model yang baru disempurnakan ini, terutama dibanding model yang belum disempurnakan?  
c. Tantangan apa yang muncul selama penelitian ini?

# Batasan Masalah
* Model yang digunakan adalah Whisper  
* Gunakan Google Colab atau Jupyter secara lokal, tergantung pada batasan saat itu  
* Teori yang digunakan adalah Automatic Speech Recognition, Artificial Intelligence, Deep Learning, dan Natural Language Processing  
* Kamus barunya akan dibatasi pada beberapa kata informal dalam Bahasa Indonesia, beberapa kata dalam Bahasa Jawa, beberapa kata dalam Bahasa Inggris (yang kemungkinan besar akan paling sering digunakan), dan beberapa kata dalam Bahasa Batak Toba.  
* Ini lebih difokuskan pada model ASR, daripada aplikasi front-end yang lengkap  
* Evaluasi kinerja dengan Word Error Rate (WER) dan Sentence Error Rate (SER)  
* Penguji yang terlibat meliputi keluarga penulis, beberapa mahasiswa Universitas Pelita Harapan, dan beberapa audio dari video Youtube.  

# Tujuan Penelitian
* Untuk mengoptimalkan model ASR agar mampu mengenali kata-kata informal, aksen baru, dan kalimat yang mengandung code-switch (kombinasi Bahasa Indonesia yang mengandung unsur formal dan informal, serta bahasa lain seperti Bahasa Jawa, Batak Toba, atau Inggris, dalam satu kalimat) yang sulit dipahami oleh model standar.  
* Untuk mengevaluasi kinerja model yang telah disesuaikan menggunakan metrik WER dan SER, dan membandingkannya dengan model asli serta layanan ASR komersial seperti YouTube, Microsoft Teams, dan Live Transcribe.  
* Untuk mendokumentasikan metodologi secara jelas dan mudah diakses, sehingga penelitian ini dapat dipahami dan direproduksi dengan mudah oleh berbagai pihak, mulai dari penggemar hingga pengembang startup dan tim tingkat perusahaan.  
