# Dokumentasi Pembuatan Visualisasi Data Bencana Provinsi Kalimantan Timur Tahun 2017-2021
Pada penelitian ini terdapat beberapa tahapan yang dilakukan dalam pembuatan visualisasi data bencana Provinsi Kalimantan Timur, yaitu :
1.	Membuat rancangan penelitian

Pada bagian ini dilakukan penentuan topik, rumusan masalah, tools yang akan digunakan, dan mengecek ketersediaan data. Topik yang diambil pada penelitian ini adalah terkait bencana dikarenakan minimnya visualisasi data bencana yang saat ini sebagian besar masih dalam bentuk data tabel. Provinsi Kalimantan Timur dipilih sebagai lokasi bencana dikarenakan sedang mendapat banyak perhatian terkait rencana kepindahan ibukota negara ke sana. Berdasarkan data yang ada peneliti merasa bahwa akan terdapat beberapa visualisasi yang cocok untuk menyajikan informasi tersebut. Beberapa visualisasi tersebut akan dijadikan satu dalam sebuah dashboard informasi.  Pembuatan visualisasi tersebut menggunakan software Tableau karena mudah digunakan, memiliki banyak referensi, dan dapat di upload secara publik. Selanjutnya dibuatlah diagram alur pengerjaan seperti pada gambar ‘Alur Penelitian.PNG’ yang terlampir.

![image](https://user-images.githubusercontent.com/107897580/174721803-a5fb8753-48f2-4c6d-9efe-3cf3bc4c0165.png)


2.	Pengumpulan Data

Data yang akan digunakan pada penelitian ini merupakan data sekunder yaitu data bencana yang terjadi di provinsi Kalimantan Timur sepanjang tahun 2017 sampai dengan 2021 dan data spasial Indonesia. Data bencana tersebut diambil dari https://dibi.bnpb.go.id/ yang merupakan portal resmi terkait data informasi bencana Indonesia yang dikelola oleh Bidang Pengelolaan Data dan Sistem Informasi (PDSI), Pusat Data Informasi dan Komunikasi Kebencanaan (Pusdatinkom), Badan Nasional Penanggulangan Bencana (BNPB) dalam format Excel. Adapun data spasial Indonesia diambil dari https://gadm.org/download_country_v3.html yang merupakan open source terkait data spasial berdasarkan negara di seluruh dunia dalam format Shapefile. 

3.	Preprocessing Data

Data bencana yang didapatkan terdiri atas beberapa atribut yaitu nama wilayah, jumlah bencana, jumlah korban berdasarkan jenis yaitu korban meninggal, hilang, terluka, menderita, dan mengungsi, serta jumlah kerusakan yang dibedakan berdasarkan jenis bangunan yaitu rumah, fasilitas pendidikan, fasilitas kesehatan, fasilitas peribadatan, fasilitas umum, perkantoran, jembatan, pabrik, dan kios. Namun, data data tersebut masih dalam bentuk file terpisah berdasarkan tahun kejadian dan jenis bencana, sehingga perlu dilakukan penggabungan terhadap data tersebut. Selain itu akan dilakukan penambahan dan penyederhanaan pada beberapa atribut agar sesuai dengan tujuan visualisasi pada penelitian ini. Sedangkan untuk data spasial Indonesia akan diambil data spasial Provinsi Kalimantan Timur saja.
Pertama akan dilakukan penggabungan terhadap data berdasarkan tahun dan jenis bencana. Selanjutnya ditambahkan atribut provinsi, tahun, dan bencana untuk memberikan informasi tambahan berupa lokasi dan waktu terjadinya bencana serta jenis bencana yang terjadi. Terakhir dilakukan penyederhanaan terhadap atribut korban berdasarkan jenis menjadi satu atribut yaitu atribut total korban. Hal tersebut dikarenakan data jumlah korban hanya terpusat pada jenis korban menderita dan mengungsi. Selain itu, penyederhanaan juga dilakukan pada atribut kerusakan berdasarkan jenis menjadi satu atribut total kerusakan dikarenakan jumlah kerusakan hanya terpusat pada kerusakan rumah. Data bencana yang telah selesai dilakukan preprocessing dapat dilihat pada 'Data Bencana_Clean.xlsx' yang terlampir.

Adapun data spasial Indonesia memiliki atribut yaitu Gid 0, Name 0, Gid 1, Name 1, Gid 2, Name 2, Type 2, Engtype 2, Cc 2, Hasc 2, dan Geometry. Penjelasan atribut tersebut yaitu Gid 0 berisi kode negara ‘IDN’; Name 0 berisi nama negara ‘Indonesia’; Gid 1 berisi kode angka dan huruf provinsi; Name 1 berisi nama provinsi; Gid 2 berisi kode angka dan huruf kabupaten/kota; Name 2 berisi nama kabupaten/kota; Type 2 berisi klasifikasi daerah sebagai kabupaten atau kota; Engtype 2 berisi klasifikasi daerah dalam bahasa inggris yaitu sebagai regency atau city; Cc 2 berisi kode angka kabupaten/kota; Hasc 2 berisi kode huruf kabupaten/kota; dan Geometry berisi bentuk daerah pada peta polygon atau multipolygon.

Selanjutnya akan dilakukan pengkoneksian kedua data yang ada (data bencana setelah diproses dan data spasial Indonesia) ke Tableau. Data bencana dan data spasial akan digabungkan secara inner berdasarkan atribut kab/kot, sehingga hanya ada data spasial untuk kabupaten/kota di Provinsi Kalimantan Timur saja.

4.	Visualisasi data di Tableau

Akan dibuat tiga visualisasi utama yang akhirnya akan digabung ke dalam dashboard, yaitu :
  
  a.	Visualisasi Bubble Chart
      
Visualisasi pertama yang akan dibuat adalah visualisasi dalam bentuk Bubble Chart. Visualisasi tersebut bertujuan untuk memperlihatkan kabupaten/kota mana di Provinsi Kalimantan Timur yang paling banyak mengalami bencana. Visualisasi ini dibentuk menggunakan dimension Kab/Kot dan measure Total Kejadian yang telah dijumlahkan menggunakan rumus SUM (total). Pada setiap bubble yang terbentuk ditambahkan label berupa nama dari masing masing kabupten/kota yang direpresentasikan. Semakin besar ukuran bubble mengindikasikan semakin banyak terjadi bencana di daerah yang direpresentasikan oleh bubble tersebut. Visualisasi yang terbentuk seperti pada gambar ‘Bubble Chart.JPG’ yang terlampir.

![image](https://user-images.githubusercontent.com/107897580/174722043-bf004d78-53c4-42a4-b295-fd93a26ae798.png)

  b.	Visualisasi Map
      
Visualisasi kedua yang akan dibuat adalah visualisasi dalam bentuk Map. Visualisasi ini digunakan untuk memperlihatkan sebaran jumlah terjadinya bencana disetiap kabupaten/kota beserta jumlah korban dan kerusakan yang terjadi. Dimension yang digunakan adalah Kab/Kot dan Bencana sedangkan measurenya adalah Total Kejadian, Total Kerusakan, dan Total Korban yang masing masing telah dijumlahkan menggunakan rumus SUM (total). Adapun data longitude dan latitude berasal dari measure Geometry. Pada setiap daerah pada peta diberikan label nama kabupaten/kota yang sesuai untuk memudahkan dalam mengenali daerahnya. Pada visualisasi disertakan keterangan warna yang mewakili banyaknya kejadian, semakin gelap maka semakin banyak bencana yang terjadi di daerah tersebut. Selain itu, dalam visualisasi ini juga terdapat filter berdasarkan jenis bencana yang terjadi untuk memudahkan pengguna dalam melihat daerah yang sering mengalami bencana tertentu. Visualisasi yang terbentuk seperti pada gambar ‘Map.JPG’ yang terlampir.

![image](https://user-images.githubusercontent.com/107897580/174722120-b6c49bc2-08b4-4e32-b9d3-51b2e356bb3e.png)

  c.	Visualisasi Line Chart
      
Visualisasi terakhir yang dibentuk adalah visualisasi dalam bentuk tiga buah Line Chart. Masing masing visualisasi tersebut bertujuan untuk menunjukkan perkembangan banyak kejadian bencana, banyak kerusakan, dan banyak korban mulai tahun 2017 sampai dengan tahun 2021. Pada Line Chart yang pertama yaitu terkait perkembangan banyak kejadian bencana dimension yang digunakan adalah Bencana dan measure Total Kejadian yang telah dijumlahkan menggunakan rumus SUM (total). Line Chart kedua tentang perkembangan banyak kerusakan akibat bencana menggunakan dimension Bencana dan measure Total Bangunan Rusak yang telah dijumlahkan menggunakan rumus SUM (total). Line Chart terakhir yaitu terkait perkembangan banyak korban akibat bencana menggunakan dimension Bencana dan measure Total Korban yang telah dijumlahkan menggunakan rumus SUM (total). Ketiga Line Chart tersebut digabungkan dengan memasukkan Tahun pada bagian Columns dan Total Kejadian, Total Bangunan Rusak, Total Korban yang telah dijumlahkan menggunakan rumus SUM (total) pada bagian Rows. Terdapat keterangan warna untuk memberikan informasi terkait bencana apa yang diwakili oleh garis tersebut. Selain itu, juga diberikan label pada setiap garis untuk memudahkan dalam mengetahui berapa banyak kejadian atau kerusakan atau korban yang ada. Visualisasi yang terbentuk seperti pada gambar ‘Line Chart.JPG’ yang terlampir.

![image](https://user-images.githubusercontent.com/107897580/174722377-bf9e46d6-6897-45fc-ae6c-7deb22dea6b7.png)
  
Setelah semua visualisasi tersebut telah selesai dibuat selanjutnya akan digabung dan ditata sedemikin rupa ke dalam dashboard untuk menyajikan kesemua informasi tersebut secara bersama. Ukuran dashboard yang digunakan adalah Desktop Size (wide: 1100; height: 975) karena dapat menampilkan visualisasi yang lebar dan cocok untuk menampilkan beberapa visualisasi yang telah dibuat. Pada dashboard ditambahkan beberapa hal untuk semakin memperjelas informasi yang akan disampaikan yaitu ditambahkan keterangan warna total kejadian dan warna jenis bencana, sehingga dapat memudahkan pengguna dalam memahami informasi yang ditampilkan oleh Tableau serta ditambahkan kotak informasi total kejadian, total kerusakan, dan total korban yang terjadi di seluruh provinsi Kalimantan Timur pada tahun 2017 sampai dengan 2021. Selain itu juga diberikan filter pada visualisasi Map sehingga jika salah satu daerah pada peta di klik akan memberikan visualisasi Line Chart sesuai daerah yang klik. Sedangkan Bubble Chart tidak akan  terpengaruh terhadap filter tersebut. Dashboard yang terbentuk seperti pada gambar ‘Dashboard.PNG’ yang terlampir.

![image](https://user-images.githubusercontent.com/107897580/174721280-f71034ea-3bbb-424a-a6e3-be0b77e4c18d.png)

Secara keseluruhan warna utama yang digunakan adalah hijau dan kuning. Hal tersebut karena peneliti merasa warna hijau dan kuning identic dengan alam dan secara tidak langsung juga bencana yang terjadi. Selain itu, sepemahaman peneliti penyajian warna hijau dan kuning secara bersama sama tidak akan menyulitkan bagi masyarakat yang buta warna untuk membedakan warnanya, sehingga dashboard informasi tersebut mudah dibaca dan dipahami oleh banyak orang. 

5.	Upload ke Tableau Public

Tahap terakhir pembuatan visualisasi ini adalah dengan menyimpan dashboard yang telah selesai dibuat ke dalam workbook “Informasi Data Bencana Provinsi Kalimantan Timur Tahun 2017-2021”. Selanjutnya workbook akan diupload ke Tableau Public melalui menu dalam Tableau dengan melakukan sign in terlebih dahulu. Setelah melakukan sign in data yang akan diupload disimpan terlebih dahulu yang selanjutnya akan di extract menjadi package workbook dan diunggah ke Tableau Public. Adapun hasil visualisasi yang telah diupload ke dalam Tableau Public dapat diakses melalui https://public.tableau.com/app/profile/kumala/viz/InformasiDataBencanaProvinsiKalimantanTimurTahun2017-2021/dashboardbencana#1

