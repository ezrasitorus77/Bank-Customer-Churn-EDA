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
