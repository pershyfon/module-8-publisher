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

![img.png](img.png)

<h4> subscriber making connection to the message broker </h4>

![img_1.png](img_1.png)

<h4> publisher cargo run in subscriber console </h4>

Saat `cargo run` dijalankan di publisher, publisher mengirim 5 event ke message broker yang akan dikonsumsi dan diproses oleh subscriber sesuai kebutuhan.
![img_2.png](img_2.png)

<h4> spike when cargo run in publiser </h4>

Spike menandakan active connection ke RabbitMQ saat cargo run dijalankan karena publisher sedang berkomunikasi dengan RabbitMQ untuk mengirimkan 5 event ke subscriber.
![img_3.png](img_3.png)