Nama: Sabrina Aviana Dewi <br>
NPM: 2206030520
<h1> Tutorial 8 </h1>
<h2> Publisher </h2>
a. How many data your publlsher program will send to the message broker in one run?

Publisher akan mengirimkan 5 data ke message broker dalam satu kali jalan. Setiap pemanggilan `_ = p.publish_event(...)` mengirimkan satu data. Karena ada 5 pemanggilan tersebut, maka akan ada 5 data yang dikirimkan.
b. The url of: “amqp://guest:guest@localhost:5672” is the same as in the subscriber program, what does it mean?

URL "amqp://guest:guest@localhost:5672" yang sama pada program Publisher dan program Subscriber berarti bahwa keduanya menggunakan koneksi ke server AMQP yang sama. 
`amqp://guest:guest` menunjukkan pengguna dan kata sandi yang digunakan untuk mengautentikasi ke server. Dalam hal ini, pengguna dan kata sandi keduanya adalah "guest".
`@localhost:5672` menunjukkan bahwa server AMQP berjalan di localhost (mesin yang sama dengan program) pada port 5672.
Dengan menggunakan URL yang sama, penerbit dan pelanggan dapat terhubung ke server yang sama, memungkinkan mereka berkomunikasi melalui perantara pesan dengan parameter autentikasi yang sama.

<h4> Running RabbitMQ </h4>

![img.png](publisher/img/img.png)

<h4> subscriber making connection to the message broker </h4>

![img_1.png](publisher/img/img_1.png)

<h4> publisher cargo run in subscriber console </h4>

Saat `cargo run` dijalankan di publisher, publisher mengirim 5 event ke message broker yang akan dikonsumsi dan diproses oleh subscriber sesuai kebutuhan.
![img_2.png](publisher/img/img_2.png)

<h4> spike when cargo run in publiser </h4>

Spike menandakan active connection ke RabbitMQ saat cargo run dijalankan karena publisher sedang berkomunikasi dengan RabbitMQ untuk mengirimkan 5 event ke subscriber. Grafik yang terlihat terdapat spikenya adalah grafik Message Rates. Grafik tersebut akan menggambarkan seberapa banyak/cepat message dikirim publisher dalam 1 menit terakhir. Semakin banyak, grafik (spike) nya akan semakin tinggi. Dalam kasus screenshot saya ini memang disetting dalam 1 menit terakhir, tetapi bisa juga disetting untuk range waktu lainnya
![img_3.png](publisher/img/img_3.png)

<h4> slow subscriber </h4>

Terjadi 2 queues karena adanya blocking execution saat pelambatan yang membuat penumpukan message queue atau peningkatan queues (dari berkali-kali cargo run dengan cepat).
![img_4.png](publisher/img/img_4.png)

<h4> three consoles subscriber </h4>

Spike pada message rates yang disebabkan karena saya menjalankan publisher berkali-kali. Improvement yang dapat dilakukan untuk reducing spike quicker:
- Penanganan Error: Saat ini, hasil dari `publish_event` diabaikan dengan _ =. Lebih baik menangani kemungkinan error tersebut.
- Duplikasi Kode: Metode `publish_event` dipanggil beberapa kali dengan argumen yang serupa. Hal ini dapat diubah menjadi loop atau fungsi untuk mengurangi duplikasi kode.
- Nilai yang Terkait Keras: String koneksi dan nama event dihardcode. Lebih baik memindahkan ini ke dalam file konfigurasi atau variabel lingkungan.
- Metode yang Belum Diimplementasikan: Metode `get_handler_action` saat ini belum diimplementasikan (todo!()). Metode ini sebaiknya diimplementasikan atau dihapus jika tidak diperlukan.
![img_5.png](publisher/img/img_5.png)
![img_6.png](publisher/img/img_6.png)