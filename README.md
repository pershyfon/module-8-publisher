Nama: Sabrina Aviana Dewi <br>
NPM: 2206030520
<h1> Tutorial 8 </h1>
<h2> Publisher </h2>
a. How many data your publlsher program will send to the message broker in one run? <br>
Publisher akan mengirimkan 5 data ke message broker dalam satu kali jalan. Setiap pemanggilan `_ = p.publish_event(...)` mengirimkan satu data. Karena ada 5 pemanggilan tersebut, maka akan ada 5 data yang dikirimkan.
b. The url of: “amqp://guest:guest@localhost:5672” is the same as in the subscriber program, what does it mean? <br>
URL "amqp://guest:guest@localhost:5672" yang sama pada program Publisher dan program Subscriber berarti bahwa keduanya menggunakan koneksi ke server AMQP yang sama. 
`amqp://guest:guest` menunjukkan pengguna dan kata sandi yang digunakan untuk mengautentikasi ke server. Dalam hal ini, pengguna dan kata sandi keduanya adalah "guest".
`@localhost:5672` menunjukkan bahwa server AMQP berjalan di localhost (mesin yang sama dengan program) pada port 5672.
Dengan menggunakan URL yang sama, penerbit dan pelanggan dapat terhubung ke server yang sama, memungkinkan mereka berkomunikasi melalui perantara pesan dengan parameter autentikasi yang sama.