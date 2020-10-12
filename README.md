<h1> Disclaimer </h1>

- Sumber : https://www.kaggle.com/santoshd3/bank-customers

- Nama - nama bank maupun posisi yang digunakan adalah fiktif.

- Alur analisis menggunakan perspektif tim Data Science Bank Purwad untuk menciptakan suasana lingkungan kerja yang sesungguhnya.

- Tidak ada info yang komprehensif mengenai dataset, khususnya mengenai variabel *IsActiveMember*.

- Oleh karena tidak adanya info, maka diputuskan untuk:

    - Membangun konteks secara fiktif dengan mempertimbangkan kegunaannya sebagai bagian dari alur *story telling* kepada *user*.
    
    - Variabel **IsActiveMember** dipercaya bukan sebagai indikator nasabah dalam hal kepemilikan macam - macam rekening / tabungan. Hal ini dikarenakan baik nasabah yang aktif maupun tidak, sama - sama mempunyai produk bank lebih dari 0 (nilai unik masing - masing berkisar dari 1 - 4). Jadi, variabel ini diasumsikan sebagai tingkat keaktifan nasabah dalam mengikuti promo / program bank.
    
<h1> Business Problem </h1>

Bank Purwad baru berdiri sekitar 7 tahun silam di Indonesia. Namun, kiprahnya selama ini tidak bisa dipandang sebelah mata dalam ruang kompetisi bank swasta. Dalam 3 tahun terakhir saja, Bank Purwad sudah berhasil membuka cabang di Spanyol, Jerman, dan Perancis.

---------------------------------------------------------------------------------------------------------------------------

Selama ini kita berhasil menghimpun total 10.000 nasabah baru di luar negeri. Pencapaian ini melampaui prestasi Bank Hacktiv (6.300), Bank Algo (8.400), dan Bank DQLab (9.700). Kemenangan ini patut kita syukuri dan apresiasi. Penghargaan tertinggi sudah selayaknya kita berikan pada Tim Sales dan Tim Marketing karena kinerjanya yang sudah sangat optimal. Namun begitu, kami (Tim Data Science) menemukan sebuah kemunduran yang cukup mengkhawatirkan.

[![1.jpg](https://i.postimg.cc/rs4bhkYj/1.jpg)](https://postimg.cc/CnFm1W0n)

Kami menemukan bahwa dari total seluruh nasabah terdaftar, ada sekitar 20.4% nasabah yang akhirnya memutuskan untuk pindah. Angka ini tentu bukan angka yang kecil karena hampir menyentuh seperempat total nasabah. Berdasar info dari tim Relationship Officer (RO), 63% diantaranya pindah ke Bank Hacktiv, 29% pindah ke Bank Algo, dan 8% sisanya tidak diketahui. Permasalahan ini harus segera diselesaikan mengingat pemerintah pada pertengahan tahun depan akan menyerahkan insentif sebesar 100 Milyar Rupiah kepada 2 bank swasta dengan jumlah nasabah tertinggi. Jika manajemen nasabah seperti ini dibiarkan, kami khawatir jumlah nasabah akan terus tergerus hingga tahun depan.

<h1> Tujuan EDA </h1>

Tujuan dari laporan dan analisis ini tidak lain adalah untuk mendukung dan mendorong tim RO maupun *Customer Service* (CS) untuk memperbaiki sistem manajemen nasabah dan komunikasnya. Adapun bentuk dukungan tersebut secara teknis akan terwujud dalam kategorisasi nasabah yang memiliki kecenderungan untuk pindah. Nantinya, dengan 'peramalan' ini, diharapkan tim RO dapat dengan sigap menghubungi, memperbaiki hubungan, menawarkan kemudahan, ataupun mencari solusi terhadap permasalahan yang mungkin seorang nasabah hadapi terhadap Bank Purwad. Dengan begitu, angka penurunan jumlah nasabah bisa kita tekan atau bahkan hentikan setidaknya sampai pemerintah memberikan insentif. 

<h1> Melihat korelasi secara umum </h1>

Pada sub pembahasan ini, hanya dilakukan pengecekan secara umum. Pengecekan maupun penanganan variabel secara lebih spesifik dan komprehensif dilakukan pada sub pembahasan **Analisis Variabel**.

[![2.jpg](https://i.postimg.cc/MGdvTk59/2.jpg)](https://postimg.cc/6749jmDZ)

Sampai di sini, korelasi variabel numerik terkuat terhadap variabel ***Exited*** adalah ***Age***, ***Balance***, dan ***IsActiveMember***. Maka itu, kolom - kolom numerik yang tidak relevan diputuskan untuk dieliminasi.
Namun, sebelum melangkah lebih jauh, variabel - variabel tersebut harus dilihat distribusinya terlebih dahulu.

<h1> Analisis Variabel </h1>

**1. Hubungan antara umur dan kepindahan nasabah**

[![3.jpg](https://i.postimg.cc/VsDQVf6G/3.jpg)](https://postimg.cc/jCwFWryP)

'Age' memiliki distribusi 'right skewed'. Oleh karena itu, untuk menilai korelasinya harus menggunakan metode Spearman.

Nilai korelasi 'Age' dan 'Exited' :

[![4.jpg](https://i.postimg.cc/d1wp5pKc/4.jpg)](https://postimg.cc/nsS3zdz3)

Korelasi ini bernilai positif yang berarti semakin tua seorang nasabah, maka semakin besar kecenderungannya untuk keluar dari Bank Purwad.

Persebaran outliers :

[![5.jpg](https://i.postimg.cc/6QwMKZbd/5.jpg)](https://postimg.cc/NKJ67KcM)

Seperti halnya visualisasi distribusi data di atas, *boxplot* juga menggambarkan hal yang sama. Sentralitas data berada pada rentang umur sekitar 32 - 44 tahun. Pada sisi lain, *outliers* berada di atas sekitar 62 tahun. Ini menandakan bahwa nasabah kita yang umurnya cukup tua cenderung sedikit dibandingkan nasabah usia produktif. *Outliers* ini tidak akan dieliminasi karena akan berbicara banyak sebagai salah satu faktor determinan pindahnya nasabah.

[![6.jpg](https://i.postimg.cc/h49bDvxs/6.jpg)](https://postimg.cc/V5kb4YK0)

Setelah kami analisis, ternyata nasabah yang proporsinya paling banyak pindah adalah nasabah dari rentang umur 48 - 65 dengan puncaknya pada umur **54 - 59**. Korelasi positif antara kedua variabel ternyata **tidak sepenuhnya berjalan linear**. Dapat dilihat bahwa memasuki kelompok umur 60 - 65 terjadi penurunan yang cukup jauh. Hal ini **menandakan** bahwa tren korelasi positif berjalan konsisten untuk nasabah dalam rentang umur 18 - 59.

Sampai disini dapat disimpulkan bahwa semakin tua seorang nasabah, maka semakin besar kecenderungannya untuk keluar dari Bank Purwad. Namun, **harus diingat bahwa kesimpulan ini berlaku sampai batas usia nasabah 59 tahun**.

[![7.jpg](https://i.postimg.cc/d34hhbJs/7.jpg)](https://postimg.cc/tnnqfm1w)

Jerman adalah negara dengan jumlah nasabah yang pindah terbanyak. Namun begitu, persebaran nasabah antar negara terlihat tidak merata, terutama Spanyol yang memiliki perbedaan jumlah yang cukup jauh. Maka dari itu, harus digunakan proporsi agar kesimpulan yang diambil tidak bias.

[![8.jpg](https://i.postimg.cc/gkjJMBYh/8.jpg)](https://postimg.cc/CzyS57nM)

Negara asal seorang nasabah tidak berpengaruh pada keputusannya untuk pindah bank. Namun, jika dilihat lebih spesifik, jenis kelamin cukup berpengaruh. Jenis kelamin wanita konsisten berada di atas 53% atau lebih dari setengah dari total nasabah pada rentang umur 48 - 59 yang pindah. Adapun faktor yang melatarbelakanginya bisa jadi berasal dari hubungan nasabah dengan ROnya maupun pelayanan yang buruk dari tim CS. Berbeda dengan pria, wanita cenderung memiliki sifat yang lebih perasa. Umur yang tergolong tua juga diyakini turut memberi dampak tambahan pada sifat tersebut. Oleh sebab itu perlu ditinjau lebih lanjut kepada tim RO dan CS.

**2. Hubungan antara saldo dan kepindahan nasabah**

[![9.jpg](https://i.postimg.cc/2y6zKVfY/9.jpg)](https://postimg.cc/r0BXdymZ)

'Balance' memiliki kecenderungan distribusi 'bimodal'. Oleh karena itu, untuk menilai korelasinya harus menggunakan metode Spearman.

Nilai korelasi 'Balance' dan 'Exited' :

[![10.jpg](https://i.postimg.cc/bJCV1DWx/10.jpg)](https://postimg.cc/r049km8s)

Dapat dilihat bahwa persebaran data saldo tidak merata dan menumpuk di dua kelompok, dimana salah satunya adalah 0 USD. Nasabah yang masuk dalam kelompok ini cukup banyak dan patut untuk dicari tahu latar belakangnya. Ada dua kemungkinan untuk menjawabnya.

**Pertama**, besar kemungkinan saat tim Data Engineer menghimpun data posisi saldo nasabah secara kebetulan sedang 0 (mengingat kebijakan Bank Purwad yang membolehkan sisa saldo hingga 0). Asumsi pertama ini memiliki dua cabang asumsi lagi:
- Nasabah secara kebetulan menggunakan semua saldonya untuk berbelanja maupun keperluan lain hingga habis.
- Nasabah dengan sengaja menarik semua sisa uangnya di Bank Purwad karena ingin pindah ke bank lain.

**Kedua**, nasabah - nasabah tersebut adalah nasabah baru (berkaitan dengan kebijakan Bank Purwad yang memperbolehkan membuka rekening tanpa minimal dana mengendap).

Nasabah dengan saldo 0 tersebut tidak kami eliminasi ataupun manipulasi, mengingat ia bukanlah *missing values* dan tentunya mempunyai dampak terhadap perilaku nasabah yang pindah maupun tidak pindah.

[![11.jpg](https://i.postimg.cc/T3Jzpwd9/11.jpg)](https://postimg.cc/213ctCBb)

36,2% bukanlah angka yang kecil dan 'normal' menurut kami. Harus dicari tahu lebih dalam apakah ada hubungan antara nasabah dengan saldo 0 dengn keputusannya untuk pindah dari Bank Purwad. Selain itu, kita juga bisa melihat distribusi umur nasabah yang masuk dalam kelompok ini.

[![12.jpg](https://i.postimg.cc/tggMJNmq/12.jpg)](https://postimg.cc/XrT8Ddbm)

Grafik di atas mematahkan salah satu asumsi kami bahwa nasabah dengan saldo 0 USD adalah nasabah yang sengaja menarik semua uangnya dari Bank Purwad karena merasa tidak puas dan berencana untuk pindah bank. Ternyata sebaliknya, kelompok nasabah inilah yang lebih loyal. Maka dari itu, fokus analisis harus di pusatkan pada kelompok saldo di atas 0 USD.

[![13.jpg](https://i.postimg.cc/qR3Q6bcT/13.jpg)](https://postimg.cc/sQ35tJ06)

[![14.jpg](https://i.postimg.cc/4NBvyRCc/14.jpg)](https://postimg.cc/XpBB1hYN)

Baik kelompok nasabah yang memutuskan untuk pindah ataupun tidak, sama - sama memiliki konsentrasi saldo pada rentang sekitar 90.000 - 160.000. Namun, nasabah yang tidak pindah terlihat memiliki distribusi yang lebih sporadis.

Data ini tentunya mengejutkan kita semua. Terlihat bahwa dalam kelompok nasabah yang pindah terdapat beberapa nasabah prioritas kita, yang lebih tepatnya memiliki saldo di atas 200.000 USD. Memang tidak bisa serta merta disimpulkan jikalau semakin tinggi saldo seorang nasabah, maka kemungkinannya untuk pindah semakin besar. Namun, kami menemukan **korelasi tersebut dalam skala kecil jika seorang nasabah sudah masuk dalam kategori prioritas (saldo di atas 200.000 USD)**. Pada sisi lain, **jenis kelamin nampaknya tidak berpengaruh lagi jika saldo nasabah sudah sebesar itu**. Hal ini tentunya mengkhawatirkan mengingat nasabah prioritas adalah nasabah yang paling potensial untuk kita tawari kredit besar. Selain itu, dana minimal mengendap mereka juga jauh lebih tinggi dari nasabah biasa.

Ada beberapa hal yang mungkin menyebabkan kecewanya kelompok nasabah ini:
- Beberapa di antaranya adalah proses peminjaman / kredit yang cenderung rumit dan lama.
- Bunga yang kita tawarkan kalah bersaing dengan bank - bank daerah / swasta setempat, khususnya di Perancis dan Spanyol.

Presentase nasabah prioritas yang pindah per negara :

[![15.jpg](https://i.postimg.cc/bJpd1dkw/15.jpg)](https://postimg.cc/8FX1SpZ2)

Presentase nasabah biasa yang pindah per negara :

[![16.jpg](https://i.postimg.cc/yNzNzWfy/16.jpg)](https://postimg.cc/0zcvY51z)

Untuk kategori nasabah biasa, Jerman adalah negara yang presentase kepindahannya tertinggi. Sedangkan, untuk kelompok nasabah prioritas Spanyol adalah yang terbanyak.

**3. Hubungan antara keaktifan dan kepindahan nasabah**

[![17.jpg](https://i.postimg.cc/5Nbd1L10/17.jpg)](https://postimg.cc/pyG1J9mb)

Variabel terakhir ini nampaknya normal dan rasional jika dibandingkan dengan fakta di lapangan. Secara lumrah, nasabah yang tingkat keaktifannya lebih tinggi tentu saja tidak akan mudah untuk pindah. Ada beberapa hal yang mungkin berkaitan, salah satu yang terkuat adalah seperti keuntungan yang selama ini di dapat, bisa berupa undian / promo / keuntungan dari program kita. Sedangkan sebaliknya, nasabah yang tidak terlibat aktif dalam kegiatan dan program kita tentunya mempunyai 'ikatan' dan loyalitas yang lebih rendah. Dengan begitu tidak ada yang mengikatnya ketika ingin pindah dari Bank Purwad.

[![18.jpg](https://i.postimg.cc/fb315v7H/18.jpg)](https://postimg.cc/gwWM28TR)
[![19.jpg](https://i.postimg.cc/tCXf8btn/19.jpg)](https://postimg.cc/XXzQyTPn)

Baik dari kelompok nasabah biasa yang tidak aktif dan pindah maupun aktif dan pindah, ditemukan bahwa Jerman mendominasi proporsi dengan nilai yang **lebih dari setengah** dan **hampir setengah** dari total populasi. Bahkan, bisa dikatakan bahwa Jerman memiliki korelasi terkuat dengan variabel ini. Dengan kata lain dapat kami simpulkan bahwa variabel keaktifan nasabah **tidak berpengaruh di lapangan**.

**Perlu ditelusuri lebih lanjut** konteks sosial - budaya nasabah Jerman. Ada kemungkinan bahwa memang kultur nasabah kita disana yang tidak mudah puas dan mudah berpindah haluan. Nampaknya **perlu dibuat program khusus yang menargetkan nasabah di Jerman dengan mengadaptasi kebiasaan dan pola konsumsi setempat**.

<h1> Rekomendasi </h1>

1. Lakukan *training* dan *screening* terhadap para RO yang menangani nasabah **wanita berusia 48 - 59 tahun**, terlepas dari mana negara asalanya. Besar kemungkinan permasalahan ini akibat buruknya manajemen hubungan mereka dengan nasabah. Opsi lainnya adalah merekrut ataupun menukar RO terkait dengan yang sudah berpengalaman. Divisi lain yang perlu diperbaiki adalah Customer Service. Kami meyakini bahwa buruknya penanganan masalah dan keluhan lewat CS juga turut memberi dampak, mengingat nasabah dalam kelompok ini cenderung lebih perasa.
2. Segera lakukan pendekatan khusus bagi nasabah prioritas (memiliki saldo di atas 200.000 USD) di Perancis dan Spanyol. Dua negara ini adalah sumber utama nasabah prioritas kita. Namun, disarankan agar pengembangan dan perbaikan difokuskan ke Spanyol. Hal ini dikarenakan presentase kepindahannya adalah yang tertinggi. Kami sarankan agar tim analis - bisnis **mengkaji ulang tingkat bunga yang ditwarkan** karena kemungkinan besar terlalu tinggi jika dibandingkan dengan bank swasta / daerah lain di Spanyol dan Perancis. **Penyesuaian dan kompromi dalam memberi pinjaman** pada nasabah prioritas di dua negara ini juga patut menjadi pertimbangan. Pasalnya, nasabah prioritas cenderung memiliki tingkat kredit produktif yang lebih tinggi dibandingkan nasabah biasa.
3. Dalam konteks nasabah biasa (memiliki saldo di bawah 200.000 USD), tidak ditemukan pengaruh khusus dalam variabel data. Namun, yang menarik adalah bahwa Jerman menjadi lumbung terbesar nasabah yang pindah. Ada dua kemungkinan disini: **Pertama**, konteks sosial - budaya - ekonomi Jerman yang belum tim kita mengerti penuh (sehingga diperlukan studi perbandingan lebih lanjut untuk memahaminya) dan **kedua** ada permasalahan sistem internal di Bank Purwad cabang Jerman. Maka itu kami menawarkan **dua solusi**:
    - Segera pahami dan pelajari konteks nasabah di Jerman kemudian bentuk program / manajemen baru yang dikhususkan untuk pasar setempat.
    - Segera investigasi dan perbaiki permasalahan dalam tubuh organisasi Bank Purwad Jerman.
