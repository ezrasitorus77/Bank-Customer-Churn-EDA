<h1> Disclaimer </h1>

- Sumber : https://www.kaggle.com/santoshd3/bank-customers

- Tidak ada info yang komprehensif mengenai dataset, khususnya mengenai variabel *IsActiveMember*.

- Alur analisis menggunakan perspektif tim Data Science Bank Purwad (fiktif) untuk menciptakan suasana lingkungan kerja yang sesungguhnya.

- Oleh karena tidak adanya info, maka diputuskan untuk:

    - Membangun konteks secara fiktif dengan mempertimbangkan kegunaannya sebagai bagian dari alur *story telling* kepada *user*.
    
    - Variabel **IsActiveMember** dipercaya bukan sebagai indikator nasabah dalam hal kepemilikan macam - macam rekening / tabungan. Hal ini dikarenakan baik nasabah yang aktif maupun tidak, sama - sama mempunyai produk bank lebih dari 0 (nilai unik masing - masing berkisar dari 1 - 4). Jadi, variabel ini diasumsikan sebagai tingkat keaktifan nasabah dalam mengikuti promo / program bank.
    
<h1> Business Problem </h1>

Bank Purwad baru berdiri sekitar 7 tahun silam di Indonesia. Namun, kiprahnya selama ini tidak bisa dipandang sebelah mata dalam ruang kompetisi bank swasta. Dalam 3 tahun terakhir saja, Bank Purwad sudah berhasil membuka cabang di Spanyol, Jerman, dan Perancis.

---------------------------------------------------------------------------------------------------------------------------

Selama ini kita berhasil menghimpun total 10.000 nasabah baru di luar negeri. Pencapaian ini melampaui prestasi Bank Hacktiv (6.300), Bank Algo (8.400), dan Bank DQLab (9.700). Kemenangan ini patut kita syukuri dan apresiasi. Penghargaan tertinggi sudah selayaknya kita berikan pada Tim Sales dan Tim Marketing karena kinerjanya yang sudah sangat optimal. Namun begitu, kami (Tim Data Science) menemukan sebuah kemunduran yang cukup mengkhawatirkan.

[![1.jpg](https://i.postimg.cc/rs4bhkYj/1.jpg)](https://postimg.cc/CnFm1W0n)
